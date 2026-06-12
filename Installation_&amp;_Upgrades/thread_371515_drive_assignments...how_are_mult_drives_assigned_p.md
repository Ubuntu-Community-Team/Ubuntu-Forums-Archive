---
title: "drive assignments...how are mult drives assigned? potential grub error"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by joeindo on 2007-02-27
Am preparing to do an install of ubuntu 6.10 on a pc with: ide 0 - dvd/rw drive master - slave empty, ide 1 dvd/rw master - slave empty, sata channel 0 160 gb segate, pata channel 0 160 gb western digital, pata channel 1 60 gb western dig...

Now I've set my bios to make the **sata drive the 1st hard drive** and also set the dvd/rw to boot first. When I look at this via XP and norton partition magic or acronis partition expert - I see that the sata drive is the 1st drive and the 160 gb drive is the 2nd drive and the 60 gb drive is the 3rd drive...
[IMG]http://farm1.static.flickr.com/125/404332248_f7fb2ecbdc_o.gif[/IMG]
I want to install / to my 2nd partition on the sata drive and swap will be the 3rd partition. I am planning on using a boot utility (acronis os selector) that has been successfully installed to mbr of the sata drive to handle the boot loaders of the 2 OS's.

Here's were things get silly... when I boot from my ubuntu alt install disk and get to the partioning section of the install, here's what I'm told:

[B]sda: 160 west dig - pata
sdb: 60 west dig - pata
sdc: 160 seagate - sata[/B]

**the above is kind of bassackwards **from what I've told bios and also from what I see in windows... What I'm afraid will happen is that I'll install grub to to / or /media/sdc1/ and when I go to boot - grub will poop out since I'll install to /media/sdc1/which is actually /media/sda1/ (as seen by windows-are you with me so far?) .... 

My question is how is windows seeing my drive assignments correctly and ubuntu's partitioner is not? And - how can I fix this?!
:confused: 

The motherboard is an asus A8V latest bios... 

Any ideas? Many thanks ! :)

---

### Post by joeindo on 2007-02-27
Anyone have anything on this? 

I've seen this post: [http://ubuntuforums.org/showthread.php?t=296700](http://ubuntuforums.org/showthread.php?t=296700)

But am looking for some assistance trying to understand why Ubuntu is seeing the drives in a different order...

---

### Post by joeindo on 2007-02-27
:guitar: 

Okay, so I fixed this "problem"... Well, that is I found a work around...

On my Asus A8V Deluxe mobo there are  ide channels supprting 4 drives total, a promise pata channel supporting 2 drives - the promise chip, in addition to the pata drives supports 2 sata drives as well. There is also a via chip that supports 2 sata drives.

What I had originally was dvd/rw as master on each ide channel, two hard drives on the promise pata channel and a single sata hard drive on the via channel. I set bios to consider the sata drive as the 1st drive and that is what windows saw as well BUT when I went to install Ubuntu, the partitioner saw the sata drive as the 3rd drive or sdc... Why? I have no clue - I tried disabling the 2nd ide port, looked to enable/disable AHCI on the south-bridge chip that controlled the via sata ports - nothing seemed to matter - I could install Ubuntu to the sata drive and also installed grub to /dev/sdc2 but when trying to boot - I'd get to the grub menu, select "ubuntu" and then get "error 22: no such partition.... ugh !!!

Here is what I did: I disabled the via sata and disconnected the drive from that connector. Luckily, since windows installed the promise drivers to support the drives on the pata channels I was able to connect my sata drive to the promise sata mobo connector - essentially, this meant that the promise chipset was supporting 3 drives. Windows still identified and saw the sata drive as the 1st drive...

This time, when I booted from CD - the partioner now saw the sata drive as the 1st drive - hurray !!! I installed Ubuntu and set grub on /dev/sda2 and am now able to dual boot...

what a pain...! :lolflag:

---

### Post by Patrick K on 2007-02-27
WOW, that's quite a bit of pain. Glad you got it worked out. I sure wouldn't have.

---

### Post by joeindo on 2007-03-02
well... sad news.

My sucessfull install was doing fine until I went and installed automatix and it screwed up my nvidia drivers and x would not start... I figured - what the heck - I'll just reinstall...:confused: 

