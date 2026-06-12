---
title: "Dell Dimension 4700, IDE device not recognized"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by lbthrice on 2007-03-31
Hi all,

Please help the newbie (me) escape the clutches of that other OS....

I have no clue at all what the heck is happening with my Dell Dimension 4700...I cannot boot from the CD despite upgrading chipset drivers and BIOS to the current A10 version.  

I also changed my BIOS settings: 
switched the SATA Drive Operation from normal to compatible, 
set my LPT port mode to ECP, 
changed DMA from off to DMA1, 
most importantly I altered the boot sequence to make the SATA drive last on the list.  

My drives:

Diskette Drive: USB=OFF
Drive 0: SATA-0=ON    <----My Hard Drive
Drive 1: SATA-2=OFF
Drive 2: PATA-0=ON    <----DVD-ROM (PRI IDE MASTER)
Drive 3: PATA-1=ON    <----CD-RW     (PRI IDE SLAVE)

So here is what happens:

I place the bootable disk in the CD-RW drive (and I am certain that it is a bootable disk because I used it to install Kubuntu on my laptop last week) and the computer progresses past the Dell logo screen.   The screen goes to normal dell boot screen.  A moment of hope: I can see and hear the CD drive spinning.  Then FAILURE the loathsome OS that Michael Dell installed at the factory loads.

One thing that is perhaps worth noting:

 is that after I changed my BIOS settings as I described above...that other OS declared "new hardware found".  It then identified the "new hardware" as the DVD and CD drive.  I have been using the computer with that OS for a couple years with full function of the CD and DVD drives....therefore the drives seem to have been recognized in some novel fashion.  Also worth noting: the drives still work after BIOS changes when I use them under that other OS.  

I've been Googling all day to no avail...any ideas?

Cheers

---

### Post by confused57 on 2007-03-31
Have you tried pressing "F12" during bootup of your Dell?  That's what I have to press on my Dell Dimension 4550 to boot from the cd drive.

---

### Post by lbthrice on 2007-03-31
Yes, I have tried F12 that but when I attempt to select the CD-ROM boot option the boot attempt fails almost immediately and gives a message that the drive is unavailable.

---

### Post by confused57 on 2007-03-31
> **lbthrice said:**
> Yes, I have tried F12 that but when I attempt to select the CD-ROM boot option the boot attempt fails almost immediately and gives a message that the drive is unavailable.
I also have 2 cd drives, master is a cd-rom & slave is a DVD+RW drive...the cdr-rom boot option in the F12 menu boots to the cd-rom master drive.  I don't know if you can or not, but wonder if switching the positions of your cd drives will make a difference.

Added: Maybe just temporarily connecting your cd drive to the master controller will work, I'm just guessing here.

---

### Post by lbthrice on 2007-03-31
I will attempt it, sounds logical to me....thanks!

I am presently on hold with Dell :-\" 

I'll post results asap

---

### Post by lbthrice on 2007-04-01
Right, thank you for the guidance...my System Restore cd booted and my drive is partitioned! 

After reading your post I said to myself: "self, why not try putting the bootable CD-RW disc in the DVD-rom drive and see what happens"
So I terminated the call to Dell (I was lamenting in hold world for quite a while...but I did get to speak with a representative overseas and one in the southern US all within the span of 10 min.)
Sure enough...it worked.
Should have known the DVD drive could read the CD-RW disc!  It was quite a treat.
I predict that your solution would have worked.

I wonder what it is about the PATA controller and the BIOS that does not allow for the Primary IDE slave to boot?  

Kubuntu is now going on my machine thank you!! \\:D/

---

### Post by confused57 on 2007-04-01
> **lbthrice said:**
> Right, thank you for the guidance...my System Restore cd booted and my drive is partitioned! 

After reading your post I said to myself: "self, why not try putting the bootable CD-RW disc in the DVD-rom drive and see what happens"
So I terminated the call to Dell (I was lamenting in hold world for quite a while...but I did get to speak with a representative overseas and one in the southern US all within the span of 10 min.)
Sure enough...it worked.
Should have known the DVD drive could read the CD-RW disc!  It was quite a treat.
I predict that your solution would have worked.

I wonder what it is about the PATA controller and the BIOS that does not allow for the Primary IDE slave to boot?  

Kubuntu is now going on my machine thank you!! \\:D/

Glad to hear it worked...I knew selecting boot from cd drive after pressing F12 booted my cd-rom drive connected as master, but I wasn't sure if a cd would boot from a DVD-ROM drive.

It's just the way Dell bios is configured, I can only boot first to my master hard drive on IDE#1 so I guess it also applies to the master cd drive on my IDE#2 controller.  Don't know about Dell's configuration with SATA controllers & booting.

---

### Post by lbthrice on 2007-04-01
Um, so, I used the linux sysrestore live cd and the gparted program contained therein to partion my drive...everything went along swimmingly. 

Then I rebooted into the other OS...everything is dandy....it even sees the new partions and everything.

Then I boot from the Kubuntu live CD and it is cranking and everything is dandy UNTIL I get to the partion manager that is invoked during the ubiquity GUI-type install and I get 

"no device found, maybey you are not logged on as root"

uh oh :neutral: 

I try an
# fdisk -l
and there is no response, just a fresh prompt.

You didn't happen to encounter this sort of thing did you?

---

