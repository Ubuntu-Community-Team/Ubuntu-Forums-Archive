---
title: "How to Re-install Ubuntu on Dual-boot with Windows XP"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by pwalter on 2008-04-07
I previously installed Ubuntu Draper Drake as a dual-boot on separate HD from the drive with Windows XP.  

Recently attempted _unsuccessfully _to upgrade to next version.  Cannot access Ubuntu.  Don't need to save anything on that HD.   

Would like to delete GRUB and install latest version of Ubuntu on the second HD.  How to go about this?

Thanks.

---

### Post by Belak on 2008-04-07
I would actually recommend waiting until Hardy Heron comes out (I think it's the 24th of this month.)

When you want to do it, you'll have to follow the following instructions:
You'll have to download and burn the Alternate Install CD (Located at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) Just be sure to check the alternate desktop cd box.
You should be able to follow this guide: [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
When you get to partitioning, chose the NTFS partition and set it's mount point as /media/windows or something like that. This is so you can access your Windows Files in Ubuntu. I would also recommend a separate home partition (Mounted at /home) and a separate root partition (Mounted at /) so that way, if you ever have to upgrade again, you can keep your old settings and stuff.

Cheers, and good luck!

ps - I have a triple boot on my system, so I know that this works.

edit: Sorry, I didn't see the fact that you had 2 HD's. This should still work, but I can't vouch for it.

---

### Post by zvacet on 2008-04-07
Do it same way you did it when you installed Dapper.When you get to the partition stage delete all Ubuntu partitions and on that unallocated space install new version.Making separate home partition is good idea.I don´ think that you need more then 10GB for root.

---

### Post by pwalter on 2008-04-07
Thanks for your response.  Makes sense to wait until the new Ubuntu is released.
Still have a question about the GRUB boot loader. Currently, my GRUB opens with 14-lines of text so I have to page down if I want to select Windows XP.  Will a new install write over the existing GRUB? or is there a way to delete it prior to install?

---

### Post by zvacet on 2008-04-08
In synaptic find linux-image package and delete them,but leave one (or two if you want) with higher number.

---

