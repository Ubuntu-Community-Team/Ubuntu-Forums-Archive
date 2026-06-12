---
title: "Pre Installed Window 8 not listed on grub after installing Ubuntu"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by taiwo2 on 2014-08-20
[http://paste.ubuntu.com/8093797](http://paste.ubuntu.com/8093797)


Please help

---

### Post by T.J. on 2014-08-20
Is one or both operating system installed using UEFI? If one is and one is not, it will not show up on the list because Ubuntu will use the bootloader for whatever setup Ubuntu used to install.

---

### Post by dave131 on 2014-08-20
Try running boot-repair in Ubuntu and post back the link it creates to the output.

---

### Post by kansasnoob on 2014-08-20
> **dave131 said:**
> Try running boot-repair in Ubuntu and post back the link it creates to the output.

It's in the OP.

---

### Post by oldfred on 2014-08-20
You show BIOS installs.

But you seem to have a newer grub installed to the partition boot sector of sda5.
Normally you only install grub to the MBR not the partition boot sector.

It does look like Boot-Repair did reinstall grub to MBR, and that would have run this which should have found Windows. Try this again and if it does not work, we can manually add an entry into 40_custom.
sudo update-grub

Did you leave Windows hibernated? Or not resize from inside Windows and reboot so it can run chkdsk and update to its new size.
Both sda2 & sda3 show typical Windows boot files. And with boot flag on sda2 that is the normal Windows boot partition.

# Manual entry:
       gksudo gedit /etc/grub.d/40_custom
      
 # update grub menu after any change
sudo update-grub

    ```
 menuentry "Microsoft Windows 7 BIOS-MBR" {
    insmod part_msdos
    insmod ntfs
    insmod ntldr     
    set root='(hd0,msdos2)'
    ntldr ($root)/bootmgr
  }

    
```

---

### Post by dave131 on 2014-08-20
> **kansasnoob said:**
> It's in the OP.
Sorry.

---

### Post by dave131 on 2014-08-21
oldfred: The title of the thread says preinstalled Windows 8 not listed in grub, and you mention things are in BIOS installs.  I'm just a newbie here, but I thought I remembered in another of your posts in another thread that Windows 8 must be in UEFI mode, and that you can't mix UEFI and BIOS installs.  Isn't this part of the problem?

---

### Post by oldfred on 2014-08-21
Not sure what OP has. :)
Part of why we usually need more info as users are not familiar with details of system.

It is my understanding that Microsoft required all vendors to install Windows 8 in UEFI mode with secure boot on.

So either Windows 8 was updated from a Windows 7 BIOS install or the Windows 8 was not pre-installed by a major vendor?

---

### Post by dave131 on 2014-08-22
thanks - didn't mean to intrude.  I'm just a newbie myself.

---

