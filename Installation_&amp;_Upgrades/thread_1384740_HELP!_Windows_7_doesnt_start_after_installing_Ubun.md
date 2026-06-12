---
title: "HELP! Windows 7 doesnt start after installing Ubuntu 9.10!"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by andreazana on 2010-01-18
I've installed Windows 7 on my new HP G60-243GL that came with Vista and 3GB of RAM. Then I decided to make partitions with Gparted and install Ubuntu 9.10. It's a 280 Gb HD, and I dedicated 30 GB to Ubuntu. I made there a Logical partition  of more or less 15 GB, and inside of it I made a 1 GB for swap and 14 GB for /home. I didn't made a /boot partition. Everything went fine, and I'm posting from Ubuntu. The problem is that know, when I pick Windows 7 on the grub, my computer loads the splash and then reboots. When I tried with the recovery partition (sda2, from the grub), it loads the Vista splash, and then reboots. I tried several times, and one of them the "recovery manager" loaded. It said something like: "The computer will reboot now. If the recovery process succeced, Windows will start normally. Otherwise, the recovery process will continue." After that, it rebooted, and grub appeared again, I picked Windows 7 and it loaded the splash, and rebooted AGAIN! I'm really frustrated because I wasn't able to make a dual boot succesfully, and I'm afraid that the same thing would happen again when I delete all the partitions from the Live CD, install Windows 7, install Ubuntu. 

Please, please help...

Oh yeah, and I tried booting from the CD, with the Windows 7 disk, and the grub loads, so I couldn't even repair...

---

### Post by tachuela on 2010-01-18
Start from scratch. Install Windows 7. Then allocate space for Ubuntu FROM Windows; Then install Ubuntu.

---

### Post by wilee-nilee on 2010-01-18
you might try in the terminal sudo update-grub

---

### Post by Sef on 2010-01-18
Applications > Accessories > Terminal

then copy and paste this code:

```
sudo fdisk -l
```

Then copy and paste the results here.

That code will show us what partitons you have and what is on them.

---

### Post by presence1960 on 2010-01-18
I need more info about your setup & boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by latenightrob on 2010-01-19
If you do decide to start from scratch, I followed this guide with no problems setting it up [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
 
good luck

---

### Post by PRC09 on 2010-01-19
Just a thought,when you finish re-sizing the windows partition reboot your machine to make sure Windows will still boot,before you continue with the ubuntu install.My reasoning for this is it is much easier to repair a windows bootloader at this point than after Ubuntu is installed.

---

