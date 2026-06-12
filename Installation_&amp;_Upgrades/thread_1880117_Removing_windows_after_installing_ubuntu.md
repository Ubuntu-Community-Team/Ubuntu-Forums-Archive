---
title: "Removing windows after installing ubuntu"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by 123.arindam on 2011-11-13
Hey guys,
                 I first installed ubuntu inside windows xp and was using that  for a while. Today to get rid of windows I reinstalled ubuntu from a usb drive. While installing it gave me message that "there is another ubuntu in my computer, so do I want to install them side by side or want to delete the previous one". I chose the second and deleted the previous one. I never got any message about windows xp! But when I restarted 
the computer the windows was gone! Only the new ubuntu is there. I guess it is okay as this is what I wanted. But I'm curious that whether I've really erased windows or not. Please reply.

---

### Post by raja.genupula on 2011-11-13
hi give me the output of ```
sudo os-prober
```
and in my signature there is a name called bootinfoscript
post output of that one also.

Thank you

---

### Post by Mark Phelps on 2011-11-13
How did you know Windows was actually gone?  Simply because the PC now boots directly into Ubuntu does not mean that Windows was removed; instead, it only means it's not included in the boot menu.

When you get inside Ubuntu, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive -- and we can see if the Windows partition is still there.

---

### Post by 123.arindam on 2011-11-13
hey, thanks........................reply is Noting, I mean I ran that in a terminal...........but no output

---

### Post by 123.arindam on 2011-11-13
@Mark..............thanks for your reply........I tried what you asked...........here is the output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   310503423   155250688   83  Linux
/dev/sda2       310505470   312580095     1037313    5  Extended
/dev/sda5       310505472   312580095     1037312   82  Linux swap / Solaris


Now I don't know this "Extended" thing is Windows or not

---

### Post by vandamme on 2011-11-13
In this noob's opinion, your XP is gone. Windows needs a real partition, can't work in an extended partition. It's too small anyhow. If you run GParted, the partition editor, you'll probably find that there's no NTFS (Windows readable) partition, they're all ext4 (linux). That wimpering you hear is Steve Ballmer and Bill Gates. You are free!

---

### Post by darkod on 2011-11-13
Unfortunately it looks like your XP is gone. That disk has only linux partitions, no ntfs.

Are you sure the message said another ubuntu? Usually I think the message is "another OS", just generally. So if you select to erase and use whole disk for ubuntu, it says very clearly that it will delete all the data on it.

---

### Post by 123.arindam on 2011-11-15
well, I wish it is gone as I was going to do that any way

---

### Post by 123.arindam on 2011-11-15
but is there a way I can check that it is gone?

---

### Post by matt_symes on 2011-11-15
Hi

> **123.arindam said:**
> well, I wish it is gone as I was going to do that any way 

You'll be happy then as it's gone.

> but is there a way I can check that it is gone?

You already have.  sudo fdisk -lu.......

The extended partition is a container for logical partitions. 

There is no Windows on your disc (sda).

Kind regards

---

### Post by 123.arindam on 2011-11-15
Hi,
Thanks a lot for your reply guys !

best
 matt_symes;11460677]Hi

You'll be happy then as it's gone.



You already have.  sudo fdisk -lu.......

The extended partition is a container for logical partitions. 

There is no Windows on your disc (sda).

Kind regards[/QUOTE]

---

