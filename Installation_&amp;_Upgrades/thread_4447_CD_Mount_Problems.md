---
title: "CD Mount Problems"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by PrpleGkEtr on 2004-11-15
Hi everyone, I'm an absolute linux newbie and am trying to install warty on a new system that already has XP installed.  I am able to get the image CD to boot up and enter my language and keyboard layout.  I then get a screen with a header "Detect and Mount CD-Rom" and the message "No common CD-Rom drive was detected".  The prompt then asks for floppies containing the CD-Rom drivers.  The message further insinuates that I may have non-standard CD-Roms, but both my primary and secondary optical drives are stock EIDE (and the same thing happens on both).

Does anyone know what I can do\why this is happening.  I've tried looking around, but could not find anything addressing this issue, although I admit that I may not be looking in the right places.

Also, Knoppix works fine on the system.

Specs:
Gigabyte GA-8IPE1000PRO-G ATX RT
Intel P4 2.8 GHz
1 GB Ram
80 GB WD SATA HD
LG 52x CD-Rom
Sony 16x CD-DVD-RW


Thanks everyone

---

### Post by jdong on 2004-11-15
Have you tried reburning the CD-Rom and/or trying your other drive?

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=PrpleGkEtr]Hi everyone, I'm an absolute linux newbie and am trying to install warty on a new system that already has XP installed.  I am able to get the image CD to boot up and enter my language and keyboard layout.  I then get a screen with a header "Detect and Mount CD-Rom" and the message "No common CD-Rom drive was detected".  The prompt then asks for floppies containing the CD-Rom drivers.  The message further insinuates that I may have non-standard CD-Roms, but both my primary and secondary optical drives are stock EIDE (and the same thing happens on both).

Does anyone know what I can do\why this is happening.  I've tried looking around, but could not find anything addressing this issue, although I admit that I may not be looking in the right places.

Also, Knoppix works fine on the system.

Specs:
Gigabyte GA-8IPE1000PRO-G ATX RT
Intel P4 2.8 GHz
1 GB Ram
80 GB WD SATA HD
LG 52x CD-Rom
Sony 16x CD-DVD-RW


Thanks everyone[/QUOTE]

You know I have experienced the same problem.  The first install went through completely normal.  Then the second install wouldn't detect my CD at all.  It was the same CD and the same condition.  So I figured hmm...lets give it some boot parameters.  

I added:
```
expert
```
to the boot: parameter at the initial stage.  This prompted a lot more questions but they are pretty much point and click.  

After this, it detected the CD just fine.

---

### Post by PrpleGkEtr on 2004-11-15
I've tried both drives (they give the same problem), but have not tried re-burning the CD.  I take it  from the lack of replies that this is not a common problem? <sigh>

I will reburn the CD when I get home and reply with the results.

---

### Post by PrpleGkEtr on 2004-11-15
jdong: I had tried it on both drives (and switched around which was master and which was slave too), to no avail, but I haven't tried reburning the disks.

FleiXiuS:  Thanks I'll try that when I get home from work and give you all an update.

Much appreciated, I can't wait to use ubuntu!

---

### Post by mr_ed on 2004-11-15
[QUOTE=jdong]Have you tried reburning the CD-Rom and/or trying your other drive?[/QUOTE]
 It sounds more to me like a bad burn than the drives.

Verify that your md5sum matches, and that you burn it at a slower speed listed on your disc.

