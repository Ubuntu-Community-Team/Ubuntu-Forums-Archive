---
title: "Install problem on ubuntu 15"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by Avijit_Palit on 2016-03-15
Hi all i am new in ubuntu.
When i am trying to install ubuntu 15, after copying some files (about 20%) is says ''Errno 5 : Input/Output error'
Hlp plz...

---

### Post by Bucky Ball on 2016-03-15
Welcome. More details, please. Machine make and model, amount of RAM, CPU, dual-boot with Windows and which version if so. Did you leave free space to install Ubuntu to? What did you choose: Use whole disk, alongside Windows, or 'Something Else' option? The more you can help us with info about your issue the better we can help you.

Also, try researching the problem (a good idea prior to posting) and see what you find. [Look here]("https://duckduckgo.com/?q=Errno+5+%3A+Input%2FOutput+error").

---

### Post by howefield on 2016-03-15
Check the veracity of the downloaded iso, assuming it is 15.10 go to [http://releases.ubuntu.com/15.10/](http://releases.ubuntu.com/15.10/) and download the MD5SUM file to your download folder.

Open a terminal and navigate to the folder containing the downloaded Ubuntu iso and type the command..

```
md5sum -c ~/Downloads/MD5SUMS
```

You should get something like..

```
hugh@wily-laptop:/Data/Xenial$ md5sum -c ~/Downloads/MD5SUMS
xenial-desktop-amd64.iso: OK
md5sum: xenial-desktop-i386.iso: No such file or directory
xenial-desktop-i386.iso: FAILED open or read
md5sum: WARNING: 1 listed file could not be read
```

---

### Post by kc1di on 2016-03-15
Hello Avijit_Palit and welcome to Ubuntu, 

This usually happens when the download or burned ISO is corrupted in some way. 
Please try downloading and burning the ISO again.  
[This page ]("https://help.ubuntu.com/lts/installation-guide/i386/ch05s04.html")may be of help also. 

good Luck :)

---

