---
title: "Getting GRUB to boot."
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Freddy on 2007-09-24
Hi all.

I just recently bought myself a new computer and choose to install Windows XP again (I can actually play som games on this machine). After I have installed Ubuntu and reboot it still gets booted into Windows. I see GRUB getting installed but it doesn't boot.

My setup is.

hda1 ext3 formated and mounted as /media/Storage1
hda2 swap

sdc1 NTFS formated and monted as /media/Windows
sdc2 ext3 formated and mounted as /
sdc3 ext3 formated and mounted as /home
sdc4 ext4 formated and mounted as /Storage1

As you can see I use my sata2 disk for both Windows and Ubuntu and use a regular IDE disk to, can this be the problem?

/Freddy

---

### Post by logos34 on 2007-09-24
Sounds like grub installed to the ide drive but you're actually booting the sata drive first.  Go into the Bios at startup and change the hard disk boot priority/order so that the ide is first.  Or it could be that grub didn't install after all.

---

### Post by Freddy on 2007-09-24
Okey thanks, I'll try that and I believe that you might be correct....at least I hope you are =).

---

