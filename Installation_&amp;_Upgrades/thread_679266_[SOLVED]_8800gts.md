---
title: "[SOLVED] 8800gts"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by mohbana on 2008-01-26
hi,

i have the 8800gts 512mb by evga, i am at a point when i going to give up after successfully installing ubuntu via the alternate cd i arrive at this situation as described by this person.

> Hello,

I tried to install Ubuntu 7.10 on my new custom rig using the LiveCD first. After the CD graphically let me know that I was going to run in low graphics mode and I hit "continue," the install just hung up on "starting local system something something" and hung there for over 30 minutes while I rocked out on DDR.

I then tried the alternate disk. It installed, and I booted the first time. Success (minus graphics). I could install the graphics driver later,

[http://ubuntuforums.org/showthread.php?t=665018](http://ubuntuforums.org/showthread.php?t=665018)


apparently there are issue with the 8800gts g92? are these solved if so how? cause i currently running the vesa driver on 800x600 which is really poor i cant stand it.  My monitor is not recognized either.

thanks for any help given.

---

### Post by PmDematagoda on 2008-01-26
You can follow these steps to install the Nvidia driver:-

1) Install the prerequisites required for the installation of the driver by executing:-
```
sudo apt-get install build-essential
```

2) Download the Nvidia driver using:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```

3) Kill the GUI using:-
```
sudo /etc/init.d/gdm stop
```

4) Run the installer of the driver using:-
```
sudo sh NVIDIA-Linux-x86-169.09-pkg1.run
```

5) After installation, reconfigure the X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```

6) After reconfiguration, restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

Your VGA card should now be working properly.

---

### Post by mohbana on 2008-01-27
your the man, i can't believed that work.  I think this threads needs to get sticked alot of people are getting the same error.

---

### Post by Scavinger on 2008-02-26
The first portion of this worked for me as well.  My thanks.  But I have an AMD 64-bit processor, so the wget command will not work as posted.

I'm enough of a newb to not be sure exactly which file I should pull down for my 64-bit setup.  Can someone post the file needed for a 64-bit AMD + 8800GTS combo? 

I also second the motion to sticky this thread.  It appears to be the most concise.

---

### Post by PmDematagoda on 2008-02-26
Here is the wget command to obtain the 64 bit Nvidia driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/169.09/NVIDIA-Linux-x86_64-169.09-pkg2.run
```

---

### Post by Scavinger on 2008-02-26
Thanks!

---

### Post by Scavinger on 2008-02-29
Followup : 
Step 1 caused me problems because the address "us.archive.ubuntu.com" was unreachable.  If you go into /etc/apt/sources.list and delete the "us." from every address that isn't commented out, then the apt-get build-essential command starts working again.  I used nano to do this.  I'm afraid that I never learned vi.

In step 4, there are some oddities with the driver install that I did not document for posting here, but that were relatively easy to navigate.  It had to build a kernel interface for me, apparently.

I did not have to do step 5.

Gnome started up just fine after that!  It looks smooth from here.  Thanks again!

---

### Post by Scavinger on 2008-02-29
I was wrong - I needed step 5.

---

