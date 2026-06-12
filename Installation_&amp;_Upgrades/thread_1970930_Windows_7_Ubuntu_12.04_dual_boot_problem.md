---
title: "Windows 7 Ubuntu 12.04 dual boot problem"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by ogoforth on 2012-05-01
I currently have Windows 7 64 bit installed.  When I install Ubuntu 12.04 as a dual boot the machine boots directly into windows.  No GRUB menu.  The OS installs into the partition that the setup creates but I am not given an option to b:mad:oot into that new install.

---

### Post by jadtech on 2012-05-01
when you installed did you choose to install grub or did you opt to not install it ???

---

### Post by ogoforth on 2012-05-01
I was not given such an option.

---

### Post by thagame on 2012-05-01
same issue. ubuntu installed but no grub. and there was no option to install grub or dont install grub. Back to gentoo i guess.

---

### Post by oldfred on 2012-05-02
Do you have more than one drive, or is USB promoted to sda, as grub often just installs to sda. In BIOS you then have to boot from that drive.

To see where everything is installed post the link to Boot-Info from this:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

@thagame
If you want to post your boot info please start a new thread as two different reports starts to get confusing.

---

### Post by cgaie on 2012-05-06
The same here with Windows 7 64bit.

I was not given the option to install grub

After installation I went into windows 7

I will try boot repair

---

### Post by cgaie on 2012-05-06
Surprise

After I boot in WIndows 7 to create the Boot Repair CD I restarted PC to boot up from the CD and I got my grub just there with Windows 7 aside

It's working perfect and I did nothing


Love Ubuntu

---

