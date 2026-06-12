---
title: "E-mail Setup Help"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by wok951 on 2008-05-25
I am trying to setup evolution. When i used windows i had this program called YPOPS. It allowed me to get yahoo mail using pop3. YPOPS was originally made for windows. But this one guy did something and made it for Ubuntu. So he gave directions on how to install it but i can't figure out how to do it. So if anyone can help me that would be great.


_DIRECTIONS:_

**_How to install YPOPs! for Ubuntu:_**
You would need my PGP public key: E22CF38B(for entire key look below!). Save this to a file (say tskariah.gpg). And then use the following command to add the key:

$ sudo apt-key add tskariah.gpg


Add the following line to the bottom of your /etc/apt/sources.list file:

deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main


followed by:

$ sudo apt-get update
$ sudo apt-get install ypops



How to (Re)configure YPOPs! for Ubuntu:

$ sudo dpkg-reconfigure -fgnome ypops

Other front-ends could be "dialog" (default), or "web". The old /etc/ypops.ini would be saved as /etc/ypops.ini.bak


How to remove YPOPs! for Ubuntu:

$ sudo apt-get remove ypops



How to start YPOPs! for Ubuntu manually:

$ sudo /etc/init.d/ypops start



How to stop YPOPs! for Ubuntu manually:

$ sudo /etc/init.d/ypops stop



How to automatically start YPOPs! for Ubuntu at bootup:
Use the configuration wizard.


Directory structure:

/etc/init.d/ypops             - init script 
/etc/ypops.ini		      - config file
/usr/bin/ypops                - executable file
/var/log/ypops/               - log directory
/var/run/ypops.pid            - pid file

WARNING: The log directory is readable by all. If the log-level is set to Advanced, YPOPs! would dump all the HTML pages there, which might contian private information. 

**_KEY:_**

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

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
z9Hqdg==
=u8Q+
-----END PGP PUBLIC KEY BLOCK-----

Again if someone can help me that would be great!!:) Thank You

---

### Post by 505 on 2008-05-25
Those directions seem pretty straight forward. Tell us where you no longer get the instructions and we might be able to help you better.

---

### Post by wok951 on 2008-05-25
The first step. when i do save it and go to terminal and type the first command in it says it can't find the file. So i don't know if i am saving it right. What i do is copy and paste the key in a notepad file and name it what it says.

---

### Post by 505 on 2008-05-26
Yes, that's correct, but when you open a terminal are you in the right directory. A terminal opens in your home directory, but if you save the file on the desktop, the command won't be able to find the file. So either first go the the desktop in the terminal (via "cd Desktop") are save the file in your home directory. To see if the file is present use the command "ls" to list all files in that directory.

---

### Post by wok951 on 2008-05-26
Okay. I got the file saved in the right directory. When i do the first command it gives me an okay. I think its added. When i do the second command it say that bash: deb: could not be found. look below for whole command!

*********@******:~$ sudo apt-key add tskariah.gpg
[sudo] password for *******:
OK
**********@*******:~$ deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main
bash: deb: command not found
*******@*******:~$

---

### Post by 505 on 2008-05-26
It doesn't say to execute the command "deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main" but to add it to the file sources.list. To do that execute the command
```

sudo gedit /etc/apt/sources.list

```
Go the the bottom of the file and paste the line "deb [http://tskariah.000webhost.com/ubuntu](http://tskariah.000webhost.com/ubuntu) ubuntu main" there. Save the file. Then continue with the command "sudo apt-get update"

---

### Post by MorrisseyJ on 2010-04-08
I am picking up and old thread here:

Having used the advice on this post i find that i have run into trouble in the next steps:

I manage to edit the /etc/apt/sources.list file, and run "$ sudo apt-get update".

After that i run into trouble. 

When i enter  "$ sudo apt-get install ypops" i get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ypopsWhen i try 

$ sudo dpkg-reconfigure -fgnome ypops

I get:

> Package `ypops' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: ypops is not installed
I sort of knew this would happen when i saw "E: Couldn't find package ypops". Can anyone tell me why the ypops package could not be found. I fear that i am doing something incredibly stupid. 

Any help will be appreciated.

---

### Post by emma48 on 2011-08-09
outdated does not work

---

