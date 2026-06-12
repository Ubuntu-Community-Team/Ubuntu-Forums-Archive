---
title: "Please help/ Problem w/ Install at login screen"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by mmic703 on 2010-03-23
Little background info:  I have a computer where the hdd crashed. Bought a new hdd tonight and installed it.  As the computer had no operating system at this point I put in a copy of the live cd and begin to install Ubuntu 9.10(32 bit)...everything went smooth with the install (at least I think).  My problem is that when I get to the login screen, I click on my user name to type in my password but as soon as I click on either my user name or guest it basically freezes...Mouse still moves but can't do anything with login or the options on the bottom right of the screen...

Right when it freezes the pixels under the login box mess up, looks like some type of graphics problem?? I'm not sure, but I can't be the first person with this problem

Also after it "freezes" I can't utilize the ctl+alt+f1 command either


any one got any suggestions??? I've been looking around and can't quite find any info

---

### Post by dstew on 2010-03-23
Do you get the grub menu? If so, try a Recovery Mode boot. If that works (gets you a command line with root privleges), your underlying system is probably intact, and you are dealing with a graphics problem.

If you have concluded that the issue is a graphics problem, you will probably need to reconfigure the X server that creates the graphical user interface. You have to do this "by hand" in most cases. Start with the command```
X -configure
```Then try```
startx
```and see what you get.

[Here is a thread]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145") with a lot of information on re-configuring X in 9.10.

---

### Post by Sef on 2010-03-23
How do things work with running the live cd?

---

### Post by Bigredjeep on 2010-03-25
> **dstew said:**
> Do you get the grub menu? If so, try a Recovery Mode boot. If that works (gets you a command line with root privleges), your underlying system is probably intact, and you are dealing with a graphics problem.

If you have concluded that the issue is a graphics problem, you will probably need to reconfigure the X server that creates the graphical user interface. You have to do this "by hand" in most cases. Start with the command```
X -configure
```Then try```
startx
```and see what you get.

[Here is a thread]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145") with a lot of information on re-configuring X in 9.10.

Hello everyone. I am having the exact same issue as the OP in this thread. I have a AMD 3200 64 bit cpu with 4gig memory and a EVGA NVIDIA 7800 GT video card. I tried whats quoted above and I am able to boot into x windows but as soon as I scroll or open a windows i get blurred lines and it hard locks again. A friend of mine told me to install the  nvidia PPA drivers and i ran through the tutorial on launchpad. Either I didn't do it right or it had no effect on this at all. Ideas Suggestions?

Thanks for all the help.

Brian

---

### Post by dstew on 2010-03-26
BigRedJeep: You don't have *exactly* the same problem because the original poster has a 32-bit system. But anyway, what method are you using to install the driver? Give us a link. [This blog]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") has a method that seems straightforward.

---

### Post by Bigredjeep on 2010-03-26
> **dstew said:**
> BigRedJeep: You don't have *exactly* the same problem because the original poster has a 32-bit system. But anyway, what method are you using to install the driver? Give us a link. [This blog]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") has a method that seems straightforward.

Thanks for the help. I didn't mean to hijack this user's thread for this issue. Here is the link that I tried to follow: [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html) . When i get home tonight I will try what you posted and let you know what I get.
Thanks,
Brian

---

### Post by Bigredjeep on 2010-03-26
I tried the link that you gave me and i get an error on the last step.
E: Couldn't find package nvidia-settings-190

I have been looking around to see if maybe that name or location might have changed. What are your ideas or thoughts on it ?

---

### Post by Bigredjeep on 2010-03-26
I decided to try the IRC ubuntu channel to see what i could get from it and someone called Gogeta was able to help me out. Here is what we did in addition to the other items in this post to get it working.
sudo apt-get install nvidia-settings 
wget -O NVIDIA-Linux-x86-pkg1.run [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
sudo sh NVIDIA-Linux-x86-pkg1.run 
i was then able to boot the system normally and i have been able to run the updates and even make this post while booted into Ubuntu.
Thanks so much for the help.

---

