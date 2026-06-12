---
title: "Upgrade from Gutsy 7.10 to Hardy 8.04 failed"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by lamps06 on 2008-04-25
Howdy, folks.  Not sure what is going on with my upgrade but I am hoping someone can lend me a hand.  Here are the details:

I have been running Ubuntu Studio 7.10 for the past four months without issue.  I ran update manager last night and attempted to upgrade to 8.04.  I let my system run for several hours downloading the 1100+ packages.  After that finished it attempted to install but had some issues.  It mentioned some potential conflict with Avant Windows Navigator and then would not proceed with the upgrade.  At that point I refreshed the update manager and it listed several hundred available updates.  I chose to just install those updates rather than do the official OS upgrade.  Most of that was successful but I could see a few items failed.  At that point I restarted the computer.

Upon restart the new Ubuntu Studio splash screen loaded, the progress bar/logo completed and then I received the following message in a popup window:

"Cannot launch graphical configuration tool because display config-gtk is not installed.  Sorry, without this tool installed you must manually configure Xorg."

At this point I click "OK" and I am left with a black screen with a few lines from the boot process.  That is it.  My system is dual boot so I can still run Win XP and I can look at my Ubuntu hard drive.  Can anyone offer any suggestions here?  It sounds like I am just missing a few files I need to run the GUI.  Am I better off just trying to format my Ubuntu hard drive and do a fresh install?  Or does it sound like something simple I could fix?  Thanks!

---

### Post by Peter09 on 2008-04-25
if you are at a command prompt try 

```
sudo apt-get install displayconfig-gtk
```

not sure if it is the right package but worth a try.

PC

---

### Post by lamps06 on 2008-04-25
Hmmm, well when I attempt a normal boot I get stuck at a black screen with those several lines.  Nothing more.  Not even a command prompt.  I can type things in and they appear on the screen but they are not recognized by the computer.  It is just like typing into a text editor.  If I use Grub I can boot into safe mode and then I get a command prompt.  Should it still work if I am in safe mode?  Unfortunately, I am at work and cannot try for myself quite yet.  Thanks for the suggestion, I will try it out when I get home tonight.

---

### Post by Peter09 on 2008-04-26
should work in safemode.

PC

---

### Post by lamps06 on 2008-04-26
Well, the install worked.  I now am presented with the Ubuntu GUI, but the resolution is off.  I tried selecting my restricted drivers but it does not work (it did previously with Gutsy).  Also, Nautilus keeps opening and closing repeatedly.  I think I am just going to do a clean install.

I can still access my Ubuntu hard drive in Windows.  I know how to back up my desktop, but I spent a good deal of time configuring Grub to do a dual boot with my two hard drives.  Do you know where the file lives that I need to copy in order to preserve my dual boot?  Similarly, there was some file I had to modify to get my other two hard drives to auto mount when Ubuntu loaded.  Do you know where this file lives?  Thanks!

---

### Post by a10waveracer on 2008-04-26
> **lamps06 said:**
> Well, the install worked.  I now am presented with the Ubuntu GUI, but the resolution is off.  I tried selecting my restricted drivers but it does not work (it did previously with Gutsy).  Also, Nautilus keeps opening and closing repeatedly.  I think I am just going to do a clean install.

I can still access my Ubuntu hard drive in Windows.  I know how to back up my desktop, but I spent a good deal of time configuring Grub to do a dual boot with my two hard drives.  Do you know where the file lives that I need to copy in order to preserve my dual boot?  Similarly, there was some file I had to modify to get my other two hard drives to auto mount when Ubuntu loaded.  Do you know where this file lives?  Thanks!

You're looking for your /boot/grub/menu.lst file and the /etc/fstab file, respectively.

EDIT:  I had you grabbing the entire grub folder. You just need the menu.lst... grab device.map as well, just in case.

---

### Post by lamps06 on 2008-04-28
Ah, thank you.  I got all the files backed up that I needed to before I reinstalled.  The installation went alright, although I have several new problems now...

I am going to start a new thread with my other problems.  Thanks for everyone's help.

---

