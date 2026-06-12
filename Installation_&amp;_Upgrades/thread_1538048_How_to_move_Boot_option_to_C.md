---
title: "How to move Boot option to C:"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by CarlFitz on 2010-07-24
New to Ubuntu. Installed to removable disk to try same and because of 

shortage of space on Laptop. Now when booting I must  have removable 

drive plugged in.  What is the simplest way to move the boot option to C:\ 

Drive?

---

### Post by uRock on 2010-07-24
> **CarlFitz said:**
> New to Ubuntu. Installed to removable disk to try same and because of 

shortage of space on Laptop. Now when booting I must  have removable 

drive plugged in.  What is the simplest way to move the boot option to C:\ 

Drive?
In order to for the grub boot loader to work it has to read the grub file withing the ubuntu partition. If it is on a second drive then it will always have to be in when you boot. You can either remove the grub boot loader or install ubuntu onto the primary drive. There may be other ways, but I am not sure of them. If you want to go the route of removing the boot loader and giving the MBR back to Windows, then follow these directions; > **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc Once that is done you can use the LiveCD and install the grub boot loader to the drive which you are using for Ubuntu. Then the fun part is going into BIOS and setting it to boot from the second drive when it is inserted. [See this link for installing grub.]("https://help.ubuntu.com/community/GrubHowto")

uRock

---

### Post by CarlFitz on 2010-07-25
many thanks for your reply,  I am not going into this lightly. I will do it another day when I have read up on it.

---

