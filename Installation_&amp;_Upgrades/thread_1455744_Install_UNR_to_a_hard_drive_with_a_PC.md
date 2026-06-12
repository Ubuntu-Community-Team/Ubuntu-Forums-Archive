---
title: "Install UNR to a hard drive with a PC"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by pillar007 on 2010-04-16
Hello,

I have a MSI Wind netbook which has a hard drive that I think will die very soon.  I would like to use my Windows 7 desktop to install UNR onto a second hard drive that I have, so that I can switch it out when the current drive fails.  Is this possible?

All drive are SATA, if that makes a difference.

Thanks for the help!

---

### Post by snowpine on 2010-04-16
It would be faster and easier to simply clone your current drive to the new drive.

Many tools exist for this such as: [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by pillar007 on 2010-04-16
> **snowpine said:**
> It would be faster and easier to simply clone your current drive to the new drive.

Many tools exist for this such as: [http://www.clonezilla.org/](http://www.clonezilla.org/)

I should have been more clear, the netbook currently has windows XP installed on it.

---

### Post by snowpine on 2010-04-16
> **pillar007 said:**
> I should have been more clear, the netbook currently has windows XP installed on it.

In that case, yes, go for it. :) Just don't install any restricted hardware drivers for your desktop, because they will be useless on your netbook. ;)

I would recommend physically disconnecting your "regular" desktop hard drive(s) during the install, so that the new netbook HDD is the only drive attached. This will prevent any accidental unpleasantness with the Grub bootloader.

---

### Post by pillar007 on 2010-04-16
> **snowpine said:**
> In that case, yes, go for it. :) Just don't install any restricted hardware drivers for your desktop, because they will be useless on your netbook. ;)

I would recommend physically disconnecting your "regular" desktop hard drive(s) during the install, so that the new netbook HDD is the only drive attached. This will prevent any accidental unpleasantness with the Grub bootloader.

Good call!  I was thinking about installing via windows 7.  Not sure why I didn't think about doing it this way.

Thanks!

BTW I am downloading Lucid Lynx Beta 2.  Do you think this is a good choice?  According to the compatibility page there are some issues with older versions on my netbook, but none on LL.  Is this because there just hasn't been enough testing with it?

---

### Post by nerdy_kid on 2010-04-16
you might have to tweek /etc/fstab after the install (once its running on your netboot).  If you have a linux swap on the machine you are using to install UNR on the (netbooks) HD, then that machines (the pc) swap gets added to fstab (on the netboot hd)...which causes errors once you run it off the netbook cause the pc's swap is no longer there :D  so yeah...

or do what snowpine said...

---

### Post by pillar007 on 2010-04-16
> **nerdy_kid said:**
> you might have to tweek /etc/fstab after the install (once its running on your netboot).  If you have a linux swap on the machine you are using to install UNR on the (netbooks) HD, then that machines (the pc) swap gets added to fstab (on the netboot hd)...which causes errors once you run it off the netbook cause the pc's swap is no longer there :D  so yeah...

or do what snowpine said...

So if I disconnect all my other hard drives I will be ok?

---

