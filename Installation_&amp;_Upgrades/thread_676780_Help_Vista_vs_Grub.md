---
title: "Help Vista vs Grub"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by Telescope_Nerd on 2008-01-24
Please help me I don't understand!!!!!

I am trying to install ubuntu on my laptop, while dual booting it with vista, which came pre installed. The plan was to create a partition in the second of my two hard disks using vista, install ubuntu on this partition, ask grub to be installed on this partition also and use easybcd to modify vista's bootloader to go find grub on the partition and boot ubunto from there.

Not working so far! 

I used vista to create a 75G partition in the second hard disk, fine. During Ubutu instalation I selected "manually edit partition table" selected the partition I had made using vista and changed it's settings to: "file system=Reiserfs" and "mount point = /". Then on the final step of the installation I selected the "advanced" tab where you cam choose where grub gets installed I specified hd(1,1) to indicate my partition. then ran the istallation. Towards the end I got an error message something like:

"Grub failed to install to hd(1,1), this is a fatal error."
-instalation exits

I also tried specifying my partion as sdb2 instead of hd(1,1), same story.

I think I'm going wrong somewhere in the manual partition set up. I followed the instrutions from the easybcd website ( i.e. reiserfs and mount point "/") but shouldn't i be doing more like maybe making a swap partition and a /boot partition? I am so confused Can anyone help me??

---

### Post by Computer Guru on 2008-01-24
Swap partitions are unnecessary. /boot partitions are relics of ancient *nix systems.

All you need is a / partition with a /boot/ folder in it (which Ubuntu makes by itself).

The "Grub failed to install" fatal error is a known issue, bug report filed on the matter here:
[https://bugs.launchpad.net/ubuntu/+bug/181276](https://bugs.launchpad.net/ubuntu/+bug/181276) (not yet addressed).

If you follow the pictorial on the EasyBCD website ([http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)), it defaults to installing GRUB to the *MBR* as a workaround, then uses EasyBCD to set things straight.

---

### Post by SunnyRabbiera on 2008-01-24
> **Computer Guru said:**
> Swap partitions are unnecessary.

Not if he has lower specs

---

### Post by amdalex on 2008-01-24
I'd always have some swap incase I run out of memory.

---

### Post by Computer Guru on 2008-01-24
True. At any rate, the guide says to go ahead and create a swap partition if you like.. no harm, no foul ;)

---

### Post by Telescope_Nerd on 2008-01-24
Oh right, thanks for the info. Is this bug only relevant to gutsy? Will it work if I follow the same procedure I originally tried but with the previous ubuntu release(feisty)?

---

### Post by Telescope_Nerd on 2008-01-24
**UPDATE!!!!!!!**
Just tried the instalation again but this time I specified the file system as "ext/3" instead of "Reiserfs". I asked grub to be installed on "/dev/sdb2" which is the partition I was installing ubuntu on. And it worked!

Then I set up easybcd to look for grub on the ubuntu partition, works like a dream!

Computer Guru, I know my experience is a single statistical sample but maybe you should think about changing you guide to recommend ext3 instead of reiserfs as this is the only thing I changed and it fixed the problem for me. p.s. thanks for easybcd geat software!

---

### Post by Computer Guru on 2008-01-25
sh!t.... it looks like GRUB fails to install to a ReiserFS partition - bug in the Ubuntu setup.

Just tested it myself in a VM, tried to insall once to ReiserFS and a second time to ext3.

Thanks for putting me on the right trail, Telescope_Nerd.

---

### Post by Computer Guru on 2008-01-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/185878](https://bugs.launchpad.net/ubuntu/+bug/185878) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bugged.

[https://bugs.launchpad.net/ubuntu/+bug/185878](https://bugs.launchpad.net/ubuntu/+bug/185878)
[http://neosmart.net/blog/2008/ubuntus-buggy-support-for-non-ext3fs-partitions/](http://neosmart.net/blog/2008/ubuntus-buggy-support-for-non-ext3fs-partitions/)

---

### Post by Telescope_Nerd on 2008-01-29
Hey Computer Guru
Good work on following up this bug and thanks for updating the step by step on your site. I know a lot of peeps who are considering taking tentative steps toward ubuntu and open source in general but are paranoid about screwing up their vista istallation. I think your new guide is the  "definitive" option for this growing group of Ubuntu newbies, like me.
Cheers
T

---

