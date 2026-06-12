---
title: "Update to 6 online with dual boot??"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2006-06-28
I hate to ask lame questions, but have prowled the forums for a coupla hours and haven't seen this directly addressed.

I've got a dual boot W2K/Breezy PC.  The Official Ubuntu Guide suggests that non-experts should just use the online Update Manager to go to Dapper.  Sounds like the way to go.  

Can I use the Update Manager to update without upsetting the dual boot/MBR/grub applecart?  Will updating in that manner effect the MBR and cause the PC to lose track of Windows or Ubuntu?

I know there are no guarantees, but would just like to hear someone verify whether that's an accepted way to go for Windows/Ubuntu dual boots.

Thanks!

---

### Post by aysiu on 2006-06-28
Updating won't affect Grub's position on the MBR, but it will upgrade the /boot/grub/menu.lst configuration file to reflect the kernel change.

---

### Post by johnc4510 on 2006-06-28
It should not affect the dual boot, because it is just upgrading your Ubunut system on the / root partition. The only thing I would advise is to back up everything you wouldn't want to lose. Another questions you should consider is this: Are your home files /home on a separate partion from your / root partition. If not, be sure to backup all your home files!

---

### Post by aysiu on 2006-06-28
If you're really paranoid, try backing up with PartImage before you upgrade. That way you can easily restore your old configuration should something go wrong.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

