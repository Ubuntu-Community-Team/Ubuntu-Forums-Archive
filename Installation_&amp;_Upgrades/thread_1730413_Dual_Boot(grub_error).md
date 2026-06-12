---
title: "Dual Boot(grub error)"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by bitsonhj on 2011-04-16
hey guys.

i am still using the 10.04 LTS version of ubuntu and i have decided to install Windows 7 to my hardisk.

After installation of win 7 ,i boot ubuntu form its CD to install GRUB. After following the first two tutorial on this website 
```
https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands
``` ,
i got this error(for both different way of installing GRUB),  check image ---->

```
http://i277.photobucket.com/albums/kk47/bitsonhj/Screenshot-2-1.png?t=1302935141
```tips** :zoom in the image to see better.

If you would like to help me with another way,please explain it to me in details.

My laptop specs :  2GB intel celeron ,533Mhz FSB ,1mb(L2 cache) , 2GB DDR2 , 320 GB SATA HDD.

ok,thanks for replying in advance :p

Soory if i have posted in the wrong section.

---

### Post by garvinrick4 on 2011-04-16
Use your Live Cd to install grub2: You will need your sda# for your linux install.
```
sudo fdisk -l
```
:that is a lower case L:
#Only a couple of commands are in links below.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

Once you get into your Ubuntu install run:
```
sudo update-grub
```
To get both your linux and windows in grub menu entry:

---

### Post by bitsonhj on 2011-04-16
thanks for replying ,but unfortunately after following the first tutorial on this website ```
http://ubuntuforums.org/showthread.php?t=1014708
```   ,it is still not working,getting the same error.
I have found that those using vmware get this error ,but i am not using any virtual machine.

Anyway, awaiting more replies from you.

Thanks for replying in advance!! :p

---

### Post by Rubi1200 on 2011-04-16
Rather than playing guessing games about the current state of your setup, I highly recommend you run the following diagnostic script and post the results here:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tomski on 2011-04-16
had to deal with 2 re-install's of grub 2 & in both instances i had success by following the chroot method:

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

---