Um, hello? WTF? Ubuntu's partitioner is reading my drives all wrong again... !!! It see's mt sata drive as drive 3 - when it is actually drive 1 and calls it "hdc" when it should be "sda"

Is this a glitch with the board or with ubuntu's partioner?

---

### Post by joeindo on 2007-03-03
The saga continues... This is making me crazy - literally...

Anyhow, what I have now done with this asus a8v deluxe board and my 3 hdd's is this. I have a sata drive on my via sata channel, a eide drive on the promise pata channel and a drive on as slave on the primary eide channel (slave to a dvd/rw drive).

What's weird now is this. In the install I set up root and grub on /dev/hdb2 - when I go to boot - grub poops the bed so to say and I get an error about a partition not existing.... So I esc back to the grub menu and edit the 1st line to read: _Root (HD2,1)_ hit "B" to boot and the damn thing boots. Why does the partioner see things one way and grub see them another????

If I read my device.map file it says: 
[U](hd0)	/dev/hdb
(hd1)	/dev/sda
(hd2)	/dev/sdb[/U]


And if I read menu.lst it says:
[U]title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot ...etc...[/U]

Now - how do I fix this? Why is the line for the kernel correct /_boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash_ but the line for root wrong _root		(hd0,1)_? 

Why ?:roll:

---

### Post by SuSUntu on 2007-03-03
Your post #6 here is the easiest to answer, at least in a practical way, since I have to go through similar steps editing Grub and then menu.lst with every new install and with every kernel upgrade. Be warned that this will not answer the question of why it occurs.

I have experienced this particular behavior (the Grub edit issue) with every Ubuntu version I have ever used (Breezy, Dapper, Edgy). I never had this problem with Centos or Suse.

In my case, I install the boot loader to /dev/sdb11 (which in Grub notation should be (hd1, 10) ). Upon first boot EVERY TIME I install Ubuntu, I get the error 22 (no such partition), and then have to edit the boot menu to read **(hd1, 10)** instead of the incorrect **(hd2, 10)**. Just as in your case, the other references in Grub to the boot location using partition notation (e.g., /dev/xxx) is correct.

After first successful boot to my desktop, I immediately edit all instances of (hd2,10) in menu.lst to reflect the correct boot record location and all is good **until the kernel is upgraded**. After each upgrade, all menu.lst references to (hd1,10) is reset incorrectly to (hd2,10) so I have to manually edit menu.lst again.

All of this is simply a routine I have come to expect with Ubuntu and is only disconcerting when it happens the first time as your posts attest. I never went through the gyrations of trying to rewire my entire system like you did :) , but it did slow me down a bit when I first installed Breezy.

Finally, during installation of Linux, I always use /dev/xxx notation to identify where the boot loader should be installed because I am very leery that using Grub notation might install the loader to the wrong partition (especially in the case of Ubuntu where it thinks (hd2, 10) = /dev/sdb11). I have no direct knowledge that the issue we're discussing would cause the boot loader to be installed to the wrong location, but I prefer not to take the risk. :)

I will post a longer response to your other assertions, observations and problems shortly.

---

### Post by SuSUntu on 2007-03-03
By the way, before I get into my theory of why Grub / menu.lst has to be edited, I wanted to point out that I have absolutely no clue why your installation is incorrectly identifying your PATA disks as sdx and your SATA disks as hdx or vice versa. I have never seen this, and I wouldn't have believed it had you not insisted that it is occurring.

I actually was going to suggest you slow down and reassess your observations, but in post #6, you show that:

> 
If I read my device.map file it says:
(hd0) /dev/hdb
(hd1) /dev/sda
(hd2) /dev/sdb


Based on what I have read of your setup (irrespective of ORDER which we agree to be an issue), I would expect to see something like this since you have two PATA disks and one SATA disk:

```

(hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/sda

```

Someone else will have to address this issue.

---

### Post by SuSUntu on 2007-03-03
Now, to the question of order. That is, the order in which various OSes or applications show your disks and why it may impact whether you get ERROR 22 when you boot from GRUB.

In my experience, Windows XP (specifically the Windows Disk Manager) and Ubuntu (excluding GRUB) show the disk order based on the mainboard channels rather than on the BIOS Boot Order settings. The order that the disks are shown generally follow:

