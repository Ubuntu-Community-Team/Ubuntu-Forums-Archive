---
title: "No grub after 13.10 install"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by woopud on 2013-10-20
Just installed Ubuntu 13.10 alongside Windows 8 but upon reboot there's no grub?  It boots directly into Windows 8.  Any help would be appreciated.

---

### Post by fantab on 2013-10-20
In machines with pre-installed Windows8 you mostly have UEFI boot. Does you machine boot in UEFI?

Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") utility. It can fix most of the boot issues. Most of the times 'Recommend Repair' is enough. Perform Boot-Repair from a Live Ubuntu DVD/USB.

---

### Post by woopud on 2013-10-20
I did try the Boot-Repair but it din't work either, it did mention something about the PC booting in legacy mode instead of uefi?

---

### Post by woopud on 2013-10-20
So, when running Boot-Repair this comes up

 "The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?"

---

### Post by oldfred on 2013-10-20
Fixed title.

You need to run Boot-Repair in UEFI mode, or reinstall in UEFI mode. From UEFI you should have two boot choices, one UEFI and the other BIOS/CSM/Legacy, but not always clearly labelled in UEFI menu.

---

### Post by woopud on 2013-10-20
How do I run boot-repair or ubuntu installation in uefi mode?

---

### Post by fantab on 2013-10-20
You have to boot Ubuntu Live DVD/USB in UEFI mode... When Selecting your boot device to boot from choose the DVD/USB in UEFI or EFI. If you boot Ubuntu in EFI mode you will see a black background with options. You see regular ubuntu background if you boot in legacy mode.

---

### Post by woopud on 2013-10-21
Thank you!  Got it working now.

---

### Post by fantab on 2013-10-21
I'm glad its working. Mark the thread as 'solve' using 'Thread Tools'.

---

