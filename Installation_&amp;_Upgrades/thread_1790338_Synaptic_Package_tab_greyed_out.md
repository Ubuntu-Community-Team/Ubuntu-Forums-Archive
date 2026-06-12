---
title: "Synaptic Package tab greyed out"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by jrkrideau on 2011-06-24
ubuntu 11.04,Windows 7 dual boot.  Almost total linux / ubuntu novice.

I just installed ubuntu 11.04 this afternoon.  The installation went smoothly but I did not get wireless internet connection.  

Aapparent problem
In the top panel : Network device not working (firmware missing)

Some hunting indicated that one needed to remove some files and install some others using synaptic. Found synaptic, loaded it by clicking and found the file to install.

However the Package Tab was completely greyed out.  Any suggestions where I am going wrong?

BTW the 11.04 is different enough that I have not yet even found the terminal so any suggestions re it, please include a suggestion on how to find it.

Thanks, all suggestions gratefully received

John

---

### Post by tommcd on 2011-06-25
What firmware package are you trying to install?
You could try using the additional drivers function to see if it offers to install the firmware for the wireless.
Otherwise, find the terminal and run:
```
sudo apt-get update
sudo apt-get install *firmware*
```
where *firmware* is the name of the package you are trying to install.
I do not know where the terminal is on Ubuntu 11.04 since I am not using Unity. You should have the option to boot into *ubuntu-classic* when you first boot the computer. This may help you find the terminal and the additional drivers menu.

---

### Post by jrkrideau on 2011-06-25
Thanks,

Firmware is **firmware-b43-installer**

Looks like I found the terminal by just poking around in the installed packages.  

There seem to be several cures for the problem but from the most basic on up all require installing firmware-b43-installer so even if this is not a complete cure it's the first step on the road.

*You should have the option to boot into ubuntu-classic when you first boot the computer*

Thanks, I'll look for it.  As an unbuntu user for roughly 20 hours (including sleep) I haven't found everything yet.

---

### Post by jrkrideau on 2011-06-25
Follow-up to above message.

Tried to install firmware-b43-installer and to remove bccwl-kernel-source with no luck  . In both cases I received the message: E: Unable to locate package XXX

I tried this both with and without issuing the command sudo apt-get update.

Any suggestions here?

Thanks

**Terminal results**

johnkane@ubuntu:~$ sudo apt-get install firmware-b43-installer
[sudo] password for johnkane&#8221;
Reading package lists... Done
Buidling dependency tree
Reading state information... Done
E: Unable to locate package firmware-b43-installer

johnkane@ubuntu:~$ sudo apt-get remove bcmwl-kernel-source
Reading package lists... Done
Buidling dependency tree
Reading state information... Done
E: Unable to locate package

---

### Post by coffeecat on 2011-06-25
You need an active ethernet connection for apt-get to work. Can you plug the machine into your router with an ethernet cable while you do the firmware installation? If so, I suggest you open Synaptic, click on reload to refresh the package metadata, close Synaptic and then open "Additional Drivers" to see if this recommends firmware/drivers for your wireless card. You can use  Additional Drivers for the firmware/drivers installation.

If you can't connect with an ethernet cable, you can install the packages form the live CD. Have a look at this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The quickest way to open a terminal in Unity is ctrl-alt-T. And have a look at the two links in my sig. They will help you find your way around the Unity desktop.

---

### Post by jrkrideau on 2011-06-25
> **coffeecat said:**
> You need an active ethernet connection for apt-get to work. Can you plug the machine into your router with an ethernet cable while you do the firmware installation? 

If so, I suggest you open Synaptic, click on reload to refresh the package metadata, close Synaptic and then open "Additional Drivers" to see if this recommends firmware/drivers for your wireless card. You can use  Additional Drivers for the firmware/drivers installation. 

No Internet at the moment, and probably, not for a couple weeks 
 I just did a wubi installation from a wireless download to the Windows 7  to see how I'd like ubuntu.

Stupidly, I expected sudo apt-get to work both internally and over the Internet.

 I have wireless access on the Windows 7 side so it looks like I can use the download files > move to home folder and move on from there.

Come to think of it,  I have a live USB copy here so I can try that first.  

> The quickest way to open a terminal in Unity is ctrl-alt-T. And have a look at the two links in my sig. They will help you find your way around the Unity desktop.

Ah, ctrl-alt-T. Obvious :) Thanks, it sure beats going through the applicatons > etc as I was doing,  

I expect that I shall enjoy those links in the signature especially the tour.  I doubt I'll ever be a power user but after years in the mind-numming world of DOS and Windows I expect I'll enjoy the chanage

---

### Post by jrkrideau on 2011-06-26
Further advances in accessing the internet: I'm almost there.
Firefox is timing out without accessing the internet even though I have input password/access code.  However this is likely another problem. I have at least contacted the router!

Any suggestions for this problem?

Following the instructions, more–or–less, from the [https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx)  link I have managed to reach the internet , at least a half dozen wireless spots including mine have appeared!  

I used the installation CD as the source of the files I needed and the instructions and installation was very straight-forward.

In doing these installations  I found that it appears that the Ubuntu 11.04 requirements may differ a bit from the general instructions.  In particular, I could not find “/p/patch” nor “/f/fakeroot”  folders and assume that “patch” and “fakeroot”  are no-longer needed in 11.04.

Many thanks for the help.

---

