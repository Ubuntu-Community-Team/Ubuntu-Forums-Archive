---
title: "dual boot uninstall"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by valke on 2010-03-26
Hi, all. I'd like to uninstall Ubuntu 10.04 beta off my dual boot (shared with Windows 7) so that I can have my full hard drive back. It's not that I don't like 10.04, but rather, I'd like to install it on my portable hard drive. I'd thought, but was mistaken, that I could just run the live cd and delete the partition Ubuntu was in. Sadly, no. Instead I got a lovely GRUB error, saying that the partition was not found. Thankfully I was able to run the live cd again and repartion and install Ubuntu, allowing me to then be able to run Windows or Ubuntu. So, in short, how can I uninstall Ubuntu without getting the GRUB error?

---

### Post by stlsaint on 2010-03-26
You need to delete the partition as you had before then give the mbr back over to windows bootloader. Basically you need to remove grub from the hdd. This can be done many ways (removing grub) and a quick google search will yield many results from which you can choose based on what resources you have.

---

### Post by Contra75 on 2010-03-26
Download Easy BCD and follow the guide.

---

### Post by oldfred on 2010-03-27
You still had grub in the MBR with the rest of grub missing. You just have to reinstall  a windows bootloader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


From Ubuntu you can do it also:
Restore basic windows boot loader - not lilo
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by maybeway36 on 2010-03-27
You can also use DOS to remove GRUB from the MBR:
```
fdisk /mbr
```

---

