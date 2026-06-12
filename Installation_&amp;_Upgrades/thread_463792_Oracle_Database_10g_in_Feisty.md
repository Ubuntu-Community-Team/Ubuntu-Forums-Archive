---
title: "Oracle Database 10g in Feisty"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by bluenectar on 2007-06-04
Dear all,

Hi I'm a newbie here, I haven't installed Feisty yet but I want to know is that possible to install Oracle 10g on Feisty ? Is there any documentation about it or I just follow the installation guide came with Oracle 10g ?
Thanks in advance,


Best regards,

Hery

---

### Post by bluenectar on 2007-06-04
Dear all,

So there's nobody here has an experience with Oracle 10g on Feisty or nobody wants to help me out ?
I'm trying to be honest to tell that I haven't installed Feisty yet but I hope it's not the reason for the members to ignore my question.

Best regards,

Hery

---

### Post by Rmantingh on 2007-06-05
Hello and welcome.
I'm a newbie as well and am trying to find my way in the wonderful world of Ubuntu.
Regarding your Oracle installation problem. There have been other people with similar
problems that have already found some answers.
See e.g. [http://ubuntuforums.org/showthread.php?t=437691&highlight=install+oracle](http://ubuntuforums.org/showthread.php?t=437691&highlight=install+oracle)
Although the target platform there is 64 bit the principle(s) remain the same.
Have a look and see if the instructions can help you. It worked for me!
Good luck.

---

### Post by bluenectar on 2007-06-05
thanks Rmantingh,
I appreciate your answer and it helps me much. I don't know what's the moderators have been doing all the time, just to guide me in  the correct path they can't...
btw thanks again Rmantingh, hope we can do chit chat to discuss Oracle 10g under Ubuntu...

---

### Post by timdoc1 on 2007-06-06
I have an Oracle class that expects me to load 10g or something in a few days.  So this is very interesting to me.. I have been running FF for about a week and am no more knowlegable of it's workings and configurations than any 6 year old  (with an old EE degree).

---

### Post by heyhey on 2007-06-13
I've just installed Oracle 10g Release 2 Enterprise (Linux X86 32-bit version [http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip)) successfully on Ubuntu 7.04 Desktop 32-bit.  Had to do it several times because of missing packages.  Also installed Oracle SQL Developer.  So far so good.  The most important thing is to install all required packages, and to "fake" the Ubuntu so that the installer thinks it's a Redhat.

---

### Post by baharak on 2007-10-07
Hello. I'm a total newbie to the world of unix and oracle. I've installed feisty on my laptop which i s AMD Turion64. Now I'm trying to install Oracle 10g. I've followed all the steps in this article 
[http://www.dizwell.com/prod/node/52?page=0%2C3](http://www.dizwell.com/prod/node/52?page=0%2C3)

When I try to run the oracle Installer, I get this message.

./runInstaller: 63: /home/oracle/database/install/.oui: not found


I would love some help please :)

Thanks

---

### Post by Rmantingh on 2007-10-08
I'm not sure (I'm a noob as well) but have you had a look at this link?
[http://ubuntuforums.org/showthread.php?t=437691&highlight=install+oracle](http://ubuntuforums.org/showthread.php?t=437691&highlight=install+oracle)
It refers to an installation of Oracle on a 64bit machine.
Please note the last to steps in his installation.

Perhaps also check this (hidden) file .oui it is looking for (use "ls -la").
Is it really not there, or perhaps it is, but created by a different group/user?
I have following directory structure under my installation directory:

/home/oracle/database

drwxr-xr-x  6 oracle oinstall 4096 2005-07-02 18:09 .
drwxr-xr-x 20 oracle nobody   4096 2007-09-24 18:15 ..
drwxr-xr-x  9 oracle oinstall 4096 2005-07-02 18:07 doc
drwxr-xr-x  5 oracle oinstall 4096 2005-07-02 18:07 install
drwxr-xr-x  2 oracle oinstall 4096 2005-07-02 18:07 response
-rwxr-xr-x  1 oracle oinstall 1327 2005-07-02 18:07 runInstaller
drwxr-xr-x  9 oracle oinstall 4096 2005-07-02 18:09 stage
-rwxr-xr-x  1 oracle oinstall 5213 2005-07-02 18:09 welcome.html

/home/oracle/database/install

drwxr-xr-x 5 oracle oinstall   4096 2005-07-02 18:07 .
drwxr-xr-x 6 oracle oinstall   4096 2005-07-02 18:09 ..
-rwxr-xr-x 1 oracle oinstall     28 2005-07-02 18:07 addLangs.sh
-rwxr-xr-x 1 oracle oinstall     76 2005-07-02 18:07 addNode.sh
drwxr-xr-x 2 oracle oinstall   4096 2005-07-02 18:07 images
-rwxr-xr-x 1 oracle oinstall  35634 2005-07-02 18:07 lsnodes
-rwxr-xr-x 1 oracle oinstall   2268 2005-07-02 18:07 oneclick.properties
-rwxr-xr-x 1 oracle oinstall   2387 2005-07-02 18:07 oraparam.ini
-rwxr-xr-x 1 oracle oinstall   6428 2005-07-02 18:07 oraparamsilent.ini
-rwxr-xr-x 1 oracle oinstall 163185 2005-07-02 18:07 .oui
drwxr-xr-x 2 oracle oinstall   4096 2005-07-02 18:07 resource
drwxr-xr-x 2 oracle oinstall   4096 2005-07-02 18:07 response
-rwxr-xr-x 1 oracle oinstall 102612 2005-07-02 18:07 unzip

Make sure all installation files are owned by user oracle and have sufficient access:

cd /home/oracle/database
chown -R oracle *
chgrp -R oinstall *
chmod -R 755 *

What happens if you create the directory yourself as user oracle ("mkdir .oui")?

I'm running out of ideas here. Anybody else?

---

### Post by Neo_0815 on 2008-02-05
Your are missing the ia32-libs, because of that oui could not be found, as its a static 32bit elf binary.
oracle for 64 bit is not pure 64bit, but a mix of 32/64bit stuff (annoying i know).

I got 11g installed fine with gutsy, 10g however still fails with compile problem which i am still investigating, how to solve them.

---

