FROM ubuntu:16.04

MAINTAINER "XiaoNian <xiaonian0430@163.COM>"

# 安装依赖
RUN apt update -y \
    && apt install -y locales \
    && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 \
    && apt update -y \
    && apt install -y fonts-wqy-zenhei fonts-wqy-microhei \
    && apt install -y xdg-utils wget xz-utils python chromium-browser \
    && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sh /dev/stdin

ENV LANG en_US.utf8

# 将程序拷贝进去
COPY . /www/ShareKnow/

# 将程序拷贝进去
COPY lib/time/zoneinfo.zip /usr/local/go/lib/time/

RUN chmod 0777 -R /www/ShareKnow/

WORKDIR /www/ShareKnow/

RUN ./ShareKnow install

CMD [ "./ShareKnow" ]