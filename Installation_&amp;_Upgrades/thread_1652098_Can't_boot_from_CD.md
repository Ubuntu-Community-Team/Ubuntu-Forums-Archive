---
title: "Can't boot from CD"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Bahokan on 2010-12-24
Hi all,

I know this has been an issue to many others recently. I have read some posts relating to this issue but couldn't figure out what to do coz all seem to offer a different solution for different machines, configurations, etc.

OK, here it goes. I've just downloaded the latest version, burned it on a CD. I first wanted to try it without installing, so booted the computer from the CD, hit a key when the logo appeared at the bottom, choosed the language and selected the first option (try ubuntu). I got a screen full of white text with no particular meaning to me. Then, just in case, I checked the hash value of the iso using winMd5Sum utility, there was no problem with that. This time I thought I should check the CD, so I booted again and went for the 'check the CD' option and having watched this 10.10 text for about 10 secs or so right in the middle of the screen, I got these mixed text again on the screen - the only difference, this time they were kinda reddish colour, which was very nice indeed but this didn't solve the issue. I took a snap of the screen with the hope of that someone can figure out what the problem is.

Any suggestion appreciated,

Thank you in advance.

---

### Post by dino99 on 2010-12-24
your screenshot is a kernel panic

when trying to boot on cd/dvd: add noacpi (F6 if i remember)

if that dont work, try with either: nomodeset, nolapic, noapic, irqpoll

---

### Post by Bahokan on 2010-12-24
Yesterday, I did what you suggested, I selected noapic, hit the enter and put a cross on it but didn't work. I'll try the others but should try one at a time or select all?

---

### Post by Quackers on 2010-12-24
One at a time, I'm afraid.

---

### Post by Bahokan on 2010-12-24
I did everything you guys suggested but none of them worked. I even played with the line reading "file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash--" and deleted the last two words but no luck. I'll try the following and see if any helps: 

i915.modeset=0
xforcevesa
fb=false

Meanwhile, if anybody has a suggestion, please let me know.

Almost forgot, when playing around with those options you suggested, I saw two lines, I cannot remember exactly what they were saying but something like 'no medium found'. Could this be related to cd drive or something? Anyone has an idea?

---

### Post by Bahokan on 2010-12-24
I tried the aforementioned three boot options but they didn't work either.  The error lines I was talkin about in my last post are as follows:

/init:line 7: can't open /dev/sdc: No medium found
/init:line 7: can't open /dev/sdc: No medium found

I gave up the try option and decided to install ubuntu but ran into the same problem again: a screen full of error mesages. Could this issue be harware related?

---

### Post by rabbits on 2010-12-26
I am unsure whether I can help,,, however I have some questions :

Please list your hardware: cpu, ram, hdd, cdrom, and graphics card. 

"sdc" is the third mass storage device (hard-disk, CD or USB memory etc). Is this your CD-drive with the Live CD ?

Which version of Ubuntu LiveCD --- 10.10 ? Did you run a "check disk" using the utility available when booting from this "live" media?

Best wishes.

---

### Post by Bahokan on 2010-12-26
Rabbits, sorry for the delay in reply. I don't know where to start coz my brain feels almost exhausted. OK, let's start with the hardware:

Intel Pentium 4, 3000 Mhz (HT)
Biostar 865GV Micro 478
1024 Ram
Nvidia GeForce FX 5200, 256mb
Philips SPD6002T 
Seagate ST3802110A  (80 GB, 7200 RPM, Ultra-ATA/100) 
SAMSUNG SP0411N  (40 GB, 7200 RPM, Ultra-ATA/133) - Empty

It is 10.10 and checked the cd when booting but I got a screen similar to the one shown above, almost the same with numbers slightly different. 

