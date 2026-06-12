---
title: "newbie having loads of problems installing on netbook and on PC"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by rienvanhoutte on 2011-04-04
i am trying to install ubuntu for 3 days now and it never gets to the hard disk part... i am trying to find the info but did not find what i was looking for.
64-bit PC (AMD64) alternate install CD was the last resort i could try to install it. i have 64bit pc now i'm running W7 but i hate it

i also tried it by usb, normal, 64bit,... maybe i have a problem with my hard disk... 

on my netbook (Aspire one) i have the same problem of not getting past the preparation... it runs perfect if i try ubuntu(pc too).
here i tried ubuntu and kubuntu but still having the same issue

tell me what u need(outprints of code's)

thx in advance
:popcorn: i'll be waiting...

---

### Post by Dutch70 on 2011-04-04
Hi and welcome to UF

Anyone that can help you will probably need...
Computer specs, mainly graphics card & RAM
What you are using to install
Which version of Ubuntu you're installing
Is it a dual boot or are you wiping windows7
What problem you're having

Best to read this first...
[[COLOR="Red"]how to get your support questions answered as quickly as possible[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by mastablasta on 2011-04-04
also (in adition to you posting the information needed to help you) does it run in live version (boot from disk and select "try it")?

---

### Post by rienvanhoutte on 2011-04-04
i have a acer aspire one AOD250, 1GB RAM, Intel Atom CPU N270 @ 1.60 GHz, 32 bit. no cd player so i have to use usb to boot. HDD Toshiba MK2555GSX(W7 say's there's a smart event so i would like to format) 
it works fine in live version. i try'd to install the 10.10 and netbook remix. 
they both keep hanging in the preparation(just before i would see my hard disks it seems)... this is the first one... i'll start with this one

need more info?

i would love to install kubuntu but i had the same problem there...

---

### Post by Dutch70 on 2011-04-04
Have you tried Ubuntu or Kubuntu 10.04? You may have better luck with it. It's not much different from 10.10, but 10.04 is the LTS (long term support) version.

If you're dual booting with windows, don't use the "install side by side" feature. I've heard it can mess up your windows install.

I'm not familiar with the acer aspire, but I've seen a lot of post on here about it lately. Hopefully one of these people will see your post now, and chime in. 

Other than that, you may be able to find a post in here that helps you, I'm sure you're not the first to have this problem with that computer. 

Best regards

---

### Post by Hedgehog1 on 2011-04-04
First: What is the SMART event windows gave you?

Second: Please boot off the LiveCD/Live USB, select 'TRY', and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by lindsay7 on 2011-04-04
> **rienvanhoutte said:**
> i am trying to install ubuntu for 3 days now and it never gets to the hard disk part... i am trying to find the info but did not find what i was looking for.
64-bit PC (AMD64) alternate install CD was the last resort i could try to install it. i have 64bit pc now i'm running W7 but i hate it

i also tried it by usb, normal, 64bit,... maybe i have a problem with my hard disk... 

on my netbook (Aspire one) i have the same problem of not getting past the preparation... it runs perfect if i try ubuntu(pc too).
here i tried ubuntu and kubuntu but still having the same issue

tell me what u need(outprints of code's)

thx in advance
:popcorn: i'll be waiting...

Have you tried the 32 bit?  Your computer is a 32 bit.

---

### Post by Hedgehog1 on 2011-04-05
**lindsay7**,

You may well be right - the Intel web site does not indicate that the processor is 64 bit at all ([Atom-Overview]("http://edc.intel.com/Platforms/Atom-N270/#overview")).

In any case, the amount of RAM this system can support is small enough that the 32bit version of Ubuntu can access it all.


***The Hedge***

:KS

---

### Post by rienvanhoutte on 2011-04-05
> **lindsay7 said:**
> Have you tried the 32 bit?  Your computer is a 32 bit.

i tried 32bit for netbook...

64bit was on PC

---

### Post by rienvanhoutte on 2011-04-05
> **Hedgehog1 said:**
> First: What is the SMART event windows gave you?

Second: Please boot off the LiveCD/Live USB, select 'TRY', and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

this is what i got from the sudo fdisk -lu code

Disk /dev/sda: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x807b6908

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8064     7831551     3911744    b  W95 FAT32

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2f64a382

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    25173854    12586896   27  Unknown
/dev/sdb2   *    25173855    25382699      104422+   7  HPFS/NTFS
/dev/sdb3        25382700   488395119   231506210    7  HPFS/NTFS

---

### Post by rienvanhoutte on 2011-04-05
the weird thing is the netbook runs like there's no problem...

in the ubuntu 10.04 LTS version ist says the problem is the reallocated sector count is failing...
Raw: 00xff0700000000


and this is the report from the smart event in W7...


System Information

Kit Installed: 8.9.0.1023
Kit Install History: 8.9.0.1023, Uninstall
Shell Version: 8.9.0.1023

OS Name: Microsoft Windows 7 Starter 
OS Version: 6.1.7601 Service Pack 1 Build 7601
System Name: LAPTOPJERIEN
System Manufacturer: Acer
System Model: Aspire one      
Processor: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
BIOS Version/Date: Acer V1.29, 12/18/2010

Language: ENU



Intel(R) Matrix Storage Manager

Intel Serial ATA Controller: Intel(R) ICH7M/MDH SATA AHCI Controller
Number of Serial ATA ports: 2
 
Driver Version: 8.9.0.1023
Serial ATA Plug-In Version: 8.9.0.1023
Language Resource Version of the Serial ATA Plug-In: 8.9.0.1023
ISDI Library Version: 8.9.0.1023
 
Hard Drive 0
Status: SMART event
Device Port: 0
Device Port Location: Internal
Current Serial ATA Transfer Mode: Generation 1
Model: TOSHIBA MK2555GSX
Serial Number: 99I4P9Q0T
Firmware: FG001J
Native Command Queuing Support: Yes
Size: 232.8 GB
 
Unused Port 0
Device Port: 2
Device Port Location: Internal

---

### Post by rienvanhoutte on 2011-04-05
> **Dutch70 said:**
> Have you tried Ubuntu or Kubuntu 10.04? You may have better luck with it. It's not much different from 10.10, but 10.04 is the LTS (long term support) version.

If you're dual booting with windows, don't use the "install side by side" feature. I've heard it can mess up your windows install.

I'm not familiar with the acer aspire, but I've seen a lot of post on here about it lately. Hopefully one of these people will see your post now, and chime in. 

Other than that, you may be able to find a post in here that helps you, I'm sure you're not the first to have this problem with that computer. 

Best regards

have tried it but i have the same problem... the installation does not get to the point where i can format my hard drive....

---

### Post by rienvanhoutte on 2011-04-05
> **Hedgehog1 said:**
> First: What is the SMART event windows gave you?

Second: Please boot off the LiveCD/Live USB, select 'TRY', and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -lu
```Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

smart system says disk failure is imminet, have the same problem installing the 10.4 lts version, it stops at the hard disk drive... i can't format the drive too(i would like to try to see if i can aviod to buy a new hd)... i am working on the live version now.

---

### Post by Dutch70 on 2011-04-05
Unless you're hdd is really old, I'd check to see if it's still under warrany.

---

### Post by Hedgehog1 on 2011-04-05
> **rienvanhoutte said:**
> smart system says disk failure is imminet, have the same problem installing the 10.4 lts version, it stops at the hard disk drive... i can't format the drive too(i would like to try to see if i can aviod to buy a new hd)... i am working on the live version now.

OK - the "disk failure is imminent" is why your install will not work. The install uses parted to do disk manipulation, and parted will not change things when the disk is in this bad of shape.

Please back up any data you can from your hard drive.  You will need another one.  If it is under warranty you might save some money (I just replaced a laptop hard drive - 320 gig was $50 USD from newegg).

The screen looked like this in the System >> Administration >> Disk Utility (from the liveCD):

[IMG]http://img225.imageshack.us/img225/7057/diskfail03.png[/IMG]

A new OS will not fix this.  Sorry.

***The Hedge***

:KS

---

### Post by rienvanhoutte on 2011-04-06
ok, thx guy's, now i have the ubuntu  10.4 lts on my pc and it works perfectly(like someone suggested).

my netbook is going to a asus serice center 4 a new hard drive and i will see when i get it back(i fear it's going to take a long time...)

---

### Post by Hedgehog1 on 2011-04-06
Let's hope your netbook isn't gone for too long.  We want you Ubuntu(ing) at home and on the road!  You need that netbook for the 'on the road' part.


***The Hedge***

:KS

---

