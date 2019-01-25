# Centos-webserver

Apache - v.2.4.6
PHP -v 5.4.16 or -v 7.2
mariadb version 5.5.60

###### repository 설정

```
# wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
# wget http://rpms.remirepo.net/enterprise/remi-release-7.rpm
# rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm
# yum install yum-utils
# yum-config-manager --enable remi-php72
```





<h6> Apache, PHP, Mariadb 설치


1. yum install -y httpd   //아파치 서버 설치

      

2. yum install -y php  //php 7.2설치

       추가적으로 자신이 필요한 모듈을 설치

       (yum install -y php php-common php-opcache php-mcrypt php-cli php-gd php-curl php-mysql -y )

      

3. yum install -y mariadb-server   //데이터베이스 설치

      

4. /etc/httpd/conf/httpd.conf  //환경변수 변경해주는 디렉토리

      

5.  httpd.conf 환경 파일 변경

       

      ```
      <IfModule mime_module>
          ``#
          ``# TypesConfig points to the file containing the list of mappings from
          ``# filename extension to MIME-type.
          ``#
          ``TypesConfig /etc/mime.types
              ``#
          ``# AddType allows you to add to or override the MIME configuration
          ``# file specified in TypesConfig for specific file types.
          ``#
              ``~
          ``.
          ``.
          ``.
          ``.
          
          ``#
          ``AddType text/html .shtml
          ``AddOutputFilter INCLUDES .shtml
      </IfModule>
      ```

      하단에 내용 추가

      ```
          ``AddType text/html .shtml
          ``AddOutputFilter INCLUDES .shtml
          
          ``AddType application/x-httpd-php .html .htm .php .inc
          ``AddType application/x-httpd-php-source .phps
      </IfModule>
      ```

      

6. 아파치를 재시작, 부팅시 자동 시작

   ```
   systemctl restart httpd
   systemctl enable httpd.service 
   ```

