---
title: "Wubi Installation Trouble"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Harshesh on 2011-03-08
[B]I am trying to download ubuntu 10.10 parallel to windows through wubi installer.
Each time I try installing it, after 40% of installing it say that it has encountered an error and for more information go to the some text file (I have attached it with this thread).
The attached file is not the whole file as it is too long, I've attached the end part of it where it says ERROR
What do I do?
Thank you
[/B]

---

### Post by Dutch70 on 2011-03-09
> **Harshesh said:**
> [B]I am trying to download ubuntu 10.10 parallel to windows through wubi installer.
Each time I try installing it, after 40% of installing it say that it has encountered an error and for more information go to the some text file (I have attached it with this thread).
The attached file is not the whole file as it is too long, I've attached the end part of it where it says ERROR
What do I do?
Thank you
[/B]

Welcome to UF Harshesh,

 I don't do wubi, or know what you mean "download Ubuntu parallel to windows", but is your processor capable of 64bit? 

You may want to try a new or different download. Where did you download it from? Try here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/windows-installer[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

Also, you may find this thread helpful, until someone that knows more about wubi installs becomes available.
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

Also, If you're using vista, did you try right clicking the .exe and selecting "run as administrator"? 

Kind regards

---

### Post by bcbc on 2011-03-09
the bittorrent downloader is getting blocked:

> DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>


you need to allow pyrun.exe access to your firewall. In some cases this still fails, [so you can download the ubuntu desktop cd ISO yourself and place it in the same folder as wubi.exe before running.]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?")

---

### Post by Harshesh on 2011-03-09
Yes, I unblocked the setting which allow pyrun.exe .
It still doesn't work ... 
so now what i have to do is download the cd version of ubuntu and copy the iso file to the same folder in which wubi.exe file is ?
I've only got one file named wubi.exe , ' WUBI(1).EXE-2F55134A.pf ' in the windows folder. Is this the file with which i should put the iso file of the cd version ubuntu?

---

### Post by bcbc on 2011-03-09
get wubi.exe and the cd Desktop image from the same place (see my previous link - I recommend 10.10 because the wubi.exe for 10.04 at that address is invalid - still waiting for someone to fix it).

---

### Post by Harshesh on 2011-03-09
[PC (Intel x86) desktop CD]("http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso") image on [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)  ?? 
download this, copy it to the same folder which has wubi.exe

and run the wubi installer ?

---

### Post by bcbc on 2011-03-09
Yes, also get the wubi.exe from there to be sure you have the correct release.

---

### Post by Harshesh on 2011-03-09
[B]Its working now .... 
Thanks a LOT! :)
[/B]

---

