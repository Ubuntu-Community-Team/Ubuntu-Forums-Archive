---
title: "Installing SunStdio 12 in Ubuntu10.04"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by mecrazycoder on 2010-07-09
Hi All, I am a newbie to Ubuntu[in fact to Linux]. I like to install SunStdio12. So I downloaded this file SunStudio12u1-Linux-x86-rpms-ML.tar.bz2. But I dont know how to proceed further. I searched and come up with some links. But I cant able to understand. Please anyone give me the steps or link for installing. Tanx in advance.

---

### Post by Kungen7 on 2010-07-09
I guarantee you that this is to be found a million places in different forums, but sure.

You move the file to your home folder (/home/**yourusername**/) the type the following in your terminal.
```
tar -jxvf **filename**.tar.bz2
```
If the file extension (in this case ".tar.bz2") is .tar.gz the command would be
```
tar -zxvf **filename**.tar.gz
``` 
When you have done this you will se it has extracted a folder with the same name to your current directory (should be home). Type
```
cd **filename**
```
to change into this directory. Then type the following, or look for a README of INSTALL file inside the folder for other instructions.
```
./configure
make
make install
```
If you get a permission error making the install you need to run the command with root priviliges. To do this you type sudo before the command you want to execute like this
```
sudo make install
```
and then type in your root password.

**EDIT**: I see now that the name of the file you wish to extract contains "rpms". See, if it extracts a .rpm file, its i different story. Try to search around a bit to learn how to handle these.


Hope this helps,
Kungen

---

