FROM docker.m.daocloud.io/openjdk:17
LABEL maintainer="ThinkGem@163.com"
ENV TZ "Asia/Shanghai"
ENV LANG C.UTF-8
VOLUME /tmp

WORKDIR /app

#RUN mkdir WEB-INF
#ADD jeesite.lic ./WEB-INF
ADD ./maven/web.war ./app.war

#ENV JAVA_OPTS "$JAVA_OPTS -Xms256m -Xmx1024m"
ENV JAVA_OPTS "$JAVA_OPTS -Dspring.profiles.active=prod"
ENV JAVA_OPTS "$JAVA_OPTS -Dnacos.home=/app"

ENTRYPOINT if [ -f "app.war" ]; then jar -xvf app.war && rm app.war; \
           fi && cd WEB-INF && sh startup.sh && cd WEB-INF && sh startup.sh

EXPOSE 8848

#docker run -p 8848:8848 thinkgem/jeesite-cloud-nacos:5.10