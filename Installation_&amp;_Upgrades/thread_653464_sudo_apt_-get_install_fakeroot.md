---
title: "sudo: apt -get install fakeroot"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by alex81 on 2007-12-29
Hello all, 

I am fairly new to Ubuntu and linux in general. 

I just installed Ubuntu Desktop edition version 7.10. 

I am currently trying to follow some instructions to get the Sun Java SDK installed. One of the instructions 
***fakeroot make-jpkg sun-j2re1.5_1.5.0+update04_i386.bin***

When I run this I get

The program 'fakeroot' is currently not installed.  You can install it by typing:
sudo apt-get install fakeroot

So I try to then install fakeroot but running the above[B][I]

sudo apt -get install fakeroot[/I][/B]

I then get the following error: 
**sudo: apt: command not found**

I am pretty confused as what to do or try next. Please any suggestions? 

This problem seems quite out of the ordinary.

Thanks, 
Alex

---

### Post by taurus on 2007-12-29
If you want to install java, just run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-sdk sun-java6-plugin
java -version
```

---

### Post by Can+~ on 2007-12-29
For starters "apt-get" goes all together. If still doesn't work, use aptitude

Second, you don't need to do that via console, most guides just give you the commands so they don't have to say "open this windows, do that, do this other". If you need to install java, open "Add/Remove Applications" on the applications menu, and add java.

Third, as the taurus said, java is on the repostiroies (repositories are a lot of programs on a server, which you download using the command apt-get or aptitude), so you don't need to install it from a that file.

And, welcome :KS

---

### Post by alex81 on 2007-12-29
Hello all, 

Taurus, thanks for your speedy reply. 

First this seems to be a general problem I am having with **apt -get**, so it still has to be solved or I might have problems installing programs in the future. 

I did try your commands as well and got the following:: 

sudo apt-get install sun-java6-bin sun-java6-jdk sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package sun-java6-bin**
alex@pcdev2:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

It did not seem to work properly? Any ideas on the next step(s)? 

Any suggestions on how to proceed with either of the two problems would be appreciated. 

Thanks, 
Alex.

---

### Post by taurus on 2007-12-29
I bet you didn't have any repos available in /etc/apt/sources.list!

```
cat /etc/apt/sources.list
```

To enable more repos so you can install stuff, click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and place a check mark in front of all the lines except the last one, Sources code and the CDROM.  Close it and hit Refresh.  Now, in the Search window, type java and look for sun-java6-sdk, sun-java6-bin, and sun-java6-plugin.  Click those names to install them or you can close synaptic after you hit Refresh and run those commands again from a terminal.

---

