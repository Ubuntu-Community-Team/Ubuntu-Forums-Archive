---
title: "PC Reboot Error after 10.04 Ubuntu Install"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by kamalpalei on 2011-02-16
Hi All
I have a PC with below configuration.

cpu intel core i5 650 boxed 3.2 ghz socket 1156
MB intel P55 Chipset DH55P J Boxed
HDD WD SATA 2Tb 64MB cache
&#12288;
&#12288;I installed "ubuntu-10.04.1-desktop-amd64.iso", and looks grub2 is not installed properly. I do not see all the files in grub install folder.

Please let me know, ubuntu-10.04.1-desktop-amd64.iso is the right installable or not.
If it is right one, how to re-install grub2 properly.

Regards,Kamal

---

### Post by Rubi1200 on 2011-02-16
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