PATA channels       1 .. n
SATA channels       1 .. n 

So, in that regard, the Linux partitioner during installation is showing your HDD ordering the way I would expect them to appear. Whether a Windows GUI partitioner (Acronis or Symantec) honors that "standard" or whether they show Disk Order = Boot Order (as your screenshot suggests) is a completely different matter. Are you sure that Windows Disk Manager shows it the same way as the Symantec Partitioner? I suspect it doesn't, and I actually consider the Symantec screenshot to be the odd-man-out. Could you re-check that and post back, just out of curiosity? 

To give you concrete examples, here is what my 3-drive system shows in BIOS (various sections), Windows Disk Manager, Ubuntu installation (expert) partitioner, and device.map, along with the mainboard specs:

***** Mainboard Channels** 

Primary   IDE - Maxtor PATA HDD (master) / (no slave)
Secondary IDE - CDRW (master) / DVDRW (slave)
SATA 1        - WD Raptor SATA HDD 
SATA 2        - Samsung   SATA HDD
SATA RAID 1 - 4 - Unused

***** Windows Disk Manager**

Disk 0 - Maxtor PATA HDD
Disk 1 - WD Raptor SATA HDD
Disk 2 - Samsung SATA HDD

***** Ubuntu / Linux Install Partitioner (expert mode)**

IDE1 - /dev/hda (Maxtor PATA HDD) 
SCSI1 - /dev/sda (WD Raptor SATA HDD)
SCSI2 - /dev/sdb (Samsung SATA HDD)

***** Ubuntu /boot/grub/device.map**

