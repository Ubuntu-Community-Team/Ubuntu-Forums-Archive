---
title: "Need easy instructions to install from a USB thumb drive"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by michael-piziak on 2014-12-01
I'm heavily considering installing a 64 bit version of Ubuntu on my Intel Core 2 duo that has Ubuntu 12.04 LTS 32 bit running now.

I've always installed Ubuntu on systems from an install CD.  I would like some easy instructions on how to download and install a 64 bit version from a USB thumb drive.

Once, I installed 14.x LTS (using the software center), but I had problems with my videos on youtube.  So I went back to 12.04 LTS.  So I'm torn between trying the 64 bit version of 14.x LTS or getting the 64 bit 12.04 LTS.

It's my understanding that one has to do a complete re-install to get to 64 bit - one simply can't update to it via the software updater.

So, where are some very easy instructions, either here or on the web, to download to a thumb drive and then do a complete re-install from it.

---

### Post by slickymaster on 2014-12-01
[Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by oldfred on 2014-12-01
How large is hard drive?
You can add another 20 or 25GB if available for another / (root) and have both your old install and a new install. Then it is easy to go back. 

Best to have good backups. And export a list of installed applications to make it easy to reinstall the new 64 bit versions.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

This is what I backup, pretty current expect I now include the info from the links below also.

 Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by michael-piziak on 2014-12-01
> **slickymaster said:**
> [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

So I can use the "Startup Disk Creator" already on my computer (I hope it's on 12.04 lts, I'm not at home).

I can use this instead of going to "pendrivelinux.com" website, as I see is used on 2 youtube videos I've viewed moments ago.  Is this Pendrive for someone who has Windows only.

---

### Post by Dennis N on 2014-12-01
> So I can use the "Startup Disk Creator" already on my computer (I hope it's on 12.04 lts, I'm not at home)

You can use that, or **unetbootin** which is another choice to make a usb installer from a downloaded .iso file. It's in the Ubuntu repositories.

---

### Post by sudodus on 2014-12-02
I think you will succeed with the Startup Disk Creator, if you want to install 14.04.1 LTS (but not 14.10 because of a bug). I think it is a good idea to install and run the LTS version, which has support for 5 years while 14.10 is supported only for 9 months. Unetbootin will work for both versions (as well as mkusb and other alternatives found in [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick"))

---

### Post by gordintoronto on 2014-12-02
Yes, Pendrivelinux is for Windows.

You might want to confirm that the BIOS of your computer can be set to boot from USB before you go very far with this project.

---

### Post by michael-piziak on 2014-12-02
> **gordintoronto said:**
> Yes, Pendrivelinux is for Windows.

You might want to confirm that the BIOS of your computer can be set to boot from USB before you go very far with this project.

I hit f9 (boot up menu for my system on startup), and my system does support booting from a usb device - I assume this means it can boot from a simple thumb stick (thumb drive).

---

### Post by michael-piziak on 2014-12-02
> **sudodus said:**
> I think you will succeed with the Startup Disk Creator, if you want to install 14.04.1 LTS (but not 14.10 because of a bug). I think it is a good idea to install and run the LTS version, which has support for 5 years while 14.10 is supported only for 9 months. Unetbootin will work for both versions (as well as mkusb and other alternatives found in [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick"))

I most likely will try 12.04 lts 64 bit.  I tried 14.04 lts 32 bit and had problems with my video (you tube) already, and I reverted back to 12.04 lts with a clean re-install.  But who knows, perhaps the 64 bit of 14.04 lts would work just fine.

---

### Post by sudodus on 2014-12-03
If 12.04 LTS works well for you, there is no reason to try hard with any other version. The standard Ubuntu flavour is supported until April 2017 :-)

---

### Post by michael-piziak on 2014-12-03
> **sudodus said:**
> If 12.04 LTS works well for you, there is no reason to try hard with any other version. The standard Ubuntu flavour is supported until April 2017 :-)

It works well other than I was trying to play the game 0 A.D. and it was slow and the mouse cursor was choppy.  I looked at System Monitor and only one of my 2 processor chips was working hard.

---

### Post by sudodus on 2014-12-03
I think it depends on the software (the game program, and/or wine or similar if it is used) if more than one processor can be used. Ubuntu can run programs that use several CPUs/threads. I do that with ffmpeg (in 12.04.5), so I know that it works.

But if you have choppy graphics you should try with a lighter desktop environment. Try either of the following flavours of Ubuntu

- Xubuntu with medium desktop environment
- Lubuntu with ultra desktop environment

Try them live before considering installing.

-o-

And/or if you have an nvidia or amd/ati/radeon graphics chip/card - try a proprietary graphics driver. For example, you can use vdpau with nvidia, which can use the graphics chip (GPU to do some of the work instead of the CPU. Also in this case it depends on the software if it can be used.

---

