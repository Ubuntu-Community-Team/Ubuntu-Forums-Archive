---
title: "Grub not showing Windows 7"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Beowulf.1000 on 2010-03-06
EDIT: Solved. 

Can anybody help me get Grub2 (Ubuntu 9.10) to show my Windows 7 partition so I can boot that? Also, most of the time during boot i just see "GRUB LOADING" and no list of options to choose for booting whatsoever-- making it impossible to even have a choice to boot into Windows, if I can ever get Windows to show up in the Grub listing.

I have a PC, had sda and sdb sata drives, Win7 on sda on first partition. I just installed Ubuntu to an IDE (ATA) drive that I added in order to get it to install. I told ubuntu to put grub on the IDE drive, which it did. Then I changed my BIOS boot order to boot the IDE drive first, so GRUB would show up, which it does. 

But I have no option at this point to boot back into my Win7, short of going to the BIOS and having it boot sda again as the first drive. I need to get grub to boot Win7.

Geez. I used to know GRUB pretty good, now apparently it is GRUB2, everything has changed, I can't just go into a text file and change grub like I used to. 

Maybe Windows AND Ubuntu should quit messing with things so much! Give us users time to just fricken use and enjoy the OS.
 Beowulf

---

### Post by presence1960 on 2010-03-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

