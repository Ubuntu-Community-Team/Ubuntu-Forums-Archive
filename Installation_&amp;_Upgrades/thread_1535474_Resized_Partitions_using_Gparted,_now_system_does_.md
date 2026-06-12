---
title: "Resized Partitions using Gparted, now system does not boot"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2010-07-20
I'd appreciate your feedback here.

My /dev/sda drive has three partitons on it as follows:

sda1 Windows7 system partition
sda2 Windows 7 partition
sda4 Ubuntu Partition

Today I shrunk the ubuntu partition moving it towards the end of the drive in order to get more space for my Windows 7 partition (that pig of an OS is always growing).  I then grew the Windows 7 partition to fill the space.  I did this using gparted on the 10.04 live disk.

I've done stuff like this many times before without problems.  This time after reboot, the system won't boot.  Grub never loads.

The first time grub actually loaded, giving me the grub repair console.  Second time I tried booting I just get a message that says "read error".

Not being a stranger to boot problems, I booted back up with the live CD to see what was going on.   To my surprise all partitions are still in good health and their numbers on the drive have not changed.   I mounted my root partition (/dev/sda4) in /mnt and installed grub again using:

grub-install --root-directory=/mnt/ /dev/sda

Grub installs successfully.   Thinking this is behind me I reboot again, only to find the "Read Error" message.

I can't seem to figure out what is going on here.  Any help would be appreciated.

Thanks,
Matt

---

### Post by Rubi1200 on 2010-07-20
Hi,

could you please boot up the LiveCD and then follow the instructions in the link at the bottom of my post.

The results will hopefully give us a better idea of what might be going on.

Thanks.

---

### Post by mattlach on 2010-07-21
> **Rubi1200 said:**
> Hi,

could you please boot up the LiveCD and then follow the instructions in the link at the bottom of my post.

The results will hopefully give us a better idea of what might be going on.

Thanks.

Thank you for your reply.

I will have to do this tomorrow.  It is getting too late.

Just in case I had a partition error, I booted up from the live disk again and ran a fschk on the partition.   It didn't look like it fixed anything, but now instead of a "read error" when I boot I get a weird error I have never seen before:

(HD0.4) Out of Disk

Does anyone know what an "out of disk" error means?

I will look at the link in your tomorrow.

Thanks,
Matt

---

### Post by oldfred on 2010-07-21
See also this link by  meieifra., author of the boot info script.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by mattlach on 2010-07-21
Thanks for your help guys.

I found that my problem was unrelated to Grub.

One of the SATA cables (connected to my /dev/sda drive) wasn't clipped on properly.   For some strange reason when it was partially loose, it allowed drive access and all functioning except being able to boot from it.

Once I discovered the loose wire, I pushed it back on, and now it works again.

Seems awfully strange to me, but it did the trick.

Thanks for the help.  I will have to remember that script.  It seems very effective at information gathering if I ever have boot troubles again.

---

### Post by oldfred on 2010-07-22
Glad you figured it out. That problem the script would not have helped us see your problem.

I hate to open my case as every time I open it I manage to have startup issues and some how I loosened something. I went out & bought new SATA  cables that have  a locking connector. My old parallel cables always were partially connected, I would swear they would get loose just by looking at them. I would push them in and pray they stayed in.

---

### Post by mattlach on 2010-07-22
> **oldfred said:**
> Glad you figured it out. That problem the script would not have helped us see your problem.

I hate to open my case as every time I open it I manage to have startup issues and some how I loosened something. I went out & bought new SATA  cables that have  a locking connector. My old parallel cables always were partially connected, I would swear they would get loose just by looking at them. I would push them in and pray they stayed in.

Agreed.   I will have to be more careful in the future.

What really surprised me was the way it failed due to the loose cable.   I would have expected the drive to either function completely, or to not be discovered in POST at all.

The fact that it was discovered in POST and functioned properly in all regards except booting really threw me off.   I'm just glad it didn't mess up my partition resizing in Gparted...

---

