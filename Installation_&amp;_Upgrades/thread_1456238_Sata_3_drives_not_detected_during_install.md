---
title: "Sata 3 drives not detected during install"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by jazee on 2010-04-16
So I'm trying to install 10.04b2 x64 on my new rig and for some reason the live cd can't detect both of my 1TB Sata 3 drives. There is no Raid and the bios has them flagged as IDE. I have also tried adding pci=nomsi to the boot string to no avail. Does anyone have any idea on how to get this to work?

---

### Post by Alfagulf on 2010-04-17
Hello Jazee,

I have similar problem here,
The hardware I am using is a Gigabye X58A-UD3R motherboard and a Seagate SATA3 HD connected to one of the two SATA3 sockets on the motherboard.
The installation of UBUNTU 9.10 reaches the stage where is says no disk was detected.

I have two theories here:
1. that the HD has to be plunged in the other SATA3 socket.
2. I nstalled win7 x64 on this PC before, and I remeber several years ago, similar thing happened to me and UBUNTU could not recognize the HD that had Windows previously installed on it. I had to use a utility to rid the HD from all partitions and clear all MBRs.

Please let me know your setup and if you had windows previously on you hard disk.

May be we can help each other.

Thanks

---

### Post by Alfagulf on 2010-04-18
Update:

I tried the other SATA3 socket with no avail!
I then plugged the drive into one of the SATA2 sockets and it was immediately recognized.

I decided to continue UBUNTU 10.04 Beta2 installation, on the hope that I might find later a driver that can work with my gigabyte SATA3 Marvell  SE9128 controller.
Gigabyte web site does not have any drivers for Linux, instead the refer us to the chipset manufactured for such driver. I looked at Marvell web site but could not find any drivers for UBUNTU !!

It would be nice if some one could share his experience with us regarding this type of setup.

Thanks

---

### Post by Alfagulf on 2010-04-25
[Solved]

I read some where in another post that I need to change the BIOS Hard disk mode from IDE to AHCI!
Sure enough, I did the change and after saving the BIOS and rebooting, the system rebooted TWICE and then booted my ubuntu lucid OS.:)

Now I need to do some speed test to see if SATA3 controller and hard disk makes a difference!
Here is the result:
When connecting the HD to the SATA2 port:
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   18796 MB in  2.00 seconds = 9407.90 MB/sec
 Timing buffered disk reads:  416 MB in  3.01 seconds = 138.19 MB/sec


When connecting the HD to the SATA3 port:
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   18744 MB in  2.00 seconds = 9381.51 MB/sec
 Timing buffered disk reads:  416 MB in  3.01 seconds = 138.27 MB/sec



Hmm, Interesting!! there is no difference!!! :(

Does anybody know why?

---

### Post by jazee on 2010-04-27
Thanks for the solution. I thought I had tried that but that may have been only to switch it to IDE from Raid/SATA. Going to try this tonight. I'd imagine it should considering I'm using relatively the same MB GA-X58A-UD7.

And anything you find on the speed issue I'd like to hear about it.

---

### Post by Alfagulf on 2010-04-28
Looking at this review:
[http://www.testfreaks.com/blog/review/review-of-seagate-2tb-barracuda-xt-sata6-desktop-hard-drive-st32000641as/](http://www.testfreaks.com/blog/review/review-of-seagate-2tb-barracuda-xt-sata6-desktop-hard-drive-st32000641as/)

It looks like we should not expect much out of SATA3 when using a mechanical HD !!! :(

I guess I have to settle with this, not so bad, of a speed!

---

### Post by jazee on 2010-04-28
So switching from IDE to ACHI worked. However had to switch all 3 of the SATA Controllers to ACHI to get it to work. Just switching the Sata3 Controller didn't work. Thanks again for finding that out.

---

### Post by wavieira on 2011-04-29
THis is awesome news.  I still have one problem however.  I have another unnamed OS :confused:, with quite a bit of data on the drives.  Changing the BIOS setting causes that OS not to work.  Is there any way to get ubuntu to see them as IDE drives?
 
 
> **Alfagulf said:**
> [Solved]
 
I read some where in another post that I need to change the BIOS Hard disk mode from IDE to AHCI!
Sure enough, I did the change and after saving the BIOS and rebooting, the system rebooted TWICE and then booted my ubuntu lucid OS.:)
 
Now I need to do some speed test to see if SATA3 controller and hard disk makes a difference!
Here is the result:
When connecting the HD to the SATA2 port:
$ sudo hdparm -Tt /dev/sda
 
/dev/sda:
Timing cached reads: 18796 MB in 2.00 seconds = 9407.90 MB/sec
Timing buffered disk reads: 416 MB in 3.01 seconds = 138.19 MB/sec
 
 
When connecting the HD to the SATA3 port:
$ sudo hdparm -Tt /dev/sda
 
/dev/sda:
Timing cached reads: 18744 MB in 2.00 seconds = 9381.51 MB/sec
Timing buffered disk reads: 416 MB in 3.01 seconds = 138.27 MB/sec
 
 
 
Hmm, Interesting!! there is no difference!!! :(
 
Does anybody know why?

---

### Post by icarus128 on 2011-07-01
> **wavieira said:**
> THis is awesome news.  I still have one problem however.  I have another unnamed OS :confused:, with quite a bit of data on the drives.  Changing the BIOS setting causes that OS not to work.  Is there any way to get ubuntu to see them as IDE drives?

This windows Fix It worked for me. (That is, it made the unamed OS work in the presence of AHCI drives so Linux would also work)

[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

---

