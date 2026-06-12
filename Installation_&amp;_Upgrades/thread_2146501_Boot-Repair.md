---
title: "Boot-Repair"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by jakegub on 2013-05-18
I'm on an Asus UX32vd and was looking to install Ubuntu on my 24Gb iSSD.  It looks like the files are there, but I don't get a grub menu, it goes straight to Windows each time.

[http://paste.ubuntu.com/5678462/](http://paste.ubuntu.com/5678462/)

---

### Post by jamesisin on 2013-05-18
Which operating system did you install first?  If Windows, you'll need to launch a live CD and run sudo update-grub at least.

---

### Post by jakegub on 2013-05-18
Windows was installed first.  I'll try the update-grub.  Will that update the right thing if booting from live usb?

---

### Post by oldfred on 2013-05-18
Grub2 does not install correctly now without the bios_grub partition.

Boot-Repair has told you.
> 
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. (debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sdc1)

 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

I would probably just install grub to the SSD. Boot-Repair likes to install it everywhere.

---

