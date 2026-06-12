---
title: "Grub2 Error"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by Penguin Guy on 2010-04-05
I upgraded Grub Legacy to Grub2 and it was giving me an error 15 when I booted. I finally found out that for some reason grub2 wasn't properly installed. Here's how you install it if you can't gain access to the system. If you *can* gain access to the system, skip to step 3.

[LIST=1]
[*]Boot into the live CD
[*]Chroot into the real system
[LIST=1]
[*]Find which partition the real system is installed on with [FONT="Courier New"]sudo fdisk -l[/FONT]
[*]Make a directory to mount it at with [FONT="Courier New"]sudo mkdir -p /mnt/computer[/FONT]
[*]Change to that directory with [FONT="Courier New"]cd /mnt/computer/[/FONT]
[*]Mount it with [FONT="Courier New"]sudo mount /dev/sd**??** /mnt/computer/[/FONT]
[*]Link [FONT="Courier New"]/dev/[/FONT] and [FONT="Courier New"]/proc/[/FONT] with [FONT="Courier New"]sudo mount -B /dev/ /mnt/computer/dev/[/FONT] & [FONT="Courier New"]sudo mount -B /proc/ /mnt/computer/proc/[/FONT]
[*]Change root with [FONT="Courier New"]sudo chroot /mnt/computer/[/FONT]
[/LIST]
[*]Make sure grub2 is up-to-date with [FONT="Courier New"]update-grub2[/FONT]
[*]Install grub2 to the MBR on one of your drives with [FONT="Courier New"]grub-install /dev/sd**?**[/FONT] (if you only have one, it'll be [FONT="Courier New"]/dev/sda[/FONT])
[/LIST]

---

### Post by stlsaint on 2010-04-05
You say you 'installed' grub2...does that mean you originally had legacy and wanted to go up to grub2?

---

### Post by Penguin Guy on 2010-04-05
> **stlsaint said:**
> You say you 'installed' grub2...does that mean you originally had legacy and wanted to go up to grub2?
Yes, I upgraded from Grub Legacy to Grub2. Sorry for not making myself clear.

---

### Post by oldfred on 2010-04-05
Error 15 often means grub2 is confused with grub legacy. When in your chroot did you total uninstall old grub and do a full re-install of grub2?

#purge old and reinstall new to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub

---

