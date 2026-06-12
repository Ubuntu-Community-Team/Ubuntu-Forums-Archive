---
title: "Ubuntu 13.04 Won't Load from USB onto Lenovo Y570"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by Keithustus on 2013-08-02
SITUATION:

I took my Lenovo Ideapad Y570 (Windows 7 Professional) into a repair center to diagnose the NVidia 3D card, since unlike everything else on the system, it wasn't working.  The repair center was a bunch of idiots and somehow lost access to the OS.  They actually asked if they could reinstall Windows, which would lose all my work and personal files for the last year (why would I need to back up everything before having a video card checked?)  So now I've trying to recover access to my hard drive partitions.  Unfortunately, this laptop like many other Lenovo Ideapads, uses RapidDrive (not RapidDrive Advanced, which was discontinued) to create partitions spanning multiple drives, in this case a 64 GB SSD and a portion of a 750 GB RPM drive.  My system partition is configured like that, and I have another partition solely on the RPM drive for my documents.  Sadly, connecting the RPM drive to another system (Rosewill SATA/IDE-to-USB cable set) does not reveal any Windows-accessible partitions.  So to access my data, I'll need to follow [these directions]("http://www.jmccc.com/blog/archives/2012/04/27/recovering-data-from-a-corrupt-rapiddrive-partition/") which requires Linux, but I have never, ever seen or used Linux, so just getting the concept of the LiveUSB and setting it up took quite some time.

LINUX METHODOLOGY:

My friend, who used to work as a mobile computer tech, told me to use [livelinuxusb.com's LiLi]("http://www.linuxliveusb.com/en/download") to operate [Ubuntu 13.04 from here]("http://www.ubuntu.com/download/desktop/thank-you?release=latest&bits=32&distro=desktop&status=zeroc").  After formating a USB to FAT32 and making the LiveUSB, I turned on my laptop and booted to the LiveUSB.  Frozen screen: "[FONT=arial]SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al".  Next, I saw elsewhere on this site that apparently Fat16 works better than Fat32, so I reinstalled the Ubuntu image to the USB in that format.  This time, my laptop bypassed the Syslinux screen, briefly showed me images at the bottom of my screen of a wide rectangle and a humanoid within a circle, and has since been stuck with an all black screen save a blinking cursor in the upper left corner.  I've tried typing "help" and "enter" but no text appears and nothing happens after hitting Enter.

So....now what?[/FONT]

---

### Post by sudodus on 2013-08-02
1. I don't know how bad is the graphics card. Will it create readable output at all (with Windows)?

Do you need a graphic desktop environment, or would it be OK with a text screen? It should be easier to get a text screen working. Then you use the boot option 'test' (without quotes).

See this wiki page [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

2. If you need to run linux and can't use the internal graphic card, you can take advantage of the fact that linux is portable. So you can install it in another computer and install some kind of network service, I'd suggest sshd. See this link

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

and then you can get access via the network from another computer (login and run linux from another computer, so you need no working screen or graphics driver).

When you have a working linux system (that you boot with the boot option 'text' to avoid problems due to the nividia card), you can move the drive to the computer with problems. This system can be on a USB pendrive, USB HDD or eSATA drive. A pendrive is a little slow, but might be good enough for this repair job.
[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

---

