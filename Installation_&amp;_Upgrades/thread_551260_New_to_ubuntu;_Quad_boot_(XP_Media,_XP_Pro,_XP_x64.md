---
title: "New to ubuntu; Quad boot? (XP Media, XP Pro, XP x64, Ubuntu AMD64)"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by WHAT THE on 2007-09-14
I'm currently running Windows Media Center (250GB Physical), and Windows XP x64 Pro (80GB Physical). I just installed a brand new 500GB drive and I'm wanting to partition about 100GB for Ubuntu AMD64 and the other 400GB for regular Win XP Pro. Could someone please explain the necessary steps needed to do this, and how difficult it would be to do.
Any help is greatly appreciated, Thank you.

---

### Post by srunni on 2007-09-14
Not sure about installing XP Pro, but I think you should just be able to start up the installer and have it install to that hard drive. Give the NTFS partition 400GB. When you install Ubuntu next, give it the rest of the space, and the installer should detect all 3 of your Windows installs and add them to GRUB. If they don't, it's pretty easy to edit the GRUB configuration file and add those partitions.
One other thing you might want to think about is if you're not actively using all of those XP installs, you could have them as virtual machines instead, and run them from inside one native XP install and from Ubuntu, using VMware (the VMware Server version is free).

---