Having seen the post in the following link, [http://art.ubuntuforums.org/showthread.php?t=1168703](http://art.ubuntuforums.org/showthread.php?t=1168703), I also turned off Acpi Function in the BIOS, but this didn't work either and got this error message:
[COLOR=Red]
(initranfs) Unable to find a medium containing a live file system. [/COLOR]

Does that mean that it cannot see the CD or something? I have a feeling that my graphics card may be the cause of the problem so I just wanted to disable it and used the on-board card. In the Device Manager, I disabled Nvidia and enabled the other one, plugged the cable into the new slot and restarted the computer and there comes the problem - I cannot see anything on the screen until XP Welcome screen. Do you know any other way to make the onboard graphic card work or in other words, make everthing visible on the screen right from the start?

---

### Post by rabbits on 2010-12-26
Bahokan, I am a little confused by your answer. You seem to boot into Windows instead of Ubuntu?  Please choose a configuration that you know is working (eg. that you can confirm works on Windows).  If Windows works with nvidia FX5200 than use that config to reduce the number of variables.

First work on the missing "sdc" and missing "live file system".

You don't seem to be able to run the "check disk" utility either.  I think your CD has some corruption. If you know how to, do a checksum of your downloaded ISO file to compare the hash-key with expected value. Or download the ISO again and burn another CD to try and get a "good" LiveCD.

Boot the "good" LiveCD; so that you can run the "check disk" on it.  Then boot and use the "Try Ubuntu" option, from there you can "Install Ubuntu" onto hdd. Later you reboot from hdd and install the nvidia proprietary drivers (,future discussion here).

I use nvidia 6150 integrated graphics successfully with 10.10, my installation was smooth; no need for "nomodeset" etc. My guess is that a good LiveCD will allow you to boot smoothly and install the 10.10 onto your harddisk,.

Don't worry about the nivida "hang" in that old post (for now), it happened to me with 10.04 or earlier, but no problem for me with 10.10

Let me know how you progress.  If you encounter further issues down the road, ask again.  Good luck.

---

### Post by Bahokan on 2010-12-27
Rabbits
 
This is to clarify your confusion. If  understood you  correctly, yes I can boot into windows without any problem. When I  restart the computer with the ubuntu cd in the drive, it sees the cd.  That means:
1. I can see the language selection page and choose the one I want, 
2.  Click on one of the options in the boot menu which is "Try Ubuntu  Without installing" OR "Install Ubuntu" OR Check Disc for Errors".

Clicking  on one of those options, however, brings up a bunch of error messages -  I have already mentioned about these. The thing I cannot understand,  however, if the cd is corrupted then none of those language and boot  options shouldn't come up on the screen, right? This is just a guess of  course, a corrupted cd may work up to a certain degree before it  produces error messages (maybe).

My computer is configured to run  with Nvidia, I disabled the onboard card to avoid conflicts and save  system resources. I wish I could try ubuntu installation with the latter  but as I indicated above, I couldn't make the onboard card work.  

As  for checking md5sum, I have already done a checksum of the downloaded  iso, there is no problem with that. But, as I said in another thread, I  don't know how to check the integrity of the cd under windows. I visited  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) already but instructions  given there are all Linux commands and I am not too sure if I can use  those commands under windows - if yes how - or when booting from ubuntu  cd.

---

### Post by dino99 on 2010-12-27
how have you burn that cd ? you always have to choose the slowest speed when burning, and select the "alternate" iso when downloading from ubuntu [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by rabbits on 2010-12-27
Bahokan, it is clear now.  The ISO download file is OK based on your checksum.  I cannot offer any Windows advice for MD5sum. When I google I found some Windows apps for md5sum which I have not tried.

Your hardware configuration with nvidia graphics is working with Windows, and I think will be OK with 10.10 installation.

I understand you got partially into the LiveCD; until the "Check Disk" or "Try" or "Install" selection screen.  I still suspect the CD has corruption,  in a later part of the disk.  If the fault is repeatable (always after check/try/install selection) then it is less likely the CD drive dirty/faulty, but still a slight chance.

I still suggest to blank+ re-write the CD again or (better still) write a second CD.  Or figure out how to checksum using Windows app.  

If you have access to a second PC, try and boot up this LiveCD on another PC and get to the "Check Disk" and "Try" stages to confirm the CD is OK.

My own opinion is that 10.10 installation is very straight-forward, I have done it on 2 desktops and 2 laptops, (all different h/w config, 3 ATI graphics, 1 nvidia graphics) ---no problems encountered.  I suspect the CD or CD-drive.

Meantime, perhaps someone else can offer a better idea.

---

### Post by Bahokan on 2010-12-30
I downloaded the alternate iso and burned it onto a disk. To my surprise it works but during the partitioning process, it gives an error. I have two HDDs installed so from the partitioning menu I selected the option "Guided - use entire partition, SCSI1 (0,1,0), partition #1 (sdb)" which represents the second HDD. 

After root and swap parts were created, it says "The attempt to mount a file system with type ext4 in SCSI1 (0,1,0), partition #1 (sdb) at / failed."

Am I doing something wrong or does it have to do something with a hardware issue?

---

### Post by rabbits on 2010-12-30
Bahokan,  I have no experience with the alternate-CD.  I see it is text-based and not GUI based but it should work.  I cannot tell whether this is hw or sw issue.   If you are comfortable with alt-CD, you can experiment with &quot;manual&quot; hdd partitioning, and/or install onto SDA instead of SDB.  For experiment a small partition, maybe 8 GB HDD space is sufficient and 1 GB swap. You may need to shrink the windows partitions to create space on a HDD. Just remember a maximum of 4 primary partitions on each hdd; or 3 primary and many logical partitions ok.  [If not comfortable with text, re-write the LiveCD and try again.]  You are having a tough time with installation, but I really think you have an unusual situation. You will soon find that Linux-Ubuntu is faster than windows.    BTW, I create a separate /home partition; so that I can upgrade a fresh Ubuntu say, 10.10 to 11.04, in future without needing to backup/restore the /home.  Others will say backup is still neccessary, but no need to 'restore' if the /home has not been over-written during the sw upgrade.  Keep trying.  Good luck.

---

### Post by Bahokan on 2010-12-31
Rabbits

I finally managed to install from the LiveCD (not alternate) . I still cannot believe it, after struggling for almost 5 days, it just happened. You'll recall that in one of my previous posts (#eight), I said that the video card may be the cause of the problem. And this turned out to be true, it was Nvidia fx5200. For some reason, I couldn't get the on-board card worked on that day but playing with some settings in BIOS solved the problem. As soon as the on board card was up and running, the installation went smoothly. Now everything seems OK.

There is, however, a little problem I am experiencing now. Having finished the installation, I re-enabled the Nvidia and but cannot boot into ubuntu, I mean all I see is a black screen. I have to go back to on board again and will try to sort it out in System > Administration > Additional Drivers and see if it works. Btw, is it possible to use my existing usb modem in ubuntu to connect to the net or should I use the ethernet card supplied on the motherboard?

---

### Post by rabbits on 2010-12-31
Glad to hear your progress!  About USB-modem: do you mean USB-WLAN or USB-WAN (Router/ISP)?  I myself like to use (wired) LAN-ethernet to avoid wifi drivers.  To install wifi/WAN drivers you can try >System>Admin>AdditionalDrivers.  Not all USB-WLAN have drivers available, I have mixed success about this.  I had better luck with USB-3G modems. 

After your experience, I realise that nvidia installation is still not smooth on 10.10;  I would like to learn what you turned on/off on the nvidia card (thru the BIOS). If this is the case, you could TRY (I have not encountered this before) to turn off/on the nvidia card, boot up into Ubuntu; then run >Admin>Synaptic to install nvidia-173 driver; shut-down, enable nvidia, reboot and fingers crossed.  Alternatively try nvidia-96 driver, both 173 and 96 are claimed to work up to GeForce7 altho I have not tried -96 in recent years.

Is the black-screen associated with turning on/off nvidia card,  different from the earlier issue of no-medium, no live file system?  Just wondering whether you also have intermittent CD errors.

Happy New Year !

---

### Post by Bahokan on 2010-12-31
I don't know much about all these technical stuff coz I have been using this usb modem for almost 6 years and never needed another one. I know that there are so many different types out there but honestly I don't know what what kind modem it is - all I know is it is a usb modem with single port connected to one of these usb ports at the back of the pc. I am not too sure but it could be a usb-wan.

To get the on board card worked, it is not just enough to enable it and disable the Nvidia in the Device Manager. In the BIOS, there is a setting which allows you to start the desktop with either an AGP card OR on board one.  Anyone following this procedure should, of course, plug the cable into the right place at the back of the computer before playing with the BIOS.

I got the black screen coz I hadn't turned off the AGP card (Nvidia) in the BIOS. In the Device Manager, it was set to start the computer with the on board card but in the BIOS it was opposite. Consequently, that is why I saw the blcak screen.

As for the CD, no there were no cd errors. All those error mesages you mention were related to the Nvidia apparently. No Nvidia no problem.

Happy new year and many thanks for the hand.

---

### Post by rabbits on 2010-12-31
Bahokan, your description is correct: now I recall I used USB-Modem  10yrs ago also,  ADSL or cable-modem with USB connection to PC (with Windows only).  I recall lack of linux drivers for these USB modems in those days, not sure about nowadays.  Today, many people have a Router with wired-LAN or wifi between modem and PC, so I needed to clarify.

To discover what sort of usb-modem: run >Accessories>Terminal and run "lsusb" command; see below my usb devices are mouse and wlan adapter.  If ">AdditionalDrivers" doesn't find you a driver, you may have to google search for modem-driver etc etc,,, a little messy.

ex@Compaq-V3000:~$ lsusb [Example of LSUSB]

Bus 002 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ex@Compaq-V3000:~$ 

To summarise your problem (for anyone else reading this later on), you can boot 10.10 Live CD with (integrated) onboard graphics but unable to boot with nvidia FX5200 (dedicated graphics card).  It is necessary to disable the nvidia card in the BIOS to use the integrated graphics.

You haven't mention whether after booting with integrated graphics, you can  use >Synaptic to install nvidia-173 driver,then Reboot using the dedicated nvidia graphics thereafter.  Oh wait, you need Internet connection to get the nvidia driver,,,, or even to get the modem driver.

It does appear that wired LAN-modem will be more straight-forward for installation.  Sorry, it takes a little extra effort to get the first Linux installation running.  Funny this,, as I demonstrated the lsusb command above, I found that the Ralink wifi adaptor suddenly starts to work !!:lolflag:  Before,  I was manually searching for Ralink drivers because 10.10 could not detect and find the driver for me.  Usually new hardware takes time before a Linux driver is available, but your "old" computer is an example of old hardware not being detected/installed with drivers.  I have to thank you for "finding" me a Ralink driver in the New Year !

Good luck again. It gets easier from here.

---

