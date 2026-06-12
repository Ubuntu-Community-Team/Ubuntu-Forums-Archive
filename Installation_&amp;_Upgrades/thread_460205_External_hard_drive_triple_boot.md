---
title: "External hard drive triple boot"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by miggols99 on 2007-05-31
I've been wanting to test out some Linux distros. But I'd like to install them to the computer (not a VM) and mess around with it, and if I like it, install it onto the computer's main hard drive. At the moment, I've got a Ubuntu Feisty and Windows XP dual boot. Can I add the external hard drive, so if it is turned on, that the computer boot's to it's grub?

---

### Post by louieb on 2007-05-31
Probably. Does your PC BIOS support booting to an external drive?  
You say you dual boot XP and Ubuntu now.  Is GRUB your boot manager / loader?
Are they installed on the internal hard drive? 
Checkout the  [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") there are several methods to setting up booting to multiple Linux distros. The two that I use are the chainloader method and the configfile method. Both are explained in the Dual Boot site.

---

### Post by miggols99 on 2007-06-01
1 - I think so, because it can boot from my USB flash drive
2 - Yes, GRUB is my boot manager on the internal hard drive
3 - No, but I have the ISOs.

---

### Post by xstevex on 2007-06-01
i have tried doing this, but when you remove the external drive, grub comes up with an error because the external is missing. what i did to overcome this, was download VirtualBox inside ubuntu, and run a text mode install to the external hard drive (it has usb support), but your xorg.conf will be messed up so you'll need to set that up, or do what i did and copy the xorg.conf from my ubuntu internal install into the external hard drive so they had the same conf.

hope that helps.

---

### Post by xstevex on 2007-06-01
im completely new to linux btw, i was just trying out different ways of installing to an external. there is probably a much easier way.

---

### Post by miggols99 on 2007-06-03
Ok. I've got my testing OS (Debian) installed to the external hard drive. But I have to turn it on, or grub will produce an error. How can I make it so it uses the grub on the internal hard drive, so I don't have to turn on the external one to boot?

---

