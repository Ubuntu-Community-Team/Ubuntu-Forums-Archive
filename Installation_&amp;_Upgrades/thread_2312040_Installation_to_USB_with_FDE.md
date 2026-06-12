---
title: "Installation to USB with FDE"
date: 2016-02-01
forum: Installation &amp; Upgrades
---

### Post by sm0ker2 on 2016-02-01
Hello!  I'm hoping someone can help me please.  I've been trying for a while to get a mobile OS working.  Ideally I want a full disk encryption USB pen that I can use at multiple sites.  I want to be able to use it at home, work, friends etc. but I want it to be fully encrypted so if it's stolen or lost then I know my data is safe.

I've been able to successfully install and boot on USB2 and USB3 pens but for some reason it very quickly stops working.  I'm testing on 2 PCs so I know it's not a BIOS setting or a USB controller issue.  Also, the USB installer pen ALWAYS boots 100%.  I really can't work out where I'm going wrong.  I've tried all sorts of different BIOS settings and nothing seems to make a difference so I'm thinking it's down to the type of configuration the boot loader users.

It is LVM LUKS encryption I am using from the installer.

Any help would be greatly appreciated!

Thanks
Sam R

---

### Post by sudodus on 2016-02-01
Welcome to the Ubuntu Forums :-)

Maybe you have problems that are caused by running your pendrive in computers that boot in UEFI mode (with Windows 8 or Windows 10). In that case you could try according to this link,

[Stable portable systems - good for USB sticks](https://help.ubuntu.com/community/Installation/FromUSBStick#Stable_portable_systems_-_good_for_USB_sticks)

But it does not offer any ready-made encrypted system.

-o-

If you will be able to switch the computers to BIOS mode (alias legacy mode alias CSM mode), you can create an encrypted disk system installed in BIOS mode, which will work in most, but probably not all the computers.

Install into a pendrive as if it were into an internal drive. The internal drive should be removed while you are doing this installation, otherwise the bootloader will be written into the internal drive.

***Edit:***

Maybe a not a straightforward method, but it should work:

1. Install a small system, for example Lubuntu, which is not encrypted. It can be done according to the first alternative (with the link).

2. Install a virtual machine (for example VirtualBox)

3. Install an an encrypted disk system into the virtual machine.

This will need rather powerful computers and rather much RAM (at least 4 GB) to work.

---

### Post by sm0ker2 on 2016-02-01
Fantastic.  Thank you for replying so quickly.  This does seem like a good option but I was wondering if it's possible to install [this]("http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13426191#post13426191") system and then encrypt the OS retrospectively.  Can I convert to LUKS after install or does that have to be done before any data is copied to the partition?  Maybe 3rd party encryption such as Truecrypt?

Thanks
Sam R

---

### Post by sudodus on 2016-02-01
> **sm0ker2 said:**
> Fantastic.  Thank you for replying so quickly.  This does seem like a good option but I was wondering if it's possible to install [this]("http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13426191#post13426191") system and then encrypt the OS retrospectively.

Yes, maybe :-)> 
Can I convert to LUKS after install or does that have to be done before any data is copied to the partition?  Maybe 3rd party encryption such as Truecrypt?

Thanks
Sam R

I have not learned the manual commands to create or convert to LUKS, but I can use the option for disk encryption (encrypted LVM) in the Ubuntu installer. It might be possible, and you might get help from someone who knows.

I think it would be easier to add encrypted home and encrypted swap afterwards (but I have not done it).

---

### Post by sm0ker2 on 2016-02-01
Thanks for all your help!

---

### Post by sm0ker2 on 2016-03-09
Sorry to resurrect an old thread but I've not had much luck with this!  Does anyone know if it would be any better to use a SSD in a USB caddy?

Thanks
Sam R

---

### Post by sudodus on 2016-03-09
I think the problem will be the same with an SSD in a USB caddy except that it is faster and should last longer. Maybe it would be easiest to do it if you remove the internal drive from the computer, so that the USB drive will be the first detected drive (dev/sda). The you should be able to use the standard procedure in the Ubuntu installer to get disk encryption.

I installed such a system into an SSD in an Akasa USB3 casing recently, so I know that it works, but I'm not sure how portable it is (between computers), and if it survives updates/upgrades if it is installed in UEFI mode.

---

### Post by paulaugust on 2016-03-10
Check out your pendrive memory status it may be the problem of your pen drive next one is check of drivers which are installed in proper way or not.

---

