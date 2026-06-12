---
title: "USB Kubuntu 11.10 - TrueCrypt - How install?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by polarbar on 2011-10-15
Hi :D ,

I created a USB Kubuntu 11.10 and I am not able to install TrueCrypt 7.1.  [URL="http://http://www.truecrypt.org/"]http://www.truecrypt.org/
[/URL]

I tried many solutions found on the web but without success and no error messages except when I tried in the Console:


> ubuntu@ubuntu:~$ ls

Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

ubuntu@ubuntu:~$ cd Downloads

ubuntu@ubuntu:~/Downloads$ ls

truecrypt-7.1-linux-x86.tar.gz    truecrypt-7.1-setup-x86  truecrypt.sys
truecrypt-7.1-linux-x86.tar.gz.1  TrueCrypt.exe            
truecrypt-x64.sys

ubuntu@ubuntu:~/Downloads$ sudo apt-get install truecrypt-7.1-setup-x86

Reading package lists... 
Done
Building dependency tree       

Reading state information... Done

E: Unable to locate package truecrypt-7.1-setup-x86

E: Couldn't find any package by regex 'truecrypt-7.1-setup-x86'

ubuntu@ubuntu:~/Downloads$ 

Any idea?:D  Why I can not run it to install?

---

### Post by polarbar on 2011-10-15
I found myself the solution:

1. Download .gz file (tarball file) to your desktop.
2. Unpack
3. Drag and drop the file inside the unpack to your desktop
4. Double-Click the file on your desktop that you dragged and dropped
5. Select "Run in Terminal"
6. Select "Install"
7. Accept License Agreement
8. PRESTO! You have TrueCrypt installed


The key here is to put the file on the DESKTOP!!!  Not in the Downloads folder....


To run TrueCrypt:

Tab Computer
Run Command..
Type: truecrypt
Click Run TrueCrypt

That is it.8-)

---

