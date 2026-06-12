---
title: "Ubuntu 10.10 Dual booting problem"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by spnoe on 2011-02-18
I have Windows 7 on my hard disk and decided to dual boot with Ubuntu 10.10. I have installed this previously and not had a problem. However, this time Windows 7 is not showing up in the boot list sda. It is on the hard disk, I have checked using GParted. I have tried various fixes but nothing has worked.

On the partition it shows /dev/sda1 as ntfs System Reserved used 100 MIB
                          /dev/sda2 ntfs 515 Gib             "   104.77 GIB
                          /dev/sda3 extended 415.47 Gib      -
                          /dev/sda5 ext4                      "   10.54 GIB 

In the GParted at the top of the window where it shows the three partitions the box on the left /dev/sda2            on the right /dev/sda5
                       515.84 Gib                     415.57 GiB

Could someone advise me on how I can get Grub to recognise Windows 7.

I did try to reinstall Ubuntu and I put the Grub /  but this made no difference.

As you see I am not very experienced in the workings of Ubuntu.

Help gratefully received

Steve

---

### Post by Rubi1200 on 2011-02-18
Hi,
to help us get a better overview of the current situation, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

