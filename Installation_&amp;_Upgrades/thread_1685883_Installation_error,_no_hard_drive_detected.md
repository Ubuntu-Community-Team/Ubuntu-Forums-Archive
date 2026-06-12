---
title: "Installation error, no hard drive detected"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by GAME2OVR on 2011-02-11
Hi,

After lot's of research i still can't find any solution to my problem, that's why i'm posting a message here.

So, it's been few days now that i'm trying to install ubuntu 10.10, with the live CD, but each time when i must choose where to install it or how to make partition, it just tell me there is no hard drive..

(i have two 1 TB sata hard drive )

So i tried many things, GParted doesn't find my hard drive either, they appear in the bios (i can run windows), try to uninstall a raid program that might hide the hard drive, but it didn't work either.

So i came to see that i had Marvell 9123 which seems to be a SATA controller, and few people seems to have some similar issue with that Marvell stuff..

I'm quite desperate now.. i tried to install ubuntu on a USB drive but my computer just doesn't boot on it (i tried this method for the sb drive [http://forum.ubuntu-fr.org/viewtopic.php?id=181665](http://forum.ubuntu-fr.org/viewtopic.php?id=181665) ,it's in french sorry..)

Sorry for my english, and thanks for your time =)

---

### Post by wahyu77 on 2011-02-11
turns out we have the same difficulty

---

### Post by RedSingularity on 2011-02-11
Interesting.  What does fdisk -l give you?  Does it show the drive as present?

---

### Post by GAME2OVR on 2011-02-11
nothing happen when i type this command, no result/empty result..
except when i plug my usb drive..

---

### Post by RedSingularity on 2011-02-11
> **GAME2OVR said:**
> nothing happen when i type this command, no result/empty result..
except when i plug my usb drive..

The hard drive is enabled in the BIOS correct?  And its sata so no need to worry about master/slave.  How about the connector on the motherboard?  Try changing to another connector.

---

### Post by GAME2OVR on 2011-02-12
I'll try it as soon as i'm home (this afternoon),
i saw during the start of the computer while in the black screen, the hard drive are detected as SATA before Marvell activate, after in the BIOS it says they are IDE..

So i'll repost after trying another connector (but's isn't it weird that it would work on some connector and not other?)

---

### Post by Quackers on 2011-02-12
At least one Marvell controller is not supported yet, but I think that's for sata3 drives.
Is your hard drive (or has it ever been) used as part of a raid array?
If so, you will need to remove the raid metadata with the command below, but beware that if raid0 is being used, you will lose your current operating systems!
```
sudo dmraid -rE /dev/sdX
```
where X is the designation of your hard drive - sda, sdb etc.

---

### Post by GAME2OVR on 2011-02-12
> **Quackers said:**
> 
Is your hard drive (or has it ever been) used as part of a raid array?

How do i know that? (i asked my father who installed it, he said no, but i'm not confident about is memory :O!)

---

### Post by Quackers on 2011-02-12
Go into your bios settings and see if any raid array is defined. It should be clearly marked in one of the bios screens.
Alternatively, and probably a better idea, is to boot from the live cd/usb and select "try ubuntu", then, when the desktop loads make sure you have an internet connection. Then go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by GAME2OVR on 2011-02-12
Here what you asked

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```

---

### Post by Quackers on 2011-02-12
Sorry for my absence.
Well, as the boot script output states, there is no valid partition table found.
That could mean a few different things.
Can you tell us exactly what has been done to the pc with regard to partitioning lately?

---

### Post by GAME2OVR on 2011-02-12
mmh i don't understand your question..

But i wanted to have one hard drive for windows, and the other for ubuntu..

So there is windows on the first one, and nothing on the other..

---

### Post by oldfred on 2011-02-12
The script did not even see the windows drive. 

Does BIOS see both? Are they plugged into the 6GB ports, if so try the 3GB/sec ports.

Some other BIOS type issues:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS

---

### Post by Quackers on 2011-02-12
A partition table error often occurs after creating/deleting or resizing partitions on a disc. If you have done none of these things recently, then I am at a loss to explain the invalid partition table.
Maybe somebody else can offer some advice for you.

I just remembered the Marvell controller. As I said earlier, there is at least one that is not supported, but, I believe that is a SATA3 controller.

---

### Post by GAME2OVR on 2011-02-12
The matter was that ubuntu did not see both of my hard drive, so i don't get the point where you cant to come..

"The script did not even see the windows drive. " 
As I said earlier few people are experiencing issue ( => no hard drive detected ) with marvell controler + linux

So there is no probleme with partitionning.. it's just ubuntu doesn't see hard drive, so it doesn't see partitions.. (i have no problem with partitionning on windows, on both hard drive)

Some other BIOS type issues:
BIOS settings need USB mouse & keyboard / ? no
BIOS in not updated to latest revision / yes
BIOS not set to boot CD or USB first / i tried many setup the probleme doesn't come from here
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs / i don't really know that kind of stuff, but i'll try other connector
Other BIOS settings - Security or locked down Boot sector, Bitlocker / i don't know that i'll will search
Disable Quickboot in BIOS / i'm going to try

---

### Post by JGSD on 2011-05-30
I had the same problem but it was partially solved when I changed the Marvell controller mode from "IDE Mode" to "ACHI Mode"

After this, Ubuntu detected the drives on the Marvell controller at starup and allowed installation to continue.

I still can't book Ubuntu from a drive on the Marvell controller, but it's a start :-)

---

