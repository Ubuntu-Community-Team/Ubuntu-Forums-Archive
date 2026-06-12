---
title: "On selecting windows 7 (loader) option, the screen goes back to the menu option"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Gurpreet_Singh on 2014-05-28
I had installed ubuntu 14.04 along side Windows 7 (loader). Everything was working fine until, my windows 7 (loader) option doesn't take me to windows 7 but my grub 2 menu is shown again after selecting windows 7 (loader) option in the grub menu. Will be gratefull if anyone can help.

---

### Post by Mark Phelps on 2014-05-28
How did you shrink down Win7 to make room for Ubuntu?  Did you use the Ubuntu installer? Did you use GParted?

If you did NOT use the Win7 Disk Management utility, you likely corrupted the windows filesystem shrinking it.

To get it back working, you need to go to the link provided, download the ISO of the win7 Repair CD, burn the file to CD, boot from the CD, and run Startup Repair three times:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by oldfred on 2014-05-28
You may need Windows repairCD or flash drive.

But lets see details, Boot-Repair can only make very minor repairs to Windows, but will show all the details of your install. Post link to BootInfo report.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Gurpreet_Singh on 2014-05-29
Thank you guys. Actually I had installed from ubuntu live cd. And it was working fine before then suddenly this thing happened. Will do the needful and let you know.

---

