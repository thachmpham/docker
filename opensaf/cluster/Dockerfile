FROM ubuntu:16.04

RUN apt update
RUN apt install -y \
    sudo sqlite3 libxml2 psmisc \
    python2.7-minimal net-tools kmod
RUN apt install -y \
    mercurial gcc g++ libxml2-dev automake \
    m4 autoconf libtool pkg-config \
    make python-dev libsqlite3-dev binutils
RUN apt install -y \
    vim iputils-ping

RUN cd /root && hg clone http://hg.code.sf.net/p/opensaf/staging opensaf-staging

WORKDIR /root/opensaf-staging
RUN ./bootstrap.sh
RUN ./configure --enable-tipc CPPFLAGS="-DRUNASROOT"
RUN make -j `nproc`
RUN make install
RUN ldconfig
