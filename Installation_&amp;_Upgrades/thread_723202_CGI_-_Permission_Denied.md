---
title: "CGI - Permission Denied"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Buduntu on 2008-03-13
Hi,

Can any one tell me how to run cgi scripts via internal intranet????

My apache error log state:


[Thu Mar 13 13:34:56 2008] [error] [client 10.0.0.14] script not found or unable to stat: /usr/local/apache2/cgi-bin/testcgi, referer: [http://10.0.0.14/form2.html](http://10.0.0.14/form2.html)
[Thu Mar 13 13:36:38 2008] [error] [client 10.0.0.14] script not found or unable to stat: /usr/local/apache2/cgi-bin/testcgi, referer: [http://10.0.0.14/form2.html](http://10.0.0.14/form2.html)
[Thu Mar 13 13:42:42 2008] [error] [client 10.0.0.14] script not found or unable to stat: /usr/local/apache2/cgi-bin/testcgi, referer: [http://10.0.0.14/form2.html](http://10.0.0.14/form2.html)
[Thu Mar 13 13:43:34 2008] [error] [client 10.0.0.14] (13)Permission denied: exec of '/usr/local/apache2/cgi-bin/testcgi.' failed, referer: [http://10.0.0.14/form2.html](http://10.0.0.14/form2.html)
[Thu Mar 13 13:43:34 2008] [error] [client 10.0.0.14] Premature end of script headers: testcgi., referer: [http://10.0.0.14/form2.html](http://10.0.0.14/form2.html)

---

### Post by Buduntu on 2008-03-13
This was taken from Access log:

10.0.0.14 - - [13/Mar/2008:13:43:31 +0000] "GET /form2.html HTTP/1.1" 200 631
10.0.0.14 - - [13/Mar/2008:13:43:34 +0000] "POST /cgi-bin/testcgi. HTTP/1.1" 500 544
10.0.0.14 - - [13/Mar/2008:13:58:24 +0000] "GET / HTTP/1.1" 304 -
10.0.0.14 - - [13/Mar/2008:13:58:24 +0000] "GET /apache_pb22.png HTTP/1.1" 304 -
10.0.0.14 - - [13/Mar/2008:13:58:26 +0000] "GET /form2.html HTTP/1.1" 304 -
10.0.0.14 - - [13/Mar/2008:13:58:28 +0000] "POST /cgi-bin/testcgi. HTTP/1.1" 500 544

---

