---
title: "Failed to install Ubuntu on my portable hard drive , need help"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Dina.M on 2011-11-11
Hi,

I installed before Ubuntu 11.04 on a USB Flash memory , and it was a success . I boot from it and it works fine . But I need an extra space .
So I bought a portable hard disk [ Samsung S1 Mini ] its size is 160 GB . and tried to install on it Ubuntu 11.04 as I did with the USB Flash , But the installation only sees my hard size 20 GB not 160 GB. I don't know where is the problem ??

---

### Post by LinuxFan999 on 2011-11-11
Is it seen as 160GB when it is mounted in an installed Ubuntu or Windows system? Or just 20GB as the installer sees?

---

### Post by Dina.M on 2011-11-11
I mounted it on Ubuntu Live CD and it was mounted as 160 GB , I even formatted it with ext4 .

---

### Post by fantab on 2011-11-11
> **Dina.M said:**
> Hi,

I installed before Ubuntu 11.04 on a USB Flash memory , and it was a success . I boot from it and it works fine . But I need an extra space .
So I bought a **portable hard disk [ Samsung S1 Mini ] its size is 160 GB** . and tried to install on it Ubuntu 11.04 as I did with the USB Flash , But the installation only sees my hard size 20 GB not 160 GB. I don't know where is the problem ??

> **Dina.M said:**
> I mounted it on Ubuntu Live CD and it was mounted as 160 GB , I even formatted it with ext4 .

During formatting did you delete the partition table, by any chance? 

I suggest you create a [**Live GPARTED DISK**]("http://gparted.sourceforge.net/livecd.php")  and boot with it. This is, IMO,  a must have if one wants to do partitioning, formating, resizing or moving your partitions. This is a safe method.

Once you have booted with Live Gparted Disk:

[LIST=1]
[*]**Delete** all partitions.
[*]**Choose a Partition Table** for your EHDD. If you are not sure which Partition Table to use, then **use DOS**.
[*]**Create Partitions**, **Format** your EHDD
[/LIST]
If this does not help Post here with Screen-shots, if possible.

---

### Post by Dina.M on 2011-11-11
But I faced this problem before formatting it , at first i tried to install Ubuntu as usual , but it didn't display the right size of the EHDD , next I tried formatting it on Linux . SO I don't think the formatting is the cause .

---

### Post by oldfred on 2011-11-11
Were you doing a liveCD install or a full partitioned install with / & swap and possibly /home?

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Dina.M on 2011-11-12
> **oldfred said:**
> Were you doing a liveCD install or a full partitioned install with / & swap and possibly /home?

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
I was installing it full partitioned , But before I create the partition table or select the boot loader , the installer see only 20 GB of the external hard drive.

---

### Post by oldfred on 2011-11-12
Can you partition in advance with gparted? Does gparted show full disk or not?

---

### Post by Dina.M on 2011-11-12
> **oldfred said:**
> Can you partition in advance with gparted? Does gparted show full disk or not?
i tried partitioning with gparted I made a partition 6 GB ( for swap) and the rest in a partition , But the installation only saw 20 GB , the only difference that they were divided into two partition one approx. 19 GB and the other approx. 1 GB .

---

### Post by oldfred on 2011-11-12
You have one of the new 4096-byte physical sectors drives. The software is seeing it as 512 and is confused. Are you using the newest version of Ubuntu or download the newest version of gparted as a liveCD?

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

There is no real reason why on a small drive they went with the new 4096 when 512 has been the standard for so long. 

Another brand with 4096 byte sectors/\.
How to install a WD Advanced Format Drive on a non-Windows Operating System
the following distributions will default to good alignment for Advanced Format disk drives: Ubuntu 10.04, Fedora 13, Redhat 6 and derived products. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

You may want to check if your vendor has more info somewhere.

---

### Post by Dina.M on 2011-11-12
> **oldfred said:**
> You have one of the new 4096-byte physical sectors drives. The software is seeing it as 512 and is confused. Are you using the newest version of Ubuntu or download the newest version of gparted as a liveCD?

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

There is no real reason why on a small drive they went with the new 4096 when 512 has been the standard for so long. 

Another brand with 4096 byte sectors/\.
How to install a WD Advanced Format Drive on a non-Windows Operating System
the following distributions will default to good alignment for Advanced Format disk drives: Ubuntu 10.04, Fedora 13, Redhat 6 and derived products. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

You may want to check if your vendor has more info somewhere.
I am using Ubuntu 11.04 , and gparted-live-0.10.0-3 .

---

### Post by oldfred on 2011-11-12
The manual discusses that with XP you cannot format it and have to download software from their site.

This seems to be a reoccurring issue with this model drive and I have not seen a good solution.

---

