---
title: "In a pickle... need help with installation."
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by T.Louis on 2006-10-23
Hello,

I'll try to be brief with my problem.

*First*, I tried to install from the Dapper CD, which didn't work because of the known issue with the Mounting of the filesystem.

*Second*, I followed one of the tips to download and try to install from the DVD version as that seemed to solve the problem and it did as far as continueing the installation properly.

*Third*, I loaded Ubuntu, and hit the install Icon on the desktop. I selected an empty drive that I had bought for Ubuntu. It installed fine etc.

Now the problem begins after reboot.

*First*, I got the "Grub error 21". Or alternatively if I change my HDDs booting sequence I get NTLDR missing.

My harddrives are as follows:

[LIST]
[*]**2** small WDs in a RAID with Windows XP on it.
[*]**1** storage drive with NTFS for Win.
[*]**1** drive that now has Ubuntu on it.
[/LIST]

I guess the RAID is causing the problem?

I have read the numerous threads about "Grub Error 21" and so on, and the only solution that I can find that is valid is: Put in Windows XP CD, Recovery, fixmbr, and forget Ubuntu while I have a Windows XP raid?

Any suggestions are welcome, and as I write this I'm still searching and reading for solutions. (A side note is that I hate the fact that I do not actually have a floppy drive in my computer.)

Thanks in advance for any help.

---

### Post by gn2 on 2006-10-23
The general principle outlined in this thread should get you fixed up: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by T.Louis on 2006-10-23
Thank you for the reply.

Reading it right away.

---

### Post by T.Louis on 2006-10-23
Thank you greatly for the above thread. It worked like a charm. I fixed my boot record for the Win RAID and it works, and I installed Ubuntu by itself with all other drives disconnected as stated. I wish I had found this thread before but I just didn't stumble upon it when doing searches.

I have a follow up question. If I edit /boot/grub/menu.lst do I need to write anything special to let it know that my Windows XP is on a RAID config?

---

### Post by gn2 on 2006-10-23
> **T.Louis said:**
> Thank you greatly for the above thread. It worked like a charm. I fixed my boot record for the Win RAID and it works, and I installed Ubuntu by itself with all other drives disconnected as stated. I wish I had found this thread before but I just didn't stumble upon it when doing searches.

I have a follow up question. If I edit /boot/grub/menu.lst do I need to write anything special to let it know that my Windows XP is on a RAID config?

Sorry, don't know, Bulldog might be better able to help with that.

I believe it can be done though.

Have you done a search about adding RAID to grub?

---

### Post by T.Louis on 2006-10-23
> **gn2 said:**
> Sorry, don't know, Bulldog might be better able to help with that.

I believe it can be done though.

Have you done a search about adding RAID to grub?

Yes, first thing I do.

I finally got it working, and the solution is simpler than I would have thought, and can be found in the Wiki FakeRAID and posts. ](*,) 

Not sure if this is of any interest to anyone but basically what you do is:

[B]1. Install dmraid. 
[/B]
[INDENT]i) In Ubuntu basically go into: System -> Administration -> Synaptic Packet Manager.
ii) In the menus pick Repositories and tick the one that is binary and (Universe). It is not ticked by default install.
iii) Reload, and mark for install and then let it download and install itself.  [/INDENT]

**2. Add your RAID to grub Device.map**

[INDENT]First, do a:
```
ls /dev/mapper
```

and you will find something like this:

```
control  nvidia_ebjhjcbc  nvidia_ebjhjcbc1  nvidia_jgdgbfaj  nvidia_jgdgbfaj1
```

if you have an nVidia based chipset of course.

If you list the first entry with fdisk:

```
sudo fdisk -l /dev/mapper/nvidia_ebjhjcbc
```

you should get an NTFS partition which should be your full RAID:

```
Disk /dev/mapper/nvidia_ebjhjcbc: 74.0 GB, 74039130112 bytes
255 heads, 63 sectors/track, 9001 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot                  Start  End  Blocks            Id  System
/dev/mapper/nvidia_ebjhjcbc1   *     1   9000    72292468+ 7   HPFS/NTFS

```

Then proceed to add it to the **device.map** (in /boot/grub/):

```
(hd1) /dev/mapper/nvidia_ebjhjcbc
```[/INDENT]

**3. Add it to the grub menu.lst**
[INDENT]
Fix the menu in menu.lst (in /boot/grub/ also):

```

title           Windows XP Professional SP2
root            (hd1,0)
map             (hd1) (hd0)
map             (hd0) (hd1)
chainloader +1

```[/INDENT]

---

