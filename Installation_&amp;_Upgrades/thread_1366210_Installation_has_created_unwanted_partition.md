---
title: "Installation has created unwanted partition"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by blindape on 2009-12-28
Hi, after running ubuntu on a wubi install for many months I finally took the plunge and created a dual boot installation of Ubuntu 9.10 on my laptop.  The newly installed version of Ubuntu seems to be working perfectly.  However I have one question.

During the Installation, the partition I had set aside for the install was split into 2 partitions. Ubuntu was then installed on one partition while the other was left as a mountable file system.  This is a pain as I would have liked ubuntu to be installed on the original partition as a whole.

So I have a couple of questions:  What is the best way to fix this?  Can I merge the two partitions with out loosing the installation of Ubuntu or do I need to re-install ubuntu to fix the problem.  If So what settings do I need to set during the installation to prevent the same partitioning occurring again?
Or,
Is there a workaround to prevent the need to re-install ubuntu.  For example is there a way to turn the empty partition into my home folder?  If this were the case I would be quite happy to leave things as they were and just use the blank partition for saving all my files.

If there are any other ideas or suggestions, I'm always open to trying new ways of doing things.

Cheers,

John Curwood

---

### Post by steveneddy on 2009-12-28
Linux will use two partitions, the primary and a SWAP partition.

Is this what you are describing? Are there the two regular primary and a swap, then an additional primary partition?

See pic - this is Gparted on my laptop which has only one OS installed so it is partitioned for Ubuntu using a large primary and a smaller SWAP partition.

---

### Post by blindape on 2009-12-28
Hi, thanks for the quick response.

 I've taken a screen-shoot of the partitioning on my hard-drive to show how it is set up.

[IMG]/home/curwood/Desktop/Screenshot--dev-sda - GParted.png[/IMG]

sda1-is the recovery partition for windows
sda2-is the windows installation
sda3 to 5 are the linux partitions
sda5 is where ubuntu is installed
sda4 is the swap partition
sda3 is the partition I'm concerned with.

Before the installation sda3-5 was all one partition.  Is there a way I can merge sda 3 and 5 without having to re-install ubuntu.
If not - how do I install ubuntu so that the partition(sda3) doesn't get created.

Cheers,

John

---

### Post by blindape on 2009-12-28
sorry about that last post.  Here is the attached image:

---

### Post by raymondh on 2009-12-28
You can use gparted (from liveCD and in live session ... which will unmount the partitions) to alter/modify your partitions.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

I am also curious about the second partition.  Did you, perhaps, migrate the wubi-install to a dedicated partition in the past?  Did you remove the wubi-installed ubuntu prior to installing the 'new' ubuntu in its' own partition?

Regards,

---

### Post by SecretCode on 2009-12-29
So sda2 (ntfs) is big enough and has no problems? And the unwanted partition sda3 has no data on it?

Booting from a live CD and running gparted, you'll need to:
- delete partition sda3 - it will then be unallocated space
You might want to do this, reboot and check both OSes.

- move & resize the extended partition sda4 (because the unallocated space has to be inside the extended partition) - move its start so 'free space preceding' is zero, and keep its end at the end of the drive (so 'free space following' is zero).
This operation will probably move all the data in sda5 and sda6 along the drive and could take a long time (even hours).

- then move the swap area to the end (no need to 'move' it - you can just delete it and recreate it)
Now you should have unallocated space directly after sda5.
- then resize sda5 to use all the available space. This will resize the partition and the filesystem - will probably take several minutes.


> **blindape said:**
> sda4 is the swap partition
I don't know if that was a typo, but sda6 is swap - sda4 is the extended partition

---

### Post by SecretCode on 2009-12-29
By the way, I have no idea *why* that partition got created. It's unusual.

---

### Post by blindape on 2009-12-29
Hi, thanks for the response SecretCode,

I'm so glad to hear that I should be able to do this without re-installing ubuntu. :D

Well I am about to start, so I will update you on my progress and by the way - Yes, "sda4 is the swap partition" was a typo - my apologies.

Cheers,

John Curwood

---

### Post by blindape on 2009-12-29
All-right, I have one last question before I begin.  Even though there is nothing on the partition when I look at it with Nautilus or the Terminal, on Gparted it shows that 425.05 Mb have been used.  what could be taking up all that space and would deleting the partition be likely to cause problems with booting up ubuntu?

cheers,

john

---

### Post by SecretCode on 2009-12-29
> **blindape said:**
> I'm so glad to hear that I should be able to do this without re-installing ubuntu. :D

There's no guarantee, you understand? ;) You *might* mess up the system and you *ought* to have a backup of each important partition (e.g. using clonezilla), or the important data (and be prepared to reinstall).

> **blindape said:**
> Even though there is nothing on the partition when I look at it with Nautilus or the Terminal, on Gparted it shows that 425.05 Mb have been used.  what could be taking up all that space and would deleting the partition be likely to cause problems with booting up ubuntu?
It's probably just the journal or some such metadata for ext3/ext4. No need to worry about that.

To be really sure, you could boot into ubuntu and check - the following should return nothing if it's not mounted:
```
cat /etc/mtab|grep sda3
```

---

### Post by blindape on 2009-12-29
Thanks for all your help SecretCode!!

I didn't have the spare media to clone the partitons, however I backed up all important files before starting. and then booted with the live CD.

I deleted sda3 and both OS's worked afterwards.

before I could do the next step I had to select the swap partition then from the partition menu select swapoff to fully unmount sda4 and sda6.
I then resized sda4 to include the space left by sda3.
When I did this however sda5 and sda6 remained where they were, so my final step was to resize sda5 to include the new space acquired by sda4 and I never needed to see to the swap partition.

I have since re-booted the OS's and everthing seems to be working fine.

Once again thanks for all your Help.
Cheers,

John Curwood.

---

### Post by SecretCode on 2009-12-29
Good news, thanks for the update!

---

