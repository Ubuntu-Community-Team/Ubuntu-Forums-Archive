---
title: "Reloading Grub"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by SpiggidyBob on 2008-03-13
I currently have Ubuntu and XP set up as a dual boot, with Ubuntu being the primary OS.  Problem is, the Windows MBR got installed on my second HDD through my own error.  I know I need to run fixmbr and that's a Windows issue, but I need to know what I need to do before and after to preserve grub and make sure I can still boot to Ubuntu.  i already added the Windows partition to the grub list, but when I select it I get the "No NTLDR" error.  Again, I know how to fix that but just don't know what to do about grub.  Thanks

Also, I'm somewhat new to Linux, although I feel I have a decent understanding of the basics so far.

---

### Post by zxscooby on 2008-03-13
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

a good source for grub info

---

### Post by housam on 2008-03-13
> **SpiggidyBob said:**
> I currently have Ubuntu and XP set up as a dual boot, with Ubuntu being the primary OS.  Problem is, the Windows MBR got installed on my second HDD through my own error.  I know I need to run fixmbr and that's a Windows issue, but I need to know what I need to do before and after to preserve grub and make sure I can still boot to Ubuntu.  i already added the Windows partition to the grub list, but when I select it I get the "No NTLDR" error.  Again, I know how to fix that but just don't know what to do about grub.  Thanks

Also, I'm somewhat new to Linux, although I feel I have a decent understanding of the basics so far.

Use [[COLOR="Red"]_this guide_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

