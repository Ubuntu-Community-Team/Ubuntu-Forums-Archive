---
title: "selecting grub install device"
date: 2020-03-20
forum: Installation &amp; Upgrades
---

### Post by lvm on 2020-03-20
During a routine package upgrade (apt-get upgrade) it prompted me 
```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The grub-pc package is being upgraded. This menu allows you to select which devices you'd like          &#9474; 
 &#9474; grub-install to be automatically run for, if any.                                                       &#9474; 
 &#9474;                                                                                                         &#9474; 
 &#9474; Running grub-install automatically is recommended in most situations, to prevent the installed GRUB     &#9474; 
 &#9474; core image from getting out of sync with GRUB modules or grub.cfg.                                      &#9474; 
 &#9474;                                                                                                         &#9474; 
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to       &#9474; 
 &#9474; install GRUB to all of them.                                                                            &#9474; 
 &#9474;                                                                                                         &#9474; 
 &#9474; Note: it is possible to install GRUB to partition boot records as well, and some appropriate            &#9474; 
 &#9474; partitions are offered here. However, this forces GRUB to use the blocklist mechanism, which makes it   &#9474; 
 &#9474; less reliable, and therefore is not recommended.                                                        &#9474; 
 &#9474;                                                                                                         &#9474; 
 &#9474; GRUB install devices:                                                                                   &#9474; 
 &#9474;                                                                                                         &#9474; 
 &#9474;    [ ] /dev/sda (2000398 MB; HGST_HUS726020ALE614)                                                      &#9474; 
 &#9474;    [ ] - /dev/sda2 (1999860 MB; /)                                                                      &#9474; 

```

So what should I choose - /dev/sda or /dev/sda2 (mounted as root and where grub.cfg is) or both? grub.cfg mentions /dev/sda2 by uuid. Where is /dev/sda1 which is mounted as /boot/efi? And how can I run it automatically as mentioned in the second paragraph?

18.04. grub-efi-signed is installed although secure boot is disabled - don't know why the installer did it.

---

### Post by Rick St. George on 2020-03-20
I recommend this posting by Old Fred on UEFI boot install & repair - Regularly Updated and Very Detailed:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2020-03-20
This is a BIOS with grub-pc install.

But whether BIOS or UEFI, you always select a drive like sda, never a partition.
If you update partition boot sector it will never be used as BIOS systems only boot from MBR, not PBR. And then the version of grub in MBR is the old version and may not want to boot updated grub in your install.

With BIOS you should have correct settings for update.
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

#to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