If you're using Windows, there are a few md5sum programs listed here:
[http://www.handhelds.org/z/wiki/md5sum](http://www.handhelds.org/z/wiki/md5sum)

If you don't have a clue what I'm talking about, this program will verify what you downloaded matches the one provided on Ubuntu's site, which are listed here:
[http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS)
This is the i386 ISO's md5sum.
a491903a2d2197651864dec3836d85e0

So basically, you run one of those md5sum programs on the .iso file that you downloaded, and if the big string of numbers that you get as a result matches the one on Ubuntu's site, it means your download was correct.  Believe me, it happens sometimes when they don't match.

---

### Post by FLeiXiuS on 2004-11-15
[QUOTE=PrpleGkEtr]jdong: I had tried it on both drives (and switched around which was master and which was slave too), to no avail, but I haven't tried reburning the disks.

FleiXiuS:  Thanks I'll try that when I get home from work and give you all an update.

Much appreciated, I can't wait to use ubuntu![/QUOTE]


The expert install is actually quite nifty, i'm now using it with all of the releases  :-s

---

### Post by PrpleGkEtr on 2004-11-16
OK, an update:

I first tried the expert install and didn't get anywhere new.  I then reburned the image at a slower speed and that also didn't work.  Further, I checked the md5Sum and it matched up as well.

Any more suggestions?  Note that I downloaded the live release of warty and that booted up without a problem.

Thanks

---

### Post by FLeiXiuS on 2004-11-16
Which cd rom tray did you place Ubuntu in?

LG 52x CD-Rom
Sony 16x CD-DVD-RW

---

### Post by PrpleGkEtr on 2004-11-16
Fleixius:  I tried it in both.  The LG was set as master and I didn't  switch that around, but I didn't think that would matter.

---

### Post by mattisking on 2004-11-17
I'm having the same problem. I have an ABIT Digidice with a single "Mad Dog Dominator 6-in-1 8X DVD+-R / +-RW" drive mounted as Master on it's own IDE channel. The only hard drive is a SATA drive also set as Master. There is no floppy drive, but there is a generic card reader included.

I checked the md5sum for my download (Warty i386 ISO) and it matched perfectly and the CD burn went fine and the CD appears to be fine. I will attempt another burn but I have VERY few CD burning problems (up to now... none) with this drive. 

Windows XP boots fine and I have a large amount of space set aside for Ubuntu. The Ubuntu installation boots fine from this CD but just as the user reported above, fails to mount the CD. Help? :confused:

---

### Post by MatthewMetzger on 2004-11-26
Is there a network install that would work as an alternative to CD install? I'm having the same problem. One similarity is that I'm using an ABIT board with a Serial ATA hard drive. Any help would be greatly appreciated.

Thanks.

---

### Post by jaspeers on 2004-11-29
This seems to be an issue with the debian-installer.  I had the same thing going on with Debian and Ubuntu last month when I tried to put them on my system.

It looks like everyone with these problems has the same setup I had:  One SATA drive and a CD-Rom drive on it's own channel.

I searched and searched and asked around for over a week before giving up and putting Mepis on, which uses a different installer but is also based on Debian.

So when these problems pop up, it's not a bad CD burn or anything.  There's some kind of bug with the debian-installer that I haven't found any help for yet.

---

### Post by rthunstrom on 2004-11-29
Hi everyone,

I also have the same problem. The computer i´m trying to install Ubuntu on:
Shuttle SB61G2 V3
HIS Platinum ATI Radeon 9600XT 128Mb
2 x KVR400X64C25/512 ( KINGSTON PC3200 DDR)
Intel P4 2,8GHz 800/512K, HT
SEAGATE BARRACUDA 7200.7 120GB 8MB SATA
**..and NEC DVD±RW 8X IDE [COLOR=Red]ND2500A[/COLOR]**

I had Suse 9.2 Pro installed a couple months ago with no problems at all on the same computer.

I´ve also checked the iso and the burnt CD with no error indication.

Is it possible to install Ubuntu in some other (simple) way?

 :confused:



[COLOR=SeaGreen]**>> Update <<**[/COLOR]

Now I have tried "all" different tips given in this forum and others but with no success ..  :(

I don´t understand why I get the message [COLOR=Red]"No common CD-ROM drive was detected"[/COLOR] when I try to install Ubuntu from... _a CD-ROM drive!!!_ (ok, a DVD drive but the installation is still on CD/DVD media).

Can it be because i don´t have a floppy disk drive?!?

I want Ubuntu on my computer :(  Please, help me someone!

---

### Post by bluewool on 2004-11-30
Hello guys, this is the first time I've ever posted a message, hope it helps. I had a similar problem loading Ubuntu on my P4 with DVD/Rw and SATA hard disk, I made some changes to the bios setting which help. Instead of setting the SATA mode to "auto", I changed it to "enhanced" and low and behold it works. I had Slackware 10 loaded prior to Ubuntu, it worked without the bios changes. Good Luck!

---

### Post by rthunstrom on 2004-11-30
I´ll try your suggestion [COLOR=Blue]bluewool[/COLOR] when I get home from work.  

87 minutes left..   8-[




..maby I also should mention that I tried to install Fedora yesterday evening  :smile:

---

### Post by rthunstrom on 2004-12-01
Thank you [COLOR=Blue]bluewool[/COLOR]! Your suggestion solved my problem. I changed the setting for SATA from Auto to Enhanched in BIOS and then there was no problem installing Ubuntu.

My first impression of Ubuntu is -"Wow! Nice!".



Now I have some other problems to solve like:
Uhh? Why is GRUB telling me that <Windows root>\system32\hal.dll is missing or corrupt? Can it be because my MS Windows is installed on my D:\ partition?

and

I wonder how to install WEP for my Netgear WG311 ver 1.0, I got it working in Suse 9.1 Pro so it should not be a problem.

 :D

---

### Post by tacubuntuforums on 2004-12-01
[QUOTE=mr_ed]It sounds more to me like a bad burn than the drives.

Verify that your md5sum matches, and that you burn it at a slower speed listed on your disc.

.......[/QUOTE]

I wanted to try that but handhelds.org seems to have flown away.

---

### Post by rthunstrom on 2004-12-01
[QUOTE=tacubuntuforums]I wanted to try that but handhelds.org seems to have flown away.[/QUOTE]
 tacubuntuforums, I downloaded MD5Sums from [http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/) (MS Windows)

---

### Post by ensiferum on 2005-01-04
Yeah, I'm having the same problem.

I'm running Abit's IC-7, Intel 875P chipset. In my configuration I've got 2 SATA hard drives and 2 legacy cd-rom IDE drives. 

With combined mode set in BIOS, (this mode has SATA devices in IDE 0) I can boot off the CD just fine. But get the same error ("no common cd-rom was found yadi yadi blah blah") when it tries to install the base system.

With SATA disabled in BIOS, installer detects the CD-ROM fine, but then again I don't have any hard drives on which to install anymore.

With enhanced mode (this mode has SATA and both IDE channels enabled) the installer detectes the cd-rom fine but hangs when trying to load some SCSI driver. 

I tried to run the installer in expert mode and look for the offending SCSI module and disallow it from loading to no avail. On that note, I also tried loading ata_piix module with modprobe, since the installer keeps on telling that that specific module is needed but could not be loaded. 

And to all you guys screaming "it's a bad burn!!11" or "bad cd!!1one", or some other crap about "bad" hardware or "bad hardware configuration", the fact is that it's the installer that's broken. And broken badly. (I have slackware/xp running just fine on the system, and the same cd was used to install ubuntu on some other pc)

All in all, it seems to be such a shame that the installer doesn't work properly with systems with SATA disks. The distro seems pretty cool and nifty otherwise.  

Also I must note that all kind of trickery to workaround the problem "install on some other hd and migrate the system later onto a SATA disk, etc" is just plain unacceptable.

---

### Post by beatdown on 2005-03-19
Hi all,

I had the same problem with a Gigabyte motherboard,SATA and ubuntu. The same happened when installing debian with kernel 2.6 (ubuntu include 2.6 too, so the problem could be with that kernel version). 2.4 kernel version worked fine on debian.
Now I am running ubuntu warty, my SATA HD is /dev/sda (I think this means it is treated like a SCSI device) and I cannot find my IDE CD-ROM devices in /dev to mount them... ¿? I will move to hoary preview this week, perhaps this problem will be solved...

The solution I used to solve my problem:
[http://www.ubuntu-es.org/node/1350](http://www.ubuntu-es.org/node/1350)


Bye.

---

### Post by beatdown on 2005-03-21
It's me again. I have removed warty from my HD and installed hoary-preview. I tried to solve the problem by another way :

I entered into my BIOS and configured the SATA Devices to map to SATA0 and SATA1, instead of IDE1. Now it detects my CD-ROMs during installation and after installation (/dev/hdc and /dev/hda). And my SATA HD is also running fine as /dev/sda.

I think this will work with the Warty release and debian too. I think it was a problem between the debian installer and the SATA mapping.

Did you all solve the problem?

---

### Post by ietiland on 2005-03-21
dear all,

   I have the same problem , on ubuntu 4.10 and 5.4 preview......
I will try to chang expert mode and SATA setting, thinks for help.

---

### Post by ubuntu_seeker on 2005-03-23
All, I *also* have the same problem:

Please see my thread at:

[http://www.ubuntuforums.org/showthread.php?t=18807&highlight=cd+detect](http://www.ubuntuforums.org/showthread.php?t=18807&highlight=cd+detect)

I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD/DVD drive, meaning, it could not find a driver for my CD/DVD so then I have to stop the installation. That is, I keep ending up back at the install menu where it says that the CD drive has not been detected yet. It asks me if I want to pick a driver from a list, and I've tried various ones "cdrom" etc. with no luck.

I've seen others post about this same problem in several places (at least 3 threads), but still there have been no replies... hoping for one soon.

My hardware is: Dell XPS Gen 3 (Pentium 4 3.6 GHZ), DDR-2 RAM, SATA 7200 rpm hard drive.

The CD-ROM is a CD / DVD RW combo drive... I believe it's an IDE drive.. listed in XP properties as "HL-DT-ST DVD+RW GRA-4120B".

MEPIS had no problem detecting my CD drive. And the drive works just fine in Windows XP SP2.

Thanks for any ideas!!! :^D.

I'd really like to be able to try out the live CD before installing Ubuntu. I'd much prefer to go with Hoary since Warty is kinda out of date by now.

I wish I could install Ubuntu....

================

The problem appears to be with the ata_piix module which requires a fix:

[http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=18808&page=2&pp=10)

I have never heard anyone talking about when that fix might appear... :( ... might have to just go with MEPIS I guess...

Btw, my SATA HD is Master and my CD / DVD IDE is also Master...  there is a "combo SATA / PATA" mode which may make the CD detectable, but people say that then you may not be able to access your XP partition... so that's not an option...

need ata_piix fix.

[QUOTE=ietiland]dear all,

   I have the same problem , on ubuntu 4.10 and 5.4 preview......
I will try to chang expert mode and SATA setting, thinks for help.[/QUOTE]

---

### Post by dnjuls on 2008-07-20
My bios was mapping SATA to IDE. After changing that setting to AHCI things seem to work better.

Dan

---

