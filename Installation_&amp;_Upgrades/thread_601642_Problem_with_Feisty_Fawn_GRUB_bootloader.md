---
title: "Problem with Feisty Fawn GRUB bootloader"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by jmm_aks on 2007-11-03
I've seen simliar issues on this forum, but can't find a solution to mine. 

I have an Feisty Fawn/XP dual-boot setup but I can't access Feisty Fawn because I never get the GRUB bootloader display asking which OS to boot into.  I have one SATA (with Fiesty and XP on it), and two other internal IDE HDDs.

I had XP installed and decided to dual-boot Unbuntu.  The installation completed and asked me to reboot - when I reboot though, it goes straight to the Windows bootloader and then boots to XP.  I found another thread (can't remember the link) that suggested using the LIVE CD to update/reinstall the GRUB.  I did something like:

sudo grub

find /boot/grub/stage1

then I got hda(2,2) as the result so I did:

root hd0(2,2) l

setup grub

I got messages saying checking to see if /boot/grub/stage1 exists then it said "yes".  There were probably 4 lines like this each which different messages but everything said "exists - yes".  I rebooted and it still went straight to the XP bootloader.  Also, it said it was setting up the bootloader on hd0(2,2) or something like that (the same location hat was output from the "find /boot/grub/stage1" command).

Any ideas?

You can IM, email, or post back to here with suggestions.

ICQ: 62689836
MSN: [email]mnm19@direcpc.com[/email]

---

### Post by xjoshx9 on 2007-11-03
Have you tried using super grub?  That is a possible option.  Don't know how well it works with multiple hard drives though.
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by Pumalite on 2007-11-03
Here is a good guide to reinstalling Grub using the Live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jmm_aks on 2007-11-03
Ok, I tried the: sudo grub; find /boot/grub/stage1; root (hd2,2); setup hd0; quit method.  That did nothing.  I went back in and did the same except used setup hd2 and it shows me the bootloader.  However, it won't but ubuntu or windows (xp is listed).  I can hit 'e' from the grub bootloader and 'e' on "root (hd2,2)" and change that to (hd0,2) and it works, but I can't get back into Windows...

---

### Post by Pumalite on 2007-11-03
The exact error messages would help.

---

### Post by jmm_aks on 2007-11-03
I don't remember the exact error message, but since it was a clean install I just unhooked the ide hdds, reinstalled feisty fawn and then reconnected the ide hdds and everything works fine.

---

