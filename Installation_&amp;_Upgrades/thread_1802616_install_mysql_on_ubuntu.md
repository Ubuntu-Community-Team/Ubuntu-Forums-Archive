---
title: "install mysql on ubuntu"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by linux_sky on 2011-07-12
im new to ubuntu. i wanna install mysql on linux server(ubuntu).
so i downloaded MySQL-client-5.1.58-1.glibc23.i386.rpm, MySQL-devel-5.5.14-1.linux2.6.i386.rpm, and MySQL-server-5.1.58-1.glibc23.i386.rpm. well, i follow the instruction from [http://howtotechie.com/how-to-install-mysql-on-linux]("http://howtotechie.com/how-to-install-mysql-on-linux"). when i try to run this "[COLOR="Blue"]rpm -ivh MySQL-server-5.1.58-1.glibc23.i386.rpm MySQL-client-5.1.58-1.glibc23.i386.rpm[/COLOR]", i got this error [COLOR="Red"]"rpm: RPM should not be used directly install RPM packages, use Alien instead!"[/COLOR]

i try to install mysql with the commands below:-
[COLOR="blue"]sudo apt-get install alien
sudo alien -d MySQL-client-5.1.58-1.glibc23.i386.rpm
sudo dpkg -i mysql-client_5.1.58-2_i386.deb
sudo alien -d MySQL-server-5.1.58-1.glibc23.i386.rpm
sudo dpkg -i mysql-server_5.1.58-2_i386.deb
updatedb[/COLOR]

when i [COLOR="blue"]updatedb[/COLOR], it returned [COLOR="Red"]updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'[/COLOR]

when i [COLOR="Blue"]/usr/bin/mysqladmin -u root password '123qwe'[/COLOR], it returned [COLOR="Red"]/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/COLOR]

i [COLOR="Blue"]locate mysql.sock[/COLOR] and [COLOR="blue"]locate mysqld.sock[/COLOR], nothing return... im blur now. someone please help me. how can i install mysql? :(

---

### Post by Bachstelze on 2011-07-12
You should not have done that. Remove yur installed packages and follow the Ubuntu Server Guide [https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

In general, do not use alien unless you are absolutely certain you can't do otherwise.

---

### Post by linux_sky on 2011-07-12
> **Bachstelze said:**
> You should not have done that. Remove yur installed packages and follow the Ubuntu Server Guide [https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

In general, do not use alien unless you are absolutely certain you can't do otherwise.

thanks. but may i know what packages you refer to?

---

### Post by linux_sky on 2011-07-12
> **Bachstelze said:**
> You should not have done that. Remove yur installed packages and follow the Ubuntu Server Guide [https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

In general, do not use alien unless you are absolutely certain you can't do otherwise.

is it alright if i continue to install mysql following the guide you provided without uninstalling the packages? just now i did try to install mysql again with the guide you provided without removing the package... but did not work

---

### Post by mastablasta on 2011-07-12
you installed client and server packages for mysql. they might be causing the problem.
 
aslo i think tasksel offers a gui for this to make it super easy to install... (not uninstall).

---

### Post by Bachstelze on 2011-07-12
> **linux_sky said:**
> thanks. but may i know what packages you refer to?

The packages you installed. Apparently they are called mysql-server and mysql-client.

---

### Post by linux_sky on 2011-07-12
> **Bachstelze said:**
> The packages you installed. Apparently they are called mysql-server and mysql-client.

so, what can i do? :( really need help here. thanks lot

---

### Post by ~!geek!~ on 2011-07-12
First try sudo updatedb. Let it finish working and after getting command prompt back,
Try to search mysql in synaptic manager(in ubuntu 11.04 type synaptic in dash and in ubuntu 10.10 n before search synaptic from system menu). If found any package with related to mysql installed, right click and choose completely remove option. 
Now go to terminal and type
 sudo apt-get install tasksel 
After this command runs successfully, type 
sudo tasksel 
 and using arrow keys, tab button, space bar and enter key select and install lamp server from a list of available choices. 
See if it helps!!!

---

