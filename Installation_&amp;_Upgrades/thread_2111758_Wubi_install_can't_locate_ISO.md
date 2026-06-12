---
title: "Wubi install can't locate ISO"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by Erebus04 on 2013-02-02
Hi,

This is my first time installing ubuntu, so obviously I'm a tad lost. When I try to install ubuntu 12.10 via the Windows installer, on the first reboot it tells me that it can't locate 'installation.iso' and tells me to run 'chkdsk /r' as a possible solution. I tried that to no avail. I've also tried downloading the iso beforehand and directing  wubi to it's location as per the instructions here: [http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478](http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478)

It doesn't even attempt to install after rebooting with that method.

Any suggestions as to how to proceed?

Thanks.

---

### Post by Frogs Hair on 2013-02-02
Are you running 7 or 8 ?  Wubi and Win 8 is new territory 

Wubi .exe should be run as administrator and down loads the iso to the root disk/folder inside the Windows partition.

You can also place the iso of a Wubi supported version of Ubuntu in a folder in downloads with Wubi and it will install from the folder. The methods are covered pretty well at link.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Erebus04 on 2013-02-02
I'm running 7. It also failed when I tried running it as administrator, saying that it "gave up waiting on the boot device" after restarting. I also tried installing from a live CD, but Ubuntu isn't able to detect any of my drives.

---

### Post by bcbc on 2013-02-02
> **Erebus04 said:**
> I'm running 7. It also failed when I tried running it as administrator, saying that it "gave up waiting on the boot device" after restarting. I also tried installing from a live CD, but Ubuntu isn't able to detect any of my drives.
If the live CD can't detect your drives then neither will Wubi. Wubi is the same as Ubuntu (except for the initial install part that runs in Windows. Which explains why it doesn't work.

Do you have some sort of raid setup? Encrypted disk? Boot a live CD and run the  [bootinfoscript]("http://bootinfoscript.sourceforge.net/") - that might provide some info.

---

### Post by NobleYorkshire on 2013-02-02
> **Frogs Hair said:**
> Are you running 7 or 8 ?  Wubi and Win 8 is new territory 

Wubi .exe should be run as administrator and down loads the iso to the root disk/folder inside the Windows partition.

You can also place the iso of a Wubi supported version of Ubuntu in a folder in downloads with Wubi and it will install from the folder. The methods are covered pretty well at link.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I had the same issue.  But I was not running as administrator.

Thank you for solving this problem for me!  Going to retry getting Kubuntu through Wubi now!

---

### Post by Erebus04 on 2013-02-03
I don't have any raid setup or encrypted disks. I've got a HDD(storage only) and a SSD that has the windows partition and an empty partition where I want to put Ubuntu.

Results of the boot info script:

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sr0                                                iso9660    Ubuntu 12.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

  No volume groups found

---

### Post by bcbc on 2013-02-03
Can you list your hardware specs... It's a bit odd that none of your drives are detected at all.

But I reckon it's got to be down to unsupported hardware? (guessing, but can't think what else would do this)

---

### Post by Erebus04 on 2013-02-03
Mobo: ASRock H61M/U3S3 LGA 1155 Intel H61 SATA 

RAM:G.Skill Sniper 8GB(2 X 4) 240 pin DDR3

GPU: GeForce GTX 560 Ti

CPU: Intel i5-2400 3.1 GHz Quad-core

HDD: Western Digital WD Blue WD50000AAKX 500GB SATA

SSD:Intel SSDSC2CW120A 128GB

Wasn't sure what all you wanted, so I just posted whatever I thought could be relevant. Let me know if more is needed.

---

### Post by bcbc on 2013-02-03
I found this post without much resolution, but it seems similar. Intel smart technology? Don't know if this applies. If this doesn't help maybe comment on the post and see if they had any response... 
[http://askubuntu.com/questions/164980/no-hdd-shows-up-during-install-12-04-on-lenovo-u410]("http://askubuntu.com/q/164980/14916")

---

### Post by Erebus04 on 2013-02-03
Hmmm. I don't have a RAID setup and I shouldn't have Intel Smart Tech set up. I couldn't find anything related to it on my computer. So unless it comes pre-set up and hidden I don't think I have that either. Thanks for the help though. Back to searching the forums for me.

---

