---
title: "Dual boot XP and Ubuntu"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by joachim10022 on 2010-04-17
Is it possible to install XP after installing Ubuntu?

---

### Post by IndyGunFreak on 2010-04-17
Yes, you just have to be careful... Windows has this desire to nuke your entire drive during install.  Also, assuming you're using Ubuntu 9.10.. You'll want to make sure you have a current Ubuntu Live CD, so you can restore your Boot loader....

ANother thing you can try(note, I've never tried this), assuming you put Windows right back on the same partition, and all goes OK... is use MBRFix, to back up your current MBR... save the image to an external source, reinstall Windows, boot Windows, and restore the MBRFix image... 

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

IGF

---

### Post by goldshirt9 on 2010-04-17
[http://http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://http//apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

if it helps , a little old in the linux issue but i should think too different

---

### Post by joachim10022 on 2010-04-17
> **IndyGUnFreak said:**
> Yes, you just have to be careful... Windows has this desire to nuke your entire drive during install.  Also, assuming you're using Ubuntu 9.10.. You'll want to make sure you have a current Ubuntu Live CD, so you can restore your Boot loader....

ANother thing you can try(note, I've never tried this), assuming you put Windows right back on the same partition, and all goes OK... is use MBRFix, to back up your current MBR... save the image to an external source, reinstall Windows, boot Windows, and restore the MBRFix image... 

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

IGF

If my bootloader gets busted, how do i restore it from the live cd?

---

### Post by wilee-nilee on 2010-04-17
If you have grub2 which should be the case unless you upgraded without installing, step 11.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by IndyGunFreak on 2010-04-17
Nevermind.. see below.

---

### Post by wilee-nilee on 2010-04-17
> **IndyGUnFreak said:**
> Edit:  If you reinstall Windows, its not "IF" your boot loader will get busted, there's about a 98% chance it will, unless you've done some advanced setup/partitions when you installed Ubuntu.  Follow the below, or like I said, try the MBR Fix tool I listed above...

Assuming Ubuntu 9.10 and below...

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Here's the relevant section:

This is for grub legacy which is okay if that is what you have. Karmic came with Grub2, or at least immediately upgrades to it unless you stop it.

---

### Post by IndyGunFreak on 2010-04-17
> **wilee-nilee said:**
> This is for grub legacy which is okay if that is what you have. Karmic came with Grub2.

Did it?.. Wow, my mistake, i was thinking it still had Grub 1...

IGF

---

### Post by wilee-nilee on 2010-04-17
> **IndyGUnFreak said:**
> Did it?.. Wow, my mistake, i was thinking it still had Grub 1...

IGF

It is good for the OP to have all the info possible, it's all good.

---

### Post by unmole on 2010-04-17
This is explained in detail in pages 139-140 of the [Ubuntu Manual]("http://ubuntu-manual.org/").

---

### Post by chris.jericho on 2010-04-17
if you are using 9.04 or before then you can use Grub and if 9.10 for after then use Grub 2

---

