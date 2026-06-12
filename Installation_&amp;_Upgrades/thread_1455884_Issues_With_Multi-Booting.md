---
title: "Issues With Multi-Booting"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by Sveetly on 2010-04-16
This may seem like a rather silly thing to do, but for fun I decided to install the Ubuntu Netbook remix (9.10, I believe) on this extra IDE hard drive I had (my other three hard drives are SATA.)  My primary hard drive contains a Windows XP, my second contains Windows 7, and my third SATA drive is just NTFS-formatted storage.  I went through the installer and choose to format and install on my 40GB IDE hard drive, which it did.  Then it finished and rebooted.  It apparently decided to install the GRUB bootloader onto the primary hard drive (not the one it was installed on,) which was not my intention.  The bootloader froze the boot of my computer and wouldn't work.  (Stuck at loading GRUB.)  I couldn't even get to the BIOS.  So I pulled the plug on the primary hard drive and tried to boot again.  I could get into Windows 7 just fine, but that was it.  The problem, though, is that the CD drive (also SATA) no longer shows up in My Computer.  Also, after changing the boot order and replugging in the former primary hard drive, it wouldn't show up, either.  Nor would the IDE one (though I'm pretty sure that's because Windows doesn't understand the EXT (or whatever Ubuntu uses) file system.

Does anyone know why this occurred and how to get those drives to show up in Windows again?  I don't really care to get the netbook remix working here, since this isn't even a laptop, it was just an experiment.  Also, I'd love to know how to remove GRUB from my primary hard disk so that I can boot from it again.

Thanks in advance, and sorry if my story was hard to follow.

---

### Post by oldfred on 2010-04-16
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows will not see the ext partitions so that is normal. I have never heard of an Ubuntu install making the windows not see the CD. That should be controlled by BIOS or windows itself. 

When plugging & unplugging things I almost always have bumped something else and had a loose connector. Even if it looks plugged in, it may be loose.

---

### Post by Sveetly on 2010-04-16
Thanks for the quick reply.  I'll look at those bootloader restore instructions now.  For future reference, if I ever want to go back on a Mac running Linux, how would I go about doing that?

And yes, I've checked the connectors.  In a bloody battle with tight areas with sharp edges, I unplugged and replugged every single plug in my computer.  But in the end, it turns out the problem was a corrupt registry entry (it could've just been coincidence that it happened at the same time, and had nothing to do with Linux after all.)  I've restored the IDE drive, fixed the CD drive problems, and now all that's left is that bootloader.  I hope it works.

Thanks again!

---

### Post by oldfred on 2010-04-16
Do not know about mac. But there is an entire sub-forum on Apple since the partitioning is gpt and the boot loader is efi based which is more modern that all of us with the 25 year old MBR partitioning scheme.

[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

