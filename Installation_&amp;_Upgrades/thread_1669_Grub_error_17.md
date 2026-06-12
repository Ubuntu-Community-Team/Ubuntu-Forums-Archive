---
title: "Grub error 17"
date: 2004-10-22
forum: Installation &amp; Upgrades
---

### Post by ignitionworks on 2004-10-22
On my dual celeron 533Mhz with 10GB box, I get Grub error 17 (don't remember the complete error). There is no other operation system other than  ububtu. I created 2 partitions

hda1 512MB swap
hda2 9.7GB  /     ReiserFS

Everything installed ok but on the first reboot, grub gives Error 17.

 On another machine (PII 400Mhz, 20GB) with the following partitions
hda1 4GB Win NT 4.0
hda2 512MB swap
hda3  15.5GB /    ReiserFS 

Ubuntu works like a charm.

Is it just me or Ubuntu SMP and grub issue? Anyone else had similar problems?

IgnitionWorks

---

### Post by rolf on 2004-10-22
[quote=ignitionworks]On my dual celeron 533Mhz with 10GB box, I get Grub error 17 (don't remember the complete error). There is no other operation system other than  ububtu. I created 2 partitions

hda1 512MB swap
hda2 9.7GB  /     ReiserFS

Everything installed ok but on the first reboot, grub gives Error 17.[/quote]

Error 17 indicates GRUB can't id the partition type. Check [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) for more info.  Here is the relevant entry:
"17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

HTH.

---

### Post by thegeekster on 2005-03-04
Hi,

Sorry for the rather late reply, but I just joined the forum here........ ;)

I also received error 17 when trying to boot from the Warty LiveCD.........

However, I found this to be a problem with the device I was booting the CD from (NEC ND-3520A DVD_RW IDE writer), since I was able to boot from my CD writer (Samsung SW-248F CD-R/RW).........

I also submitted this in a _[bug report](https://bugzilla.ubuntu.com/show_bug.cgi?id=7178)_......

---thegeekster

---

### Post by thegeekster on 2005-03-04
PS: And to Matt Zimmerman - Thanx for the very fast, 10-minute reply to the bug report I submitted....... :D

---

### Post by Jerklaren on 2005-04-25
How do you actually solve this problem? I'm a total noob.

This is my hard drive constellation:

hda 1*NTFS
sda 2*NTFS (Win XP installation)
sdb 2*NTFS

During the installaion, I empty the first partition on sdb and let the installation program configurate it automatically. I end up with one partition of about 40 GB ext3 (partition 1), and one of about 1 GB being the swap thingie (partition 5, though it comes just after the first partition. Why is this?). I also choose to install Grub at /dev/sdb.

Still, booting the system from that hard drive gives me error 17. What can I do?

It says:

root (h2,0)
Filesystem type unknown, partition type 0x7
....the boot directory.... Error 17: cannot mount the selected partition.


What's hd2? I have a hard drive on hd0, and a CD recorder on, I guess, hd1 (slave to the hda hard drive)

---

### Post by Digitallysick on 2005-04-27
I had the same problem, make sure in your bios, that its not set on auto, that it has your harddrive listed instead of auto, my problem was i have a 200 gig HD, but my pentium only sees it as a 136 gig hd,  once xp boots, it sees the other part of the hard drive, i was trying to format that part,  finally i realized its a windows only thing, and to go by my bios, so now all is well

---

### Post by Jerklaren on 2005-04-27
No, that's not my problem. I boot from the linux drive, and the drive is only 120 GB in total. Thanks anyway.

ANyone else?  :|

---

### Post by sirwally on 2005-05-02
Jerklaren, I see that you are booting off of /dev/sdb (and /dev/sda for Windows).  Is that an actual SCSI drive, or is it a USB or FireWire drive?  I just ran into this same problem on my notebook, but it was fine earlier.  I rebooted a few times, reinstalled grub twice, then I unplugged my USB drive (/dev/sda) and rebooted.  It worked!  Very odd.  I bet any money that if I plug my USB drive back in and reboot, it will continue to work (until the next time the USB drive gets borked and requires a hard reset ;-)

---

### Post by Jerklaren on 2005-05-05
They are actually sata drives. Do you think that could cause a problem as well?

---

### Post by resiak on 2007-02-24
I recently removed my ubuntu partition from my main hard drive, and I plan on reinstalling it on my slave drive. However, after I turned off my computer after formatting my Linux partition, it comes up with GRUB Error 17. Where do I go in BIOS to change it to only boot windows?

[email]darkresiak@gmail.com[/email] is my email, please email me with any suggestions.

I appretiate it greatly.

---

### Post by dusty_z on 2007-06-20
i have the exact same problem.

i am able to get into fixboot using the windows xp cd but when i change the settings and restart the same error comes up. 

contact me with answers :D [email]dusty_z@hotmail.com[/email]

---

### Post by andymadonna on 2007-07-09
I have the same problem as dusty_z , and resiak. I deleted my ubuntu partition and now I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Now I cant boot into windows, I dont really even know what GRUB is.

Please help me!!!!!!:(:(:(:(

---

### Post by Pumalite on 2007-07-09
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by andymadonna on 2007-07-09
Thank you Pumalite

I understand I must edit the menu.1st or grub.conf

but how do I actually get to and edit these files?

---

### Post by Pumalite on 2007-07-09
gksudo gedit  /boot/grub/menu.lst ( l is lower case L)

First backup your file:

cp /boot/grub/menu.lst /boot/grub/menu.lst.back

---

### Post by andymadonna on 2007-07-09
But I can't get to linux I deleted the partition

---

### Post by andymadonna on 2007-07-09
I actually just did what this guy said and it worked!!!!  :):):):):):)

[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html#143450]("http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html#143450")

---

### Post by dn_desaku on 2007-07-28
Hello, I have been getting simillar problems however it seems to vary in someplaces.
I just went in the shallow end of the ubuntu pool and I am lost. :-({|=

I dual boot Windows Vista and Ubuntu together.

When GRUB loads the menu appears with all the items (3 ubuntu boot items and Windows).
Every time I try to load Ubuntu it gives me error 17. :(

When I loaded Vista and it worked. :)

But I wondered why Vista works and Ubuntu does not? :confused:

Thanks in advance and any and all help is appreciated. 

email: [email]davidnuongm@gmail.com[/email]

---

### Post by confused57 on 2007-07-28
> **dn_desaku said:**
> Hello, I have been getting simillar problems however it seems to vary in someplaces.
I just went in the shallow end of the ubuntu pool and I am lost. :-({|=

I dual boot Windows Vista and Ubuntu together.

When GRUB loads the menu appears with all the items (3 ubuntu boot items and Windows).
Every time I try to load Ubuntu it gives me error 17. :(

When I loaded Vista and it worked. :)

But I wondered why Vista works and Ubuntu does not? :confused:

Thanks in advance and any and all help is appreciated. 

email: [email]davidnuongm@gmail.com[/email]

I would recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb) and may be able to boot your Ubuntu, then you should be able to repair the booting problem

You could also boot the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

Here is a description of grub error 17 & possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by dn_desaku on 2007-09-18
Well, I just decided to reinstall Ubuntu. That solved it

---

