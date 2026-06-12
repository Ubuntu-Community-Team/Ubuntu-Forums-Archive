---
title: "mod_auth_mysql killin me"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by gentooserberlin on 2010-10-14
Hello ubuntu.

normally i use gentoo but for a website they work at an ubuntu 9.04 server i install this too and all is fine but mod_auth_mysql over .htaccess is killing me hardly...

After the errors that AuthMySQLDB and equal is invalid i googled some solution but no one works really fine.

I set all in an <IfDefine AUTH_MYSQL> or <IfModule something.I.dont.know.yet.Im.not.at.home> Directive that contains a <Directory> Directive where AuthMySQLDB and all the others seted in like this

###begin of my gentoo mod.auth.mysql.conf###

<IfDefine AUTH_MYSQL>
LoadModule mysql_auth_module modules/mod_auth_mysql.so

# mod_auth_mysql can be used to limit access to documents by checking
# data in a MySQL database.

# This will enable user-based MySQL authentication of everything
# within /home/httpd.  You'll need to do the following as the MySQL
# root user beforehand:
#
#    CREATE DATABASE auth;
#    USE auth;
#    CREATE TABLE users (
#      user_name CHAR(30) NOT NULL,
#      user_passwd CHAR(20) NOT NULL,
#      PRIMARY KEY (user_name)
#    );
#    GRANT SELECT
#      ON auth.users
#      TO authuser@localhost
#      IDENTIFIED BY 'PaSsW0Rd';
#
#    INSERT INTO users VALUES ('testuser', ENCRYPT('testpass'));
#
<Directory /var/www/localhost/htdocs/websitedirectory/html/cms/>
#       # If you want tot make mod_auth_mysql work with apache-2.2, please uncomment
#       # the following line:
        AuthBasicAuthoritative Off
        AuthName "MySQL authenticated zone"
        AuthType Basic

        AuthMySQLUser value
        AuthMySQLPassword "value"
        AuthMySQLDB value
        AuthMySQLUserTable value
        AuthMySQLNameField value
        AuthMySQLPasswordField value

        AuthMySQLGroupField value
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                
        require group stb user admin userInaktiv userBeantragt userTestAccount                                                                                                                                                  
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                
</Directory>
</IfDefine>

After that no error occurs no matter how directiv i us module or define. BUT if i visit my site nothing is asking my about username and password i am the automatically the user with the less permittions.

have any a help for this problem?

thanx in advance :guitar:

---

