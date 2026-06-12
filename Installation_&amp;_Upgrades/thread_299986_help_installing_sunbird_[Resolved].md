---
title: "help installing sunbird [Resolved]"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by darthseth on 2006-11-15
I am using the instructions here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
and I had downloaded sunbird from the mozilla website for linux_x86, but these are the errors I am getting.  It looks like to me that I need to find another way to find another way to install it.  Any suggestions at all?

darthseth@darthseth-laptop:~/Desktop/sunbird$ sudo ./configure
Password:
sudo: ./configure: command not found
darthseth@darthseth-laptop:~/Desktop/sunbird$ sudo make
make: *** No targets specified and no makefile found.  Stop.
darthseth@darthseth-laptop:~/Desktop/sunbird$ sudo make install
make: *** No rule to make target `install'.  Stop.
darthseth@darthseth-laptop:~/Desktop/sunbird$

I would also really like to know how to run thunderbird which I already installed using apt-get, but when I search my computer I get these files, but of course nothing looks like an ".exe".  Any suggestions?  The big question is "WHAT AM I LOOKING FOR?" any clues, pointing fingers or even super-critical demeaning remarks are welcome so long as they help me open and run a program that I installed all by myself in Linux.  

Thanks!

---

### Post by aysiu on 2006-11-15
It's not a .tar.gz you compile from source. It's a precompiled binary. Paste these commands into the terminal: ```
cd ~/Desktop
sudo mv sunbird /opt
sudo ln -s /opt/sunbird/sunbird /usr/bin/sunbird
``` Now the command *sunbird* should launch the application.

---

### Post by darthseth on 2006-11-15
Thanks Aysiu! I will try this out when I am home from work in about two hours! Can't wait! :)

---

### Post by darthseth on 2006-11-16
It worked! you're the bomb!

HEy is there a place I can go to learn more about linux commands? Maybe i could have known this by myself?

---

### Post by aysiu on 2006-11-16
> **darthseth said:**
> It worked! you're the bomb!

HEy is there a place I can go to learn more about linux commands? Maybe i could have known this by myself?
Great to hear that it worked.

Most of the commands I know I learned from this:
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

