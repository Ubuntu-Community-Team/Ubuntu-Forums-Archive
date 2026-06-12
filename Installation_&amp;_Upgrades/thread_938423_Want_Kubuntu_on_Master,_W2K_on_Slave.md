---
title: "Want Kubuntu on Master, W2K on Slave"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Major Pain on 2008-10-04
I've been trying to find an answer to this for a long time.  I've found a lot of advice about installing the other way around, but as a noob, I need step-by-step instructions.

About 6 months ago, my W2K system blew up.  Knoppix couldn't fix it any more (it had done so about eight times before).  I installed Debian to my slave and started playing with it.  I really liked it.

Long story short, I installed Kubuntu on my 500 GB Master and I am very happy.  This *is* my primary OS and I don't want to change that.  *But* I found that I could use some things in W2K that I can't quite find for Kubuntu; (some system specific software).  I don't intend to use W2K very often.

So I want to install it to my Slave.  But when I put in the install disk and tell it do that, it tells me it needs to write some code to the Master (I assume the MBR) but that that drive has another system on it that can't be recognized.  It tells me to partition something on that drive first (there'as about 1024 MB of unpartitioned space right now on the Master; is this the MBR?)

I don't want to ruin my Kubuntu install and I want W2K on the Slave as a dual boot option.  Is this possible?  I've seen a lot of advice about disabling Master to install to Slave, then putting them back, etc., but do you really have to go to all that trouble just to get a windblows installation which will hardly ever be used?

Please help!

---

### Post by IgnorantGuru on 2008-10-04
I recently encountered this situation with Windows wanting to write to the first SATA drive.  It's not just the MBR as it required a Windows-compatible partition on the drive.  I'm not sure what that's about.

This is a step-by-step which covers backing up and restoring the MBR, backing up and moving partitions, etc.:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

I think in your situation I would create that small (1G) partition on the Master and let Windows use that space for whatever it is writing.  I don't think it will touch a linux partition.  Backup the MBR on the Master before proceeding so you can restore it after the Windows install.

---

### Post by caljohnsmith on 2008-10-04
> **Major Pain said:**
> 
So I want to install it to my Slave.  But when I put in the install disk and tell it do that, it tells me it needs to write some code to the Master (I assume the MBR) but that that drive has another system on it that can't be recognized.  It tells me to partition something on that drive first (there'as about 1024 MB of unpartitioned space right now on the Master; is this the MBR?)

I don't want to ruin my Kubuntu install and I want W2K on the Slave as a dual boot option.  Is this possible?  I've seen a lot of advice about disabling Master to install to Slave, then putting them back, etc., but do you really have to go to all that trouble just to get a windblows installation which will hardly ever be used?

Please help!
I think you will save yourself a lot of trouble in the near future if you change the slave drive to master, and install Windows to it. If you really, really don't want to do that, you could take that 1 GB of unpartitioned space on your master drive and format it to NTFS. Then when you install Windows on your slave, it will probably stick all its boot files in that NTFS partition on your master drive, and it will also surely overwrite your master drive MBR (Master Boot Record). So do you see how complicated this is all ready getting? Because when you try to move the Windows boot files back to the slave drive, you will most likely have to reconfigure boot.ini or whatever Win 2000 uses to determine its boot partition (I'm used to Win XP). And you will have to reinstall Grub to the MBR of the master drive, which actually isn't too big a deal, but still some work. 

So bottom line is, if I were you, I would disconnect your master drive, make the slave drive master, and then install Windows. After that you can change them back to the way they were. That's just my own opinion based on my experience with Windows. :)

---

### Post by Major Pain on 2008-10-04
caljohnsmith:

This does not make me happy.  God, I wish MS would simply shrivel up and die!  But you're right; I think its the safest way.  :(

Thanks.

---

### Post by Major Pain on 2008-10-04
IgnorantGuru:

Thanks for the advice.  This seems like it will take as long (or longer) than just swapping the Slave to Master, etc.  And I think that this seems to be the safer way.  I *really* hate MS!  If I didn't need the specific software, I would chuck it for good! :(

---

### Post by Major Pain on 2008-10-11
OK.  I couldn't install W2K (don't ask!)  So I have now successfully (??) installed Windows XP onto my second (slave) drive (sdb).  Kubuntu is on the first (master) drive (sda).

Grub still works in that it launches and I can launch Kubuntu.  However, I can't for the life of me figure out how to edit the grub/menu.lst file to see/launch into XP.

The menu.lst file currently reads as follows:

```
default 0
timeout 10
color light-blue/light-gray white/blue

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c4edafc5-5249-4dcb-b7eb-e8f798dcdacc ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c4edafc5-5249-4dcb-b7eb-e8f798dcdacc ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c4edafc5-5249-4dcb-b7eb-e8f798dcdacc ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c4edafc5-5249-4dcb-b7eb-e8f798dcdacc ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows XP Home Edition (NTFS)
root (hd1,0)
kernel \boot.ini quiet
chainloader +1
makeactive
```

Any ideas?  Please help!  This seems like it is the last step. :confused:

---

### Post by caljohnsmith on 2008-10-12
OK, open your menu.lst with:
```
kdesu kate /boot/grub/menu.lst
```
Then add the following at the end:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
If that doesn't work, then please post:
```
sudo fdisk -lu
```
Otherwise, let me know how it goes. :)

---

### Post by Major Pain on 2008-10-12
caljohnsmith:

When I try to input:

```
kdesu kate /boot/grub/menu.lst
```

I get the following:

```
sudo: kate: command not found
```

I can't seem to be able to act as root anymore.  I don't know why.  I recently upgraded to KDE 4.1.2 and ever since then, it seems I can't edit as root.  Any suggestions?

Thanks once again for your help.  I'll keep trying what you have said.  In the meantime, the results of

```
sudo fdisk -lu
```

were

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bca1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   973747844   486873891   83  Linux
/dev/sda2       973747845   976768064     1510110    5  Extended
/dev/sda5       973747908   976768064     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976751999   488375968+   7  HPFS/NTFS
```

---

### Post by caljohnsmith on 2008-10-12
OK, do you have kedit installed? Try:
```
kdesu kedit /boot/grub/menu.lst
```
If you get an error related to using kdesu and not kedit, let me know what it is, but otherwise the above should hopefully work for you.

---

### Post by Major Pain on 2008-10-12
That's great!  It works!  Yahoo!!!!!!  :mrgreen:

Thanks a bunch, caljohnsmith!  I don't know what or why it works, but it does.  I am finally at peace (for now....).

:)

):P

---

### Post by caljohnsmith on 2008-10-12
> **Major Pain said:**
> That's great!  It works!  Yahoo!!!!!!  :mrgreen:

Thanks a bunch, caljohnsmith!  I don't know what or why it works, but it does.  I am finally at peace (for now....).

:)

):P
Great to hear it's working, and I'm glad I could help out; in case you are interested in learning more about Grub and why the above method works, a good place to start is:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

Or if you have any specific questions, feel free to ask. Otherwise cheers and have fun Kubuntu-ing. :)

---

