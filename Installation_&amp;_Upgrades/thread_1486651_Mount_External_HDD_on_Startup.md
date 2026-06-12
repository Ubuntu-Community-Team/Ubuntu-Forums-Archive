---
title: "Mount External HDD on Startup"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by painkilleryusuf on 2010-05-18
Hey guys,
Just installed my first ever linux distro in my life and sad that i did not come here before. 
Anyways i have a WD Green 1TB External HDD. 
I have Ubuntu 10.04 Lucid Lynx Installed and i want it to mount my HDD as soon as my PC starts up. Please help.

Quick Q: How much time does it take for any USB device to get recognized on ubuntu. Takes me more than 2 minutes compared to a few seconds on my windows i had before (same machine)

---

### Post by mikewhatever on 2010-05-18
What happens with the hdd exactly when you login? By default, Ubuntu automounts external media and it should be the matter of seconds, not minutes. Try running a file system check in Windows.

---

### Post by painkilleryusuf on 2010-05-18
Hi,
thanks for the reply. 
Well it shows up in Computer folder but i actually have to click it to mount it which takes 2-3 minutes. As it is with all the other USB devices that i plug-in every time. 
I only have Ubuntu. No windows no nothing.
Should i be having windows and dual boot this?

---

### Post by BoneKracker on 2010-05-18
This might help you diagnose what's going on...

Boot up without it plugged in.  Then open a terminal window, and type
```
sudo tailf /var/log/messages
```
Then plug it in.

You should see messages as the system starts handling the new device.

(Actually, I don't use Ubuntu, so I don't know how you guys have your logging set up, but I'm guessing all goes to one big "messages" file.  Somebody correct that if I'm wrong.)

---

### Post by mikewhatever on 2010-05-18
> **painkilleryusuf said:**
> Hi,
thanks for the reply. 
Well it shows up in Computer folder but i actually have to click it to mount it which takes 2-3 minutes. As it is with all the other USB devices that i plug-in every time. 
I only have Ubuntu. No windows no nothing.
Should i be having windows and dual boot this?

You don't have to have Windows to check a Windows file system. Somehow, I must have thought you dual boot, hence the suggestion. What file system does the external hdd have?

---

### Post by CharlesA on 2010-05-18
I know one of my external drives takes a few seconds (10-15 maybe, probably 5 seconds, idk) to initially spin up and mount, after that is done, it's fine.

You could try running this:

```
dmesg | less 
```

Or this:

```
 dmesg | tail 
```

After plugging in the USB drive.

---

### Post by painkilleryusuf on 2010-05-19
@charlesA i am completely new to that, so where should i put in those commands?

UPDATE:
Other problems that i come across recently.

Sometimes when i start up the theme is lost, other times sound driver would just decide not to work, and sometimes it wont boot and stop at some message (i have to force restart then)

Another problem is that Firefox just hangs up sometimes. 

These problems seem to come when my External HDD and My wireless USB internet stick are connected. If i disconnect them then PC start (with problems sometimes) but faster..

should i have a driver for my D-Link DWA 110? or does ubuntu works out its own stuff. I suppose it should because when i re-insert it, its just works..

UPDATE 2: OH DID I MENTION, printer stopped working?

---

### Post by CharlesA on 2010-05-20
You would run the dmsg command in a terminal window.

Let's just focus on one thing at a time, getting the USB drive to work.

Was the MD5SUM of the ISO verified before you burned it to cd?

---

### Post by BoneKracker on 2010-05-20
dmesg just prints the kernel ring buffer (which contains the most recent kernel log messages).  It may be useful to understand that dmesg only displays kernel log messages above a particular level of importance.  Typically, that level has been configured to "1", meaning you're not going to get much detail.

Typically, other log files will provide a greater level of detail.  Depending on how dmesg and logging are configured on your system, you may get a lot more detailed information by viewing whatever log file your kernel messages end up in (as I suggested above).

---

### Post by painkilleryusuf on 2010-05-21
> **CharlesA said:**
> You would run the dmsg command in a terminal window.

Let's just focus on one thing at a time, getting the USB drive to work.

Was the MD5SUM of the ISO verified before you burned it to cd?

Hey, thanks for the prompt reply..
I did not actually burn anything to a CD, although now that you say i would like to format and have a fresh install of ubuntu from a CD. I used Wubi, a friend suggested that to me. And as i was watching it download, i saw it installed an x64 version on my PC. but i only wanted x32. There is no way i couldve selected x64 for my old PC.

---

### Post by painkilleryusuf on 2010-05-23
So i burnt an UBUNTU 10.04 CD and installed it after cleaning the whole drive. 
The solution? NONE.. it still is the same!

Sound Driver does not work. Printer does. USB External HDD takes ages to load. 

It also asked me to update the OS and so i did. What am i doing wrong here?

---

### Post by dino99 on 2010-05-23
you have several issues, so we'll try to solve them one by one:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

dont need to follow the hard way when usefull and friendly tools exist, so install mountmanager and tweak it (system admin mountmanager) to deal with your devices and partitions as you want.

the latest problem about sound: install paprefs and gnome-alsamixer (set your prefs) and check: system pref sound to see if your driver is recognized.

you might check : system admin hardware driver to see if your video driver is activated

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by painkilleryusuf on 2010-05-25
this is what i got when i folow trouble shooter

[http://yfrog.com/b9screenshotnkp](http://yfrog.com/b9screenshotnkp)

---

