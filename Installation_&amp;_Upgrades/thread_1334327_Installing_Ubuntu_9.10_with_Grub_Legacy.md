---
title: "Installing Ubuntu 9.10 with Grub Legacy ?"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by nl2br on 2009-11-22
Hi guys,

I've recently tried to install a new copy of the new Ubuntu 9.10, with a fakeraid via BIOS.

I have got an ICH9 southbridge that comes with Intel Matrix Storage, and I did a RAID 1 (mirrored) array between 2 disks.

Well, the point is, that I want to install Ubuntu in the mirrored map, so, the problem is that when the install goes trough the GRUB installation, it just fails.

I've searched in google but appearently there is no current fix or something. 

Here they have the same problem that I have:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340)

Grub 2 is not supporting this kind of mapping. So I think using Grub legacy would do the trick, but, I am not sure how do I do that. Would you guide me, please?

Thanks in advance!  :)

---

### Post by nl2br on 2009-11-24
Any Ideas?

---

### Post by drs305 on 2009-11-24
> **nl2br said:**
> Any Ideas?

During the installation, one of the last steps includes an "Advanced" option. If you click on that button, it displays Grub install options. Perhaps you could deselect the installation of the Grub 2 bootloader, finish the install, then boot from the LiveCD and install grub legacy.

The Grub 2 community doc has a section on how to remove G2 and install Grub legacy. You wouldn't have to remove G2 since it wasn't installed, but you could follow the remainder of the section.

[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy")

I don't use raid so I can't help you there, but either you know how to set it up in Grub legacy or presumably can find the answer on the forums.

---

### Post by mstaehr on 2009-11-24
Thanks for creating this thread, nl2br. I am stuck in the exact same situation with ICH7R + RAID1 and found the same bug report. Still browsing around to find out how to get around what appears to be a Grub 2 bug.

---

### Post by mstaehr on 2009-11-28
Well... I ended up forgetting about fakeraid and used md instead. This seems to work just how I wanted. Good luck!

---

### Post by cgb223 on 2010-01-02
so does the live cd method work? if so how do i do that?

---

### Post by cedric.driard on 2010-01-02
I think you can read this, I have got the same problem
[http://ubuntuforums.org/showthread.php?t=1360445&highlight=grub2+fakeraid](http://ubuntuforums.org/showthread.php?t=1360445&highlight=grub2+fakeraid)

---

### Post by freackout on 2010-01-02
> **nl2br said:**
> Hi guys,

I've recently tried to install a new copy of the new Ubuntu 9.10, with a fakeraid via BIOS.

I have got an ICH9 southbridge that comes with Intel Matrix Storage, and I did a RAID 1 (mirrored) array between 2 disks.

Well, the point is, that I want to install Ubuntu in the mirrored map, so, the problem is that when the install goes trough the GRUB installation, it just fails.

I've searched in google but appearently there is no current fix or something. 

Here they have the same problem that I have:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340)

Grub 2 is not supporting this kind of mapping. So I think using Grub legacy would do the trick, but, I am not sure how do I do that. Would you guide me, please?

Thanks in advance!  :)
i had a setup using similar system when ext4 first came out, however the grub responsible legacy should i say must be on ext 3, however i did get everything working following the alternate.iso install with ubuntu quite easily incorporating a later pmagic disk (the partitioner also needs to be ext4 compliant, with the tools on for this purpose. ie grub2 is still on ext3 but a very small partition set up when ubuntu say wipes the whole system for you if thats what you wish.
ie i had raid 0 lvm, plus a completely seperate disk for backup not raid 1, cos thats just me. and IE MOST OF MY SYSTEM WAS EXT 3, i was just testing the speed of a minor ext4 single partition and wow was it fast.
you may find pmagic helps also as it can show device mappings ect.

---

### Post by freackout on 2010-01-02
you may find the extra options on the pmagic (4.8) from distrowatch.com also has automatic settings for setting up grub and grub2 for you.. which you might also find very handy with your drive mapper included plus its a live everything goes type of recovery cd too the best ive ever come across.
a must for any pc toolbox. (ie scroll down to extras on the boot)

---

