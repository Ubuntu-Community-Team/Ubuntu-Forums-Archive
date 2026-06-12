---
title: "Unetbootin and Startup Disk Creator not working"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by nLpPyXR on 2013-11-03
Long story short, I've tried more than a few Linux distros over the past couple of weeks and I finally decided to stay on Lubuntu; I downloaded the 13.10 .ISO file for x86 systems and performed the obligatory MD5 checksum, which was successful, as in, no errors. I was previously on Windows XP, so I always used Universal USB Installer with 100% success rate, including the last time I used it to install my current OS, Ubuntu 13.10.

While on Ubuntu 13.10, I used Unetbootin to make a live USB with Lubuntu 13.10, and it worked the very first time I rebooted, but after checking the "disc" for errors, there was one file found; no problem, I decided to boot normally, format the USB drive with the Disks utility, and try Unetbootin once more...

Six hours later and about 20 attempts after, I'm losing my patience, I've tried both the included Startup Disk Creator and Unetbootin several times; I've wiped the USB drive clean several times, both with the quick method and the slow method (overwriting with zeroes), I've used Gparted to format to FAT 32 etc. etc. etc.

All I get is either "Boot Error" from trying to boot a Unetbootin-made live USB, or "This device isn't bootable, please insert a bootable floppy" from trying to boot a SDC-made live USB.

---

### Post by sammiev on 2013-11-03
I use the same method on the weekly (daily) basics and never had any trouble with UNetbootin. Is it possible your USB stick is the problem? Do you have another that you can try?

---

### Post by coldraven on 2013-11-04
Make sure that you do not have any other USB drives attached when trying to boot. If I have an external USB hard drive plugged in my laptop fails to see the bootable USB stick or card.
I usually boot from a 1GB SD card in my laptop's card reader that I create with Unetbootin.
Edit: Conversely, make sure that you do not have a card in your card reader if trying to boot with a USB stick.

---

### Post by nLpPyXR on 2013-11-04
> **sammiev said:**
> I use the same method on the weekly (daily) basics and never had any trouble with UNetbootin. Is it possible your USB stick is the problem? Do you have another that you can try?

Anything's possible; and no, not at the moment, but I'll go out and get me a cheap new Thumb Drive to test just in case.

> **coldraven said:**
> Make sure that you do not have any other USB drives attached when trying to boot. If I have an external USB hard drive plugged in my laptop fails to see the bootable USB stick or card.
I usually boot from a 1GB SD card in my laptop's card reader that I create with Unetbootin.
Edit: Conversely, make sure that you do not have a card in your card reader if trying to boot with a USB stick.

USB mouse, USB Keyboard, and the USB Drive, that's it other than my actual, internal HDD.

---

### Post by fantab on 2013-11-04
If the USB was previously used to burn another .iso and if the USB was not formatted properly then it can cause issues with Unetbootin and Startup diskcreator. 
Use Gparted and 'create a new partition' table on the USB drive, it can found in on the gparted menubar, under 'Device'.

---

### Post by sudodus on 2013-11-04
If you still have problems with this USB pendrive after creating a new partition table, please try to wipe the first megabyte (overwriting with zeros) according to this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073"). You can also try to clone the iso file itself directly to the pendrive.

If none of these methods works, I think there is a problem either with the pendrive itself or with the cooperation of your USB system and the pendrive. I'm also awaiting your report from using a new pendrive. See also this link (with a couple of paragraphs about the pendrives themselves)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

'Prerequisites -- Notes about bootability' and 'Booting the Computer from USB'

---

### Post by nLpPyXR on 2013-11-04
> **sudodus said:**
> If you still have problems with this USB pendrive after creating a new partition table, please try to wipe the first megabyte (overwriting with zeros) according to this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073"). You can also try to clone the iso file itself directly to the pendrive.

tried that, same problems.

> **sudodus said:**
> If none of these methods works, I think there is a problem either with the pendrive itself or with the cooperation of your USB system and the pendrive. I'm also awaiting your report from using a new pendrive. See also this link (with a couple of paragraphs about the pendrives themselves)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

'Prerequisites -- Notes about bootability' and 'Booting the Computer from USB'

I used a cheap new Thumb Drive that I bought today and it didn't work either, **BUT**, I managed to figure out what was going on and I am in fact, typing from my recently installed Lubuntu 13.10 machine after properly shredding all my old data and installing.

See, in my desperation I rebooted and decided to take a look at my BIOS settings, but one thing I hadn't done before for whatever reason was booting and checking my BIOS **with** the Pendrive plugged in.

After tweaking a few minor and unrelated things, I noticed that my Pendrive was set to "auto" mode rather than "HDD" mode, I changed that, saved and exited the BIOS, rebooted, and there it was, my Lubuntu live USB with no errors working perfectly.

Hopefully this'll save someone a major headache.

---

### Post by sudodus on 2013-11-05
> **nLpPyXR said:**
> ...

See, in my desperation I rebooted and decided to take a look at my BIOS settings, but one thing I hadn't done before for whatever reason was booting and checking my BIOS **with** the Pendrive plugged in.

After tweaking a few minor and unrelated things, I noticed that my Pendrive was set to "auto" mode rather than "HDD" mode, I changed that, saved and exited the BIOS, rebooted, and there it was, my Lubuntu live USB with no errors working perfectly.

Hopefully this'll save someone a major headache.

Thanks for sharing :-)

---

### Post by Michel2k on 2014-03-08
Hi,
Just like to say I had these same problems and kept getting 'this disk is not bootable' messages. I am using a generic 2GB USB stick, 12.04 LTS and the Unetbootin from the standard repository. Tried to get Hirens boot CD on there. Tried different PC's to boot from, different BIOS settings, reformatted multiple times, all to no avail.

As it turns out solution #5 did the trick for me: Use Gparted to remove and recreate one single FAT32 formatted partition.

---

### Post by raamiz-h on 2014-10-13
Thank you so much. After hours it finally worked, however I had to 'Force HDD'.

---

