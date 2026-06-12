---
title: "Help trying to Understand where to Move Applications Files in Ubuntu"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by dineshmahadev3 on 2017-04-24
Hi to all 

I am New to Linux could someone please help me understand what the File System Structure of Ubuntu Linux, 
When I download a application, for example GIMP "**gimp-2.8.20.tar.bz2**" if I wanted to install this file where would 
I extract it to and move it to. I come from a Windows Environment where Files are installed into a folder called Program Files which I am sure everyone is familiar with,
 I do understand that this is not windows but could someone please help me into the right direction and also how do I create a Shortcut for this Application in my Gnome Desktop Environment.

Thanks in Advance.
I Apologize if this thread is already answered before or started in the wrong Topic.

---

### Post by howefield on 2017-04-24
First thing I would ask is do you have a reason for not using the Gimp packages that are already available from the Ubuntu repositories?

Can be installed via the Software Centre or via the command line if you are not afraid to use the terminal with..

```
sudo apt-get install gimp
```

Which version of Ubuntu are you using ?

```
cat /etc/*-release
```

---

### Post by dineshmahadev3 on 2017-04-24
Hi I understand how to use the terminal don't mind getting my hands dirty in the terminal always like learning about it.
I am using Ubuntu Gnome 16.04.02 LTS 64Bit

Maybe a better Example instead of Gimp would be Android Studio how would I go about installing that ?

---

### Post by howefield on 2017-04-24
Well, if this is a hypothetical question, I'll point you to this link :  [Install Android Studio]("https://developer.android.com/studio/install.html")

Usually it is preferable to install software from the official repositories but if you have to go and get a zip/tarball you would extract the compressed files (double click on the zip/tarball to extract) and look for the readme file which would contain installation instructions, normally by way of invoking an install script.

[This]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") might help you with your File System Structure question.

---

### Post by dineshmahadev3 on 2017-04-24
Thank You, this answers my Question. 
I appreciate your time.

---

