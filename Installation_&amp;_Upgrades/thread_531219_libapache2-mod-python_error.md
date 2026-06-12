---
title: "libapache2-mod-python error"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Rience on 2007-08-21
I have installed Apache, python, mod_python, followed the instructions in the manual, wikipedia, from this forum, instructions from my mate. But nothing allowed me to use python from URL.
Then I done:

[PHP]
sudo aptitude install python
sudo aptitude install libapache2-mod-python
sudo gedit /etc/apache2/mods-available/mod_python.conf

AddType application/x-httpd-python .py
AddHandler mod_python .py
PythonHandler mod_python.publisher
PythonDebug On

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/mod_python.conf mod_python.conf
sudo /etc/init.d/apache2 restart
[/PHP]

And I had error with libapache2-mod-python, that occurs also whatever i try to install.
Please help me.

---

