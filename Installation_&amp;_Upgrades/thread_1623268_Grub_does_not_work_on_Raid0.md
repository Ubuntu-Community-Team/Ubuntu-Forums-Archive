---
title: "Grub does not work on Raid0"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Kaheil on 2010-11-16
Hello,

Having had many problem using my fakeraid and grub together, I decided to erase everything and start again with a software raid. I created two ext4 partition, two swap partitions and used them as raid0 members. The raid was created just fine and the install went on. However, once the installation is completed, burg refuses to load, leaving me in front of the shell. I tried using "#grub-install @/dev/sdc #grub-install /dev/sdc", but that failed too. 

Ubuntu can see the raid correctly on a liveCD, but fail to mount it. When I do sudo update-grub2 I get the following error: "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

Thank you for your help :)

---

### Post by BobMUK on 2010-11-18
You can't boot from RAID 0, period.

The only RAID array that's bootable is RAID 1.  This is because the bootloader (GRUB) has to be able to assemble/run the array in order to access the data stored on it, which is way beyond the scope of what a bootloader should be able to do (handling RAID is the kernel's job).

You can boot off a RAID 1 array because each member is just a regular partition that the bootloader can read.  Once the kernel is up-and-running it then assembles the members thanks to the little bit of metadata that's stored on it (which basically says "I look like a partition but I'm actually half of a RAID 1 - assemble me!")

What you need to do is create a small partition for /boot that you can boot from.  Once the kernel's up and running it can assemble any arrays needed to continue booting.

---

### Post by Kaheil on 2010-11-19
I'm going to try that, 

Thank you very much :) 

Of all the things I love in Ubuntu, the community is definitely my favourite.

Edit: I'm confronted with two issues. First, I don't know what kind of filesystem I should use in the partition for grub, but I suppose it's ext4. Then, I don't know how to actually put grub there.

Help! :)

---

### Post by lukeiamyourfather on 2010-11-19
More generally speaking, why do you want RAID 0? For most users it won't make any difference in real world use but poses much greater risks of data loss. If you really do need RAID 0 then I suggest getting a quality hardware controller (e.g. Adaptec, LSI, etc.). Also some software and cheaper hardware (JMicron, Silicon Image) implementations can be slower than a single non-RAID disk!

---

### Post by Kaheil on 2010-11-19
You make a fair point there. First of, I'll go with the raw performance: I have two 500Gb WD black hdd, with an average 78mb/s read rate (max 95). Configured in raid0  that rate goes up to 110mb/s. In practice it does not make any difference on basic use, but it's a big deal when moving about big lump of data.*

For now I will use Ubuntu on a single HDD. However, I will try to implement a raid0 on a virtual machine for practice purpose. 

Thank you very much for the help :)

PS: if you know the answer to my questions, it would be of great help whilst testing on the virtual machine.

*All this data is referent to a fakeraid, not a software raid.

---

