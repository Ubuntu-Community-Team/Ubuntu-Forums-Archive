---
title: "LAMP Server and Python"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by jagiboy on 2006-12-06
I wanted to get a LAMP server running and be able to use Python on Apache. Searched and found information scattered. So I am compiling the list of things I did to get the server up and running. 

Installed Ubuntu Server 6.06 and Choose the Lamp Server Install. This installs the following.
  ->Apache2
  ->Python2.4
  ->PHP5
  ->mysql5.0

  Default web folder for Apache2 /var/www
  default cgi-bin folder /usr/lib/cgi-bin

  php works out of the box without any issues.

Python cgi works out of the box. Just drop the .py file in the cgi-bin folder and you are set. (http://localhost/cgi-bin/test.py)
To get mod_python working install the mod_python package for apache2
 -> sudo apt-get install libapache2-mod-python2.4

Once the package is installed you will need to edit the apache2.conf file located in /etc/apache2 and add the following lines

To use the mod_python publisher on file in folder /var/www/pub
  <Directory /var/www/pub>
     AddHandler mod_python .py
     PythonHandler mod_python.publisher
     PythonDebug On
  </Directory>

To use the mod_python psp handler on file in folder /var/www/psp
  <Directory /var/www/psp>
     AddHandler mod_python .psp
     PythonHandler mod_python.psp
     PythonDebug On
  </Directory>

Restart the apache2 server (sudo /etc/init.d/apache2 restart)

now you should be able to run py (say test.py) files from the pup folder using
 http://localhost/pup/test.py

Similarly for psp
 http://localhost/psp/test.psp

---

