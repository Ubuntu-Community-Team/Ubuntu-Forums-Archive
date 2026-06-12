---
title: "Uninstalling Ubuntu"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by The Morninglord on 2008-06-12
I'm sorry if this is redundant, but I looked around and all the instructions seem to be applicable only to partitions, not to my case.

I have a computer with a 320 GB hard drive and a 160 GB hard drive, and I am dual booting XP from the 320 GB drive and Ubuntu from the 160 GB drive. Long story short, for this particular computer, rarely ever use Ubuntu (its primary purpose is gaming) and I would like to reclaim the 160 Gigs that are currently not really going to any productive use.

So my question is this: how do I remove Ubuntu so that I can still access (and boot to) the other hard drive. I accidentally reformatted the 160GB drive a few months ago, and was unable to boot my system (due to what seemed to be a GRUB error) until I reinstalled Ubuntu. I don't particularly want GRUB anymore, because I really don't have any use for it.

Once again, I apologise if this question has been answered before. All of the topics that I could find seemed to be dealing with uninstalling a partition. I don't know if it works the same way if I have previously dedicated a whole drive to the OS.

Thanks in advance.

---

### Post by overdrank on 2008-06-12
> **The Morninglord said:**
> I'm sorry if this is redundant, but I looked around and all the instructions seem to be applicable only to partitions, not to my case.

I have a computer with a 320 GB hard drive and a 160 GB hard drive, and I am dual booting XP from the 320 GB drive and Ubuntu from the 160 GB drive. Long story short, for this particular computer, rarely ever use Ubuntu (its primary purpose is gaming) and I would like to reclaim the 160 Gigs that are currently not really going to any productive use.

So my question is this: how do I remove Ubuntu so that I can still access (and boot to) the other hard drive. I accidentally reformatted the 160GB drive a few months ago, and was unable to boot my system (due to what seemed to be a GRUB error) until I reinstalled Ubuntu. I don't particularly want GRUB anymore, because I really don't have any use for it.

Once again, I apologise if this question has been answered before. All of the topics that I could find seemed to be dealing with uninstalling a partition. I don't know if it works the same way if I have previously dedicated a whole drive to the OS.

Thanks in advance.

HI and this link can help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by dstew on 2008-06-12
Reading between the lines, it seems you are using grub to dual-boot Windows and Ubuntu, correct? If you remove Ubuntu, grub will no longer work, and your computer will be un-bootable.

You will have to install a Windows boot loader into the Master Boot Record (MBR) of your Windows disk. To do that, boot a Windows Recovery CD, and get the Recovery Console. If Windows is on your C: drive, then issue the command```
fixmbr c:
```and you should be good to go. Fixmbr over-writes the MBR with the Windows boot loader, effectively removing the grub boot loader.

Do this before you delete your Ubuntu partition, to make sure Windows is working. Then, once you know you can boot Windows without grub, delete your Ubuntu partition.

---

### Post by The Morninglord on 2008-06-17
That helped a ton. I was kinda getting worried that I'd have a hard drive doing nothing, and I'm glad that it got fixed. Thanks again for the help.

---

