---
title: "Windows Recovery = Ubuntu gone"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Microsoft Hater on 2011-01-30
Hi all,

I just reformatted my c: partition with my d: windows recovery drive, and now I lost ubuntu on sdb3. 

I used the live usb to try and see what's going on; the ext partitions still remain, and windows recognizes it's appropriate drive size. 

How do I get back into Ubuntu? There is no grub, no anything...

Any and all help is extremely appreciated.

---

### Post by howefield on 2011-01-30
Windows prefers to think it is the only operating system on the disk, so will have overwritten your grub menu with its own.

You will need to reinstall grub, but the instructions may differ depending on the version of Ubuntu you are running ?

---

### Post by Rubi1200 on 2011-01-30
To reinstall GRUB we need a better look at your current setup.

To that end, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

