---
title: "can not install mysql, php5 and apache2 server on ubuntu 10.04"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by pratyushdeka255 on 2010-08-04
**can not install mysql, php5 and apache2 server on ubuntu  10.04** 			
 			 			 		   		 		 		currently I am  using Ubuntu 10.04.I want to install mysql, php5 and apache2 server in  my machine.  I have tried this-- 

aptitude install mysql-server mysql-client  

But the outcome is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched  "mysql-server"
Couldn't find any package whose name or description matched  "mysql-client"
Couldn't find any package whose name or description matched  "mysql-server"
Couldn't find any package whose name or description matched  "mysql-client"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

and also tried to install php5 and apache2 in the same way. But could  not install.

Also trid inthis way

apt-get install apache2

But the outcome is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2


How to proceed??

---

### Post by rollin on 2010-08-04
This should help: [http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/installing-wordpress-3-0-on-ubuntu-10-04-lucid-lynx.html)

If you really can not get any packages, check your sources under System>Administration>Software Sources. Also run:

```
sudo apt-get update
```

Prior to apt-get install of the files.

---

### Post by imnotjack on 2010-08-04
Hello
I'm using Joomla! to create and edit my Boy Scout Troop's Website. I'n order to install it I need the same LAMP (Linux Apache Mysql PHP) configuration. So I finally found a single command that works for me. IDK if you've tried it, I'm just throwing it out. In a terminal type " sudo apt-get install lamp-server^ " This installed everything for me so simply and easily... I was utterly SHOCKED. First time ever that I was able to install flawlessly on the first try. Word of warning however.... DO NOT UNINSTALL IT USING THE REVERSE COMMAND. I tried it and was forced to reinstall my OS. 

Have you successfully installed apache in the past using the apt-get install apache2 command? I thought there was more to that method of installing apache.

Anyway let us know if that worked. :)

---

### Post by imnotjack on 2010-08-04
oh... I guess that wouldn't help if you don't have your repositories in order. Have you messed with the software sources option under System-Administration-Software Sources
You should be able to enable the main repositories.

---

