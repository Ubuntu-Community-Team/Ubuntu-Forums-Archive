---
title: "Help! dual boot problem"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by PimpinMonkey247 on 2010-01-20
I just recently installed Ubuntu 9.10 netbook remix and im loving it. But when i installed it the windows 7 Partition no longer works. I can see the windows 7 partition but when i click on it, it just reloads the grub boot loader. Im in college and need the windows 7 partition. Someone please help me, Also if it helps im using a acer d250 netbook. Any questions just ask. Sorry if its been posted or im in the wrong section.

---

### Post by lidex on 2010-01-20
Grub probably overwrote your windows bootloader. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by presence1960 on 2010-01-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2010-01-20
> **lidex said:**
> Grub probably overwrote your windows bootloader. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

well of course GRUB overwrote the windows bootloader on MBR- how else is the GRUB menu going to take over at boot?

---

### Post by PimpinMonkey247 on 2010-01-20
Thanks to everybody replying so quick. I have read to use the windows 7 cd. But im on a netbook with no cd drive and just got it dont want to buy a drive right away. Is there any other method to boot into the windows 7 partition

---

### Post by presence1960 on 2010-01-20
> **PimpinMonkey247 said:**
> Thanks to everybody replying so quick. I have read to use the windows 7 cd. But im on a netbook with no cd drive and just got it dont want to buy a drive right away. Is there any other method to boot into the windows 7 partition

run the script so we can see exactly what you have prior to making any suggestions. I for one will not issue suggestions without seeing exactly what the problem is.

---