### Post by lbthrice on 2007-04-01
Oh yeah....here is the lspci .... it is somewhat encouraging I think looks like it sees my SATA controller and has no error ... hmmmmm 

```
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Cont
roller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express
Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US
B UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) 
LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) 
SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) 
SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [RadeonX300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 
[Radeon X300SE]
03:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
03:01.0 Modem: Intel Corporation FA82537EP 
56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE 
(LOM) Ethernet Controller (rev 03)
```

---

### Post by confused57 on 2007-04-01
Try booting up the live cd, open a terminal(Applications---Accessories---Terminal), enter(or copy & paste):
```
sudo fdisk -l
```
the -l is a small "L"

I'm not sure about your error message, if it might be this bug or not:
[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)
this bug in the ubiquity installer gives the error that no root partition was assigned.

installing Kubuntu, you might need to use "gksudo kwrite..." instead of "gksudo gedit..."

Added:  or with Kubuntu, maybe "kdesu kwrite..."

---

### Post by lbthrice on 2007-04-01
yep it liked "kdesu kwrite /so-on/so-forth" BUT editing the validation file didn't fix it

additionally...

```
sudo fdisk -l 
```

lists nothing...all I get is a fresh prompt

Kubuntu...so close...yet so far away :(

I can almost taste it for goodness grace

---

### Post by confused57 on 2007-04-01
> **lbthrice said:**
> yep it liked "kdesu kwrite /so-on/so-forth" BUT editing the validation file didn't fix it

additionally...

```
sudo fdisk -l 
```

lists nothing...all I get is a fresh prompt

Kubuntu...so close...yet so far away :(

I can almost taste it for goodness grace

The live cd must have recognized your hard drive when you first repartitioned your hard drive, I'm not sure what's going on.
Maybe you can just try rebooting the live cd...you did use -L instead of -one for the command "sudo fdisk -l"...of course, if the live cd didn't recognize your hard drive, it wouldn't return any results.

If rebooting doesn't help, you might want to boot into your other OS and burn a copy of the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
it's a great partitioning tool and it would be interesting if it's able to detect your SATA drive.

I have to get some sleep for now, it's getting rather late, but I'll check back later on today & see if you've found a solution, possibly from someone else...good luck.

---

### Post by lbthrice on 2007-04-01
HEy, I'm posting this reply from within my new Kubuntu HD install!  This distro (Edgy) is amazing...all my hardware was detected and works great so far.

The way that I fixed the partion manager hard drive recognition issue was to change the "SATA Operation" value in the Bios back to "Normal".

I think that changing it to "Compatible" in the first place was unnecessary.
(Recall that I changed it in an effort to make the BIOS recognize my Primary IDE slave as bootable when I was trying to use the live CD...then solved the problem instead by using the dvd-rom (the primary IDE Master) to read the cd-rw install disk)

Anyway...After I changed the BIOs the Partion Manager recognized my sda. (yipee confetti parade)

I did have a couple problems afterwards though:

Next I attempted to HD install by invoking the ubiquity installer provided on the desktop....but I kept getting error messages from the GUI partion manager that is used in the ubiquity installer.  To be completely honest, I am not exactly sure how I fixed it.

Here is a brief recap:
I started the Ubiquity installer and when the partion manager showed my HD partition scheme it was accurate; the ubiquity partition manager recognized everything I had done previously with GParted.  

However after selecting my root and swap mount points the partition manager performed a filescan prior to reformatting and mounting the swap and root target partitions.

The manager reported "unresolved errors" in the Dell utility (FAT16) partition, as well as in both linux partitions that I had formated with gparted (a 10 G primary ext3, a 2 G ext3 extended (for my swap) and a 10 G FAT32 extended (for shared space between the two OSs).

It gave me the choice to proceed and leave the partitions "as is" so I chose that option HOWEVER it didn't progress to formatting stage of the process...it just gave an error message and aborted.

Therefore, next time when I entered the installer I reformatted the Primary ext3 and exteneded swap partions prior to selecting them as mount points.

When I tried to progress through the install this time the same thing happened as before (unresolved errors detected, ubiquity aborts)

So being the glutton for punishment that I am...I tried ubiquity one more time before downloading and buring the alternative install iso...

Wonder of wonders: I started ubiquity...selected my mount points (and checked the "reformat boxes next to the swap and primary partitions) and it worked!  The partition manager only complained about the FAT16 Dell utility partion during the scan this time.

So there you have it....
Sorry about the sloppy explanation of the whole thing; I can't be sure exactly what I did to make the install follow through to completion.

The important thing is that I have Kubuntu running on my desktop now!

Thank you for all your help Confused!!  You rock! Cue rock and roll smiley :guitar:

---

### Post by confused57 on 2007-04-01
Job well done, glad you got it working...at least I helped you get your Kubuntu install cd booted.
You know your system better than anyone trying to help you and what changes you may have made, for example something had to have changed from the time you  pre-partitioned your hard drive and the time you tried to install(for the installer not to recognize the hd)...great job of troubleshooting.  I usually just format my partitions when I'm installing, rather than pre-formatiting...the installer was probably complaining about setting a mountpoint for the FAT16 utility partition, don't believe it'll be a problem.  You can probably do a "sudo fdisk -l" now and see what your partition table looks like.  
I know you'll enjoy your experience with Kubuntu...for me, it's been fun and I've learned a lot as well.  See you around in the forums.

---

