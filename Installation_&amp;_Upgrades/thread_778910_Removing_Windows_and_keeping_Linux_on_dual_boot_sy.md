---
title: "Removing Windows and keeping Linux on dual boot system"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by petrafan007 on 2008-05-02
Is it possible to remove a Windows Vista NTFS partition and have Linux take over the entire partition? I am looking to run virtual box for the select few programs I need that only work in Windows.

Thanks!

---

### Post by fmartinez on 2008-05-02
Be very careful when you do this; I've had my fair share of screw ups with this. 
command line:
$sudo fdisk -l         #list the partions on  my disk
$sudo fdisk /dev/yourdevice        #choose the device and reformat

REMEMBER TO BACK UP YOU GRUB.CONF FILE AND MENU.LST FILE; ALSO MAKE THE NECESSARY CHANGES IN YOU MENU.LST TO ENSURE YOU WILL BE TO BOOT BACK INTO UBUNTU.
**REMEMBER** BACK UP YOUR DATA PRIOR TO DOING THIS JUST IN CASE.

---

### Post by petrafan007 on 2008-05-02
is there an in depth guide for this anywhere? i just want to make sure I don't screw up because I am a bit new to linux (1 week)

---

### Post by XemeX on 2008-05-02
Use GParted to make it simple.
For safety purposes, make a backup as noted above.

Bear in mind that you have to set the proper partition as active and remember that GRUB has to be present on that partition together with the boot folder.

---

### Post by Rallg on 2008-05-02
(1) If, when you are done, you try to re-boot and get the ominous BIOS message "No operating system," don't panic. Use GParted from the live CD, and be sure that the "boot" flag is set to the correct partition. That advice is already given, above; but it is easy to overlook.

(2) If you ever decide to re-install Windows, you may discover that your validation key is rejected. Don't panic. Under some circumstances, the Windows installer is suspicious if the install partition is not where it is expected. Just do what the installer tells you to do to solve the problem.

---

