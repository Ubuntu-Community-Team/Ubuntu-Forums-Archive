---
title: "flash player problem"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by lentejas1987 on 2011-01-20
Dear ubuntu community,
I have been using this thread for a couple of days and just getting exposed to the vast world of ubuntu after succesfully partitoning the hard drive through a live cd.:p (a copy of linux for dummies book)So naturally after getting adjusted to the new os I started seeking for downloadable media and applications.Started with flashplayer last night and installed after watching some videos.But when I tried the same thing with vlc through the terminal command;
 
sudo apt-get vlc
 
The video streaming seased  because they wouldn't load it stays searching forever! Now youtube doesn't work.I am afraid that by tampering with the command it also affected the flash player file.This is an ethernet connection , 100 mb/s, netgear router.
Any suggestions if it the routers problem or something internal in the os?
thakx

---

### Post by presence1960 on 2011-01-20
> **lentejas1987 said:**
> Dear ubuntu community,
I have been using this thread for a couple of days and just getting exposed to the vast world of ubuntu after succesfully partitoning the hard drive through a live cd.:p (a copy of linux for dummies book)So naturally after getting adjusted to the new os I started seeking for downloadable media and applications.Started with flashplayer last night and installed after watching some videos.But when I tried the same thing with vlc through the terminal command;
 
**_sudo apt-get vlc_**
 
The video streaming seased  because they wouldn't load it stays searching forever! Now youtube doesn't work.I am afraid that by tampering with the command it also affected the flash player file.This is an ethernet connection , 100 mb/s, netgear router.
Any suggestions if it the routers problem or something internal in the os?
thakx

It should have been sudo apt-get install vlc

I have a netgear WNR1000v2 router and my wired and wireless connections play flash perfectly and have 21 Mbps download, 3.5 Mbps upload.

I would uninstall flash and then reinstall it. You may be better off installing ubuntu-restricted-extras. Run in terminal ```
sudo apt-get install ubuntu-restricted-extras
```

Here is the description from Synaptic Package Manager of what ubuntu-restricted-extras will do for you:

This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback.

Please note that this does not install libdvdcss2, and will not let you play
encrypted DVDs. For more information, see
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Bucky Ball on 2011-01-20
You might try installing ubuntu-restricted-extras from System>Administration>Synaptics Package Manager. That should install flash properly, java, and a bunch of other stuff.

---

### Post by Rubi1200 on 2011-01-21
There is also FlashAid (courtesy of forum member lovinglinux)
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by lentejas1987 on 2011-01-21
Presence 1960,
 Thanks for the option for this command it sounds almost like a windows batch file since it has so many components in it.But definetly something i will try:D.Does this option:
 
> **presence1960 said:**
> You may be better off installing ubuntu-restricted-extras. Run in terminal ```
sudo apt-get install ubuntu-restricted-extras
```
 
Here is the description from Synaptic Package Manager of what ubuntu-restricted-extras will do for you:
 

 have any other steps other than just typing in the command ,what i mean is once it has loaded does ..some sorta icon appear in your desktop to notify you've downloaded the restricted extra package??

---

### Post by presence1960 on 2011-01-21
> **lentejas1987 said:**
> Presence 1960,
 Thanks for the option for this command it sounds almost like a windows batch file since it has so many components in it.But definetly something i will try:D.Does this option:
 

 have any other steps other than just typing in the command ,what i mean is once it has loaded does ..some sorta icon appear in your desktop to notify you've downloaded the restricted extra package??

Once installed your browser will be able to view flash.

---

### Post by lentejas1987 on 2011-01-21
hello ,
 
I find the following things  to be happening I cannot get unistall the flashplayer  for good. When i go to the trash-can icon and permanetly try to delete the file  error pops up saying that it cannot get rid of flashplayer.Well 
i tried running the command:
 
sudo apt-get install ubuntu-restricted-extras
 
 it loaded for about 5 minutes .it says an application has crashed before with a red exclamation point.message=
 
Accessed problem Report of System package problem.Sorry, the package "libavcodec-unstripped-52 3:0 svn20090303 failed to install.
:-|

---

### Post by Bucky Ball on 2011-01-21
. Posted in error. ;)

---

### Post by lentejas1987 on 2011-01-23
Can the flash player crash your operating system.There is a exclamation sign in my browser .I believe the system has crashed.I might just go ahead and reinstall the ubuntu over again from the live cd.how can can i go about it?

---

### Post by lentejas1987 on 2011-01-29
Bucky,
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.

This window is hindering me from The synaptics package manager

---

