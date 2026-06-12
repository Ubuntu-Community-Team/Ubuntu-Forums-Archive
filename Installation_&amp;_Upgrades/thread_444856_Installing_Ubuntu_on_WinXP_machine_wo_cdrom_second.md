---
title: "Installing Ubuntu on WinXP machine w/o cdrom: second attempt"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Dlrnc3 on 2007-05-15
I have been trying to find out how to install Ubuntu on my laptop for school. Currently it is running Windows Tablet PC Edition, but I am tired of windows and want a change. The problem is that I don't have a CD-ROM drive. Someone suggested doing a PXE install, but I havn't found any clear guides on it so I don't understand how it works.

I tried installing it with both a usb and a pcmcia drive but i could not boot the cd. Hopefully there is something that I am missing or something.

The computer is a Acer TravelMate C110. 


Thanks.

---

### Post by Jonne on 2007-05-15
[https://wiki.ubuntu.com/install.exe/](https://wiki.ubuntu.com/install.exe/)

It won't be a 'native' install with its own HD and such, but it's the easiest solution.

---

### Post by tgm4883 on 2007-05-15
First I would check on this, because last I heard linux on tablet pc's doesn't work very well (if you want to use the tablet portion of the pc that is)

Second, make sure your set to boot from usb.

Then do this, it shows how to put ubuntu on a flash drive.  Then you should be able to install it from there

Quoting reacocard
> there are some threads on these forums about getting ubuntu onto a flash drive. idk if it works, but it's worth looking into.

EDIT: [http://ubuntuforums.org/showthread.php?t=71567&highlight=ubuntu+flash+drive](http://ubuntuforums.org/showthread.php?t=71567&highlight=ubuntu+flash+drive)
take a look at [post #158]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158")
it puts the livecd of ubuntu onto the drive, using it's persistence feature to let it save changes. you could also use the ubuntu customization kit to pre-customize the livecd to your needs.

---

### Post by Dlrnc3 on 2007-05-15
I am going to try Jonne's idea first and hopefully that will work alright. As for the tablet functions, I didn't choose to get a tablet pc, its through my highschool, I never really cared for the feature and never use it, so it won't be missed.

Thanks for the help.

---

### Post by mikewhatever on 2007-05-15
Try looking at [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots.html)
Perhaps, also, search for some fit backs, I do not really know if it works.

---

### Post by tgm4883 on 2007-05-15
Also, if you don't mind spending $30-$40, you could get it here

[http://store.madtux.org/index.php?cPath=89&osCsid=122ffe589594264557b7be5410bad59e](http://store.madtux.org/index.php?cPath=89&osCsid=122ffe589594264557b7be5410bad59e)

---

### Post by Dlrnc3 on 2007-05-16
I tried the .exe installer but it failed while making virtual disks. Right now I am looking into getting a firewire external drive to try my dapper disk in, hopefully it will work. Windows will not boot anymore but I really don't care as long as I can get something working on it in the next couple days. Thanks for all the help so far though. That preloaded usb drive is very tempting...

After looking at that Wubi link, I think i had a bad version of it or something. It didn't ask my for anything but log in details for my new account, downloaded the OS, and then reboot and failed.

---

### Post by Jonne on 2007-05-16
Ow, that kinda sucks. your boot.ini is probably screwed up, which you can easily edit with any OS you manage to boot. Ofcourse, not a lot of stuff can boot without a cd-rom... Who designs a computer without cd-rom-drives anyway? (There doesn't happen to be a floppy drive available?)

---

### Post by pk4ip on 2007-05-17
I have the exact same tablet and installed Ubuntu Feisty last week.  I purchased an IDE to USB adapter for 15 bucks and connected it to a regular IDE CDROM drive.  After plugging in the CD drive via USB, I put the Ubuntu CD in, made sure BIOS was set to boot from CD and started the machine up.  Sure enough it booted right into the Ubuntu install.  You can probably use any external USB CD drive.

Overall, the tablet works great.  The tablet pen and all major components work without any additional driver installation.  My big gripe right now is that the wireless will not resume after the tablet goes to suspend/hibernate.  Only way to get it back is to reboot.  Still trying to figure that out.  Good luck!

---

### Post by Dlrnc3 on 2007-05-19
I got it too work finally with a firewire external. It works great except I don't yet have tablet features and I have that same wireless problem. I put dapper on it though. Thanks for all your help. Hopefully, I'll start a revolution at my H.S. now since we all have them. The tech guy was mad at me though, lol. I already know of four people that now want to switch their tablets over too.

It's a great machine for linux. Nice, small, and portable. Will be great once I have the pen working on it.

---

### Post by mircione on 2007-06-07
> **pk4ip said:**
>  I purchased an IDE to USB adapter for 15 bucks and connected it to a regular IDE CDROM drive.  After plugging in the CD drive via USB, I put the Ubuntu CD in, made sure BIOS was set to boot from CD and started the machine up.  Sure enough it booted right into the Ubuntu install.  You can probably use any external USB CD drive.

Overall, the tablet works great.  The tablet pen and all major components work without any additional driver installation.  My big gripe right now is that the wireless will not resume after the tablet goes to suspend/hibernate.  Only way to get it back is to reboot.  Still trying to figure that out.  Good luck!

I have a Toshiba portege 3500 tablet PC. I can't boot from USB or CDrROM. I have a PCMCIA to USB adapter and I tried to boot from my external CDROM via PCMCIA but my computer can't see the CD.
The last chance to have Ubuntu in my machine is to boot from network.
Somebody know how this work...or another idea.
I tried this too: I put my hard drive in my desktop and I installed Ubuntu...but when I start from laptop the Ubuntu start to download but after couple seconds stop and I have a black screen.

---

