---
title: "Grub Recovery and a RAID Array"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by LastHylian on 2014-02-04
Hey guys,

I've been using two HDDs equally partitioned so that there is a RAID0 Array for the root filesystem and another RAID0 array for the swap. I have future plans to switch over to my SSD I just got, so I popped it in the same box (without physically altering the cabling for the RAID array) and began to install Ubuntu to the SSD. I did custom partitioning as to make sure it would not touch my existing setup and finished the wizard. The SSD boots fine, but obviously, the RAID array was not found in the grub menu. I rebooted and attempted to boot from the RAID array by using the BIOS Boot menu, but when I do, I am presented with a grub recovery menu.... How do I proceed without destroying my original array? :/

Thanks in advance.

---

### Post by oldfred on 2014-02-05
I do not know RAID, and there are many types.
You may want to add RAID driver to your install on SSD. Not sure which one is correct for your type of RAID.
       mdadm if Linux RAID or dmraid for BIOS or fakeRAID.

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If you now have SSD, not sure why you would want RAID 0.

 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by LastHylian on 2014-02-05
I suppose I should clarify that the SSD is not part of the RAID array. It will become my standalone single SSD for my installation. I am currently using a RAID0 array composed of 2 HDDs for both speed and capacity. The intention is to move to the SSD, then use these extra HDDs as storage - but I digress. 

I found an answer that look promising
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

> I had this same problem when I created my /boot as a RAID 1 mirror on Mint 13.

Solved, by using the install CD to boot back into the system. Then re-mount my drives and chroot into the installed system:


It has been a long time, but can someone refresh my memory on how to chroot from a live CD and mount each drive of the array? And I suppose that begs the other question, "Do I need to re-install grub on both /boot partitions of each drive?"

---

### Post by LastHylian on 2014-02-05
So I was able to mount my RAID array by issuing the following commands. 

```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

While this wasn't the exact solution I wanted (being able to boot from it), this is more than sufficient to let me retrieve my files.

---

