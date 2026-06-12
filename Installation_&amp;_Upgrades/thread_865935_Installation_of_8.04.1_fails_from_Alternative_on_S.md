---
title: "Installation of 8.04.1 fails from Alternative on Select and install"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by stenjo on 2008-07-21
I have spent more than 3 days now (off and on) trying to install Ubuntu on my Fujitsu Lifebook E8020D. I have already got rid of Win XP on this one and have managed to install Grub and LILO on the hard drive. It now boots from disk but when running the installer from CD it always fails on Select and Install. I end up without the desktop starting.

It appears I'm able to run sudo apt-get install and I'm hoping that this will enable me to install the missing parts from the net rather than the CD.

I have also tried the Live CD but this one also gives me difficulties.

Anyone able to provide me with some command lines to complete and/or correct the installation?

---

### Post by Partyboi2 on 2008-07-21
hi, you could try
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by stenjo on 2008-07-21
Thanks for the tip. when running the sudo apt-get update i get the following response:
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/main Translation-nb
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701) hardy/restricted Translation-nb
Reading package list ... Done!

Not mutch more happens I'm afraid. How do I check if the desktop is available and if so, how do I start it?

No difference trying the sudo apt-get upgrade either...

/Sten

---

### Post by stenjo on 2008-07-21
bump?

---

### Post by Partyboi2 on 2008-07-21
try disabling the cdrom  in your sources.list
```
sudo nano /etc/apt/sources.list
```put a [COLOR=Red]#[/COLOR] infront of the line(s) that look something like this:

```
[COLOR=Red]#[/COLOR] deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted


```Then save and exit
ctrl+o
enter
Ctrl+x
then 
```
sudo apt-get update
sudo apt-get upgrade
```Make sure you are hardwire to the internet.
Also what is the output to this command
```
 dpkg -l ubuntu-desktop gdm
```

---

### Post by stenjo on 2008-07-22
Thanks again for the input.
I managed to get things working using both my Live CD and the Alternative.

This is what happened:
Tried to install Ubuntu 8.04.1 on my Fujitsu E8020D Celcius using the Live CD. This caused the bootup message: Operating system not found. Regardless of what I tried to do, this was the result of my efforts.
Then I made myself an Alternate CD and tried to install from there, but this also failed during installation and all I managed to do was getting the user promt for logging in. No desktop.

At least I had managed to get the loader in so I tried the Live CD again with the GRUP and LILO loaded from the Alternate installation. This time it went well and my laptop now boots as expected, althoug the boot process takes some time.

Thanks again for all your help.
Actually I installed ubuntu on an old laptop for my 13 years old daughter - She is really enjoying this now - discovering the wonders of bittorrents :-)

:guitar:


/Sten

---