(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb

***** BIOS - Device Identification / Summary**

Primary IDE Master - Maxtor HDD
Primary IDE Slave  - Not Detected
Secondary IDE Master - CDRW
Secondary IDE SLave -  DVDRW
Third IDE MASTER - WD Raptor
Fourth IDE MASTER - Samsung

**BIOS Boot - Boot Device Priority (User Setting)**

1st Device    1.44 Floppy
2nd Device    DVDRW Rom
3rd Device    WD Raptor SATA

**BIOS Boot - Hard Disk Drives (User Setting)** 
1st Disk  - WD Raptor SATA
2nd Disk  - Samsung SATA
3rd Disk  - Maxtor PATA

**BIOS Boot - CDROM Drives (User Setting)**

1st Drive - DVDRW
2nd Drive - CDRW

So, as you can see from the above info, the BIOS Device Summary, Windows Disk Manager, the Linux installation partitioner and /boot/grub/device.map show my drives exactly according to the way they are plugged into the motherboard ordered by type (PATA first, SATA second) / channel number (all the sections above that match each other are marked with '***"). 

The other BIOS items I show (without the 3 asterisks) are set by the user for boot priority purposes; these priorities are not reflected in Windows Disk Manager, the Linux partitioner, or device.map, but they seem to be used by GRUB (and why not ... GRUB is a boot manager, isn't it?)

**Now for the conclusion / theory**:

If GRUB used motherboard channel ordering (e.g., like the installation partitioner), it would see my HDDs like this:

```

hda = hd0 (Maxtor PATA)
sda = hd1 (WD Raptor SATA)
sdb = hd2 (Samsung SATA - bootloader installed here on /dev/sdb11) 

```

Doesn't that look familiar? Yes, it looks just like my device.map. And, most importantly, if GRUB saw the drives like that, I wouldn't get an ERROR 22 nor would I have to manually edit GRUB / menu.lst

However, it seems that GRUB actually sees the HDDs based on BIOS boot order (again, why not?) like this:

```

sda = hd0 (WD Raptor SATA)
sdb = hd1 (Samsung SATA - bootloader installed here on /dev/sdb11)
hda = hd2 (Maxtor PATA)

```

Now, that also looks familiar. This sequence corresponds to how GRUB / menu.lst needs to be edited by me (hd2,10 must be changed to hd1,10) in order for Ubuntu to properly boot.

So, my theory is that Ubuntu is using a scan of the motherboard channel ordering to derive device.map and also to derive the entries in the automatically generated menu.lst. However, GRUB needs its entries derived from the BIOS HDD Boot Order (note: the /dev/xxx entries are correct because they are "absolute").

Why does this not affect everyone? Not sure. But it does seem that if you leave your BIOS Boot Order the same as the mainboard device channel order, you won't experience this. If BIOS HDD Boot Order is rearranged and differs from the channel ordering, then this will occur.

Why does Ubuntu create its entries in GRUB using the mainboard channel ordering instead of BIOS HDD Boot Order? No telling.


Anyway, I'm open for any and all corrections.

Thanks.

---

### Post by joeindo on 2007-03-05
SuSUntu,

Thanks kindly for the replies. I have spent a little time researching this issue an it appears that you are correct about how Ubuntu "see's" drives. It apparently does not rely on what BIOS tells it and therefore creates it's own device map - which to me seems to be nothing more than a "hunch" at what drives exist and in what order they exist...

What also puzzles me is how the BIOS seems to be somewhat disregarded by grub and by that I mean that regardless of the boot order or drive order that I have specified in BIOS - grub seems to do it's own thing ?

Here is a screenshot taken with Gparted running on feisty live cd of my drives:
[IMG]http://farm1.static.flickr.com/93/412078712_1abcd0635f.jpg[/IMG] 

Device hdb2 is where root and grub where installed, Here is a copy of my device.map:
(hd0)	/dev/hdb
(hd1)	/dev/sda
(hd2)	/dev/sdb

And here is what menu.lst looked like before I edited it:
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

If I want my Ubuntu install to boot I change menu.lst to read:
title		Ubuntu, kernel 2.6.15-23-386
root		**[COLOR="Red"](hd2,1)[/COLOR]**
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot



According to several sources: "GRUB does not have access to the boot sequence information in the BIOS."  [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html#sec:grub.map](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html#sec:grub.map)
and: "The reason why the grub shell gives you the device map file is that it cannot guess the map between BIOS drives and OS devices correctly in some environments. " 
[http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html)

For some reason I was always under the impression that toggling the setting in BIOS "Plug and play OS" would impact the install process and assumed that in turn would impact Grub as well but? Maybe it doesn't? I am going to continue to research and experiment this issue further... I may even try playing/researching with LILO...but then there is the whole limiting factor with Lilo...

---

### Post by joeindo on 2007-03-05
SuSUntu,

I stand corrected - Yes, windows disk manager does show a different order than the symantec partitioner. I was also not correct in stating that grub disregards bios as it is labling the drives per the drive order setting that I suggested in Bios. Grub is labling the disks *exactly* that way.

---

### Post by confused57 on 2007-03-05
> **joeindo said:**
> SuSUntu,

I stand corrected - Yes, windows disk manager does show a different order than the symantec partitioner. I was also not correct in stating that grub disregards bios as it is labling the drives per the drive order setting that I suggested in Bios. Grub is labling the disks *exactly* that way.
I've "attempted" to help people with muliple drives corrrect their Linux booting problems and it's been my experience that grub does set up the device.map according to the hard drive boot sequence in bios...I was skeptical when I read the first link you gave, it could be that was written for older versions of grub(I don't know for sure).  I wasn't sure it was a hard-and-fast rule, but it had been my experience & observations from assisting other people.

---

### Post by SuSUntu on 2007-03-05
> **joeindo said:**
> SuSUntu,

I stand corrected - Yes, windows disk manager does show a different order than the symantec partitioner. 

Thank you for clearing that up. I thought that is what you would find. 

> **joeindo said:**
> 
I was also not correct in stating that grub disregards bios as it is labling the drives per the drive order setting that I suggested in Bios. Grub is labling the disks *exactly* that way.

I would not go so far as to say you were incorrect (or that I was :) ). I think we can only conclude, based on experience and *especially on official documentation*, that **it just depends** ... (see my comment to Confused57 below).

Thanks for sticking with the topic and continuing to add to it.

---

### Post by SuSUntu on 2007-03-05
> **confused57 said:**
> I've "attempted" to help people with muliple drives corrrect their Linux booting problems and it's been my experience that grub does set up the device.map according to the hard drive boot sequence in bios...


> **confused57 said:**
> 
I was skeptical when I read the first link you gave, it could be that was written for older versions of grub(I don't know for sure).  I wasn't sure it was a hard-and-fast rule, but it had been my experience & observations from assisting other people.

The GRUB document that JoeIndo linked to is for the latest version (GNU GRUB Manual 0.97):

[http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html)

> 
The reason why the grub shell gives you the device map file is that it cannot guess the map between BIOS drives and OS devices correctly in some environments. For example, if you exchange the boot sequence between IDE and SCSI in your BIOS, it gets the order wrong.

Thus, edit the file if the grub shell makes a mistake. You can put any comments in the file if needed, as the grub shell assumes that a line is just a comment if the first character is `#'.


I'm running Edgy on the machine I discussed in this thread and the file:

```

/boot/grub/installed-version

```

shows **0.97-11ubuntu14**.

The SUSE link that JoeIndo provided was a little stale (it was for v9.1), but still relevant. However, in the interest of providing up-to-date information, I'll submit this link to the SUSE 10.2 manual which leaves the comments about GRUB and device.map essentially unchanged from the content in the 9.1 manual:

[http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html#sec:grub.map](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html#sec:grub.map)

> 
GRUB does not have access to the boot sequence information in the BIOS. If your system contains both IDE and SCSI hard disks, GRUB must try to determine the boot sequence by means of a special procedure. It saves the results of this check to the file /boot/grub/device.map ...

As the order of IDE, SCSI, and other hard disks depends on various factors and Linux is not able to identify the mapping, the sequence in the file device.map can be set manually ...


[http://www.novell.com/documentation/opensuse102/index.html?page=/documentation/opensuse102/opensuse102_reference/data/sec_grub_basic.html](http://www.novell.com/documentation/opensuse102/index.html?page=/documentation/opensuse102/opensuse102_reference/data/sec_grub_basic.html)

14.2.2 The File device.map

The file device.map maps GRUB and BIOS device names to Linux device names. In a mixed system containing IDE and SCSI hard disks, GRUB must try to determine the boot sequence by a special procedure, because GRUB may not have access to the BIOS information on the boot sequence. GRUB saves the result of this analysis in the file /boot/grub/device.map. For a system on which the boot sequence in the BIOS is set to IDE before SCSI, the file device.map could appear as follows:

(fd0)  /dev/fd0
(hd0)  /dev/hda
(hd1)  /dev/sda
   

Because the order of IDE, SCSI, and other hard disks depends on various factors and Linux is not able to identify the mapping, the sequence in the file device.map can be set manually. If you encounter problems when booting, check if the sequence in this file corresponds to the sequence in the BIOS and use the GRUB prompt to modify it temporarily if necessary. After the Linux system has booted, the file device.map can be edited permanently with the YaST boot loader module or an editor of your choice.


---

### Post by confused57 on 2007-03-05
> I would not go so far as to say you were incorrect (or that I was  ). I think we can only conclude, based on experience and especially on official documentation, is that it just depends ... (see my comment to Confused57 below).

Thanks for sticking with the topic and continuing to add to it.

I appreciate the time and effort you guys put into describing your experiences and conclusions in this thread...it was good reading.   I would agree that it "just depends" on the system setups and I wouldn't conclude anyone was incorrect.  I hope I wasn't intruding by replying, but I had "gathered" from my experiences, that grub sets up the device.map at install based on the bios hard drive boot sequence.  I wouldn't state this is true for each and every install on different hardware configurations, but as a "general" rule this seems to be the case.

Added:  Just read your reply, grub does ocassionally make mistakes in "guessing" hard drive configurations...I think it would be unrealistic to expect grub to be 100% accurate on each and every configuration & hardware, especially with newer chipsets(SATA promise controllers come to mind)...thanks again, I learned a lot reading the info both of you provided in this thread.

---

### Post by SuSUntu on 2007-03-06
> **confused57 said:**
> I appreciate the time and effort you guys put into describing your experiences and conclusions in this thread...it was good reading.   I would agree that it "just depends" on the system setups and I wouldn't conclude anyone was incorrect.  I hope I wasn't intruding by replying, but I had "gathered" from my experiences, that grub sets up the device.map at install based on the bios hard drive boot sequence.  I wouldn't state this is true for each and every install on different hardware configurations, but as a "general" rule this seems to be the case.

I'm happy to have your posts here. :)

It's been several days since anyone replied, and I've been checking back everyday to see if anything new has been added. It's a subject that I've had to deal with for a while as I noted, and  it is interesting to see how other people's experiences compare.

---

