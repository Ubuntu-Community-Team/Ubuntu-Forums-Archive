---
title: "problem with LUBUNTU 13.04. on HP PAVILION ze5600 notebook"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by nikola2 on 2013-08-06
Hi there, I heard about Lubuntu, and i tried to install it on my HP notebook witch has 512mg of ram, 2.8 Intel CPU and 20GB HDD.
Originally i had a 40gb toshiba drive, and  Win XP sp1, but a virus destroyed the drive... So then i replaced it with a 20gb and installed Ubuntu 10.10

I downloaded Lubuntu from the Lubuntu [home site ]("http://www.lubuntu.net/tags/lubuntu-1304"). The problem appears when i try to burn the ISO image to a CD. On my hp notebook i tried to burn the iso to a CD with the built in burning program. When i select burning speed, it offers me Max speed and 24x  I selected 24x and waited...** "Burning complete, some files may be missing" **
I know that burning speed must bee minimum (better quality), but now i can't select other then max or 24 :/
Then i transfered the .iso file over my Flash memory to my other laptop and tried to burn it with PowerISO, but same situation (Speed max, or 24x), i also didn't manage to burn the disk properly :P 

I used a new CD in both cases. I have used PowerISO before to burn other iso files and i used the same CDs but now it's different and it doesn't work :(
I also tried to use the windows wizard for burning (i don't know what its called ) and a error comes out. Unable to burn CD. 

What am i suppose to do in order to solve the problem!? 
Thanks  (:

---

### Post by patspiper on 2013-08-06
Why don't you put the Ubuntu installer on the flash disk and boot from it? There is no need to burn the iso onto a CD.

---

### Post by nikola2 on 2013-08-06
Hi
I have already made a bootable USB drie, but i didn't manage to boot from USB. In my Bios, i have a option to boot from HDD, CD drive, or from a removable device. I set the removable device 1st, but i can boot in Lubuntu :P
i am currently running Lubuntu 13.04. but only as a "live disk"(no installation).
 When i run the install process either from the desktop, or the start up screen, i get a black screen and it stays like that for 3 hrs :/
Thanks for your reply :)

---

### Post by patspiper on 2013-08-06
IIRC, old PC's expect a floppy type (FDD) USB drive. I have a pretty vague recollection of a similar encounter where I had to use the dd command to copy the iso onto the USB flash disk to have the PC boot from it..

As for the black screen, try booting the CD is safe mode, and add the following to the boot line: acpi=force vga=791

---

### Post by nikola2 on 2013-08-06
My HP is i think from 2002 :/
Anyway, i will have to try this tomorrow because it is pretty late, and i have to get up early :P
I am not quite sure how to start safe mode with the CD and boot up properly, could you tell me :)

---

### Post by patspiper on 2013-08-06
From [https://help.ubuntu.com/community/BootOptions:](https://help.ubuntu.com/community/BootOptions:)

As the CD boots, you can gain access to the advanced page and its  options by pressing any key when the small logo appears at the bottom of the screen. Press F6 for other options and add 'acpi=force vga=791' at the end of the boot options line. Then press ENTER.

---

### Post by patspiper on 2013-08-06
Regarding the booting form USB, have a look at: [http://community.linuxmint.com/tutorial/view/744](http://community.linuxmint.com/tutorial/view/744)
The easiest way to do it is from the live CD. Open a terminal and type:
isohybrid ~/Desktop/myiso.iso
sudo dd if=~/Desktop/myiso.iso of=/dev/sdx oflag=direct  bs=1048576

where sdx is your flash disk (replace sdx and myiso.iso part). The first command makes the iso image a hybrid one (that can be installed on USB sticks), and the second copies the image to the USB disk.

WARNING: using dd with the wrong sdx may overwrite your hard disk with the iso. Make sure you understand the process before you start.

An enlightening page: [http://www.rm.com/Support/TechnicalArticle.asp?cref=TEC818956](http://www.rm.com/Support/TechnicalArticle.asp?cref=TEC818956)

---

### Post by nikola2 on 2013-08-07
I would rather try the live CD process, but honestly i don't get the "[COLOR=#000000][FONT=Ubuntubeta]_*where sdx is your flash disk (replace sdx and myiso.iso part). The first command makes the iso image a hybrid one (that can be installed on USB sticks), and the second copies the image to the USB disk.*_" part :/ And i'm not sure weather i can boot from USB drive :P 
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntubeta]
If you could just write me what am i suppose to put in the terminal, and press enter :) 
I know a lot about computers, but the problem is that i tried Ubuntu only 4 days ago, and now I'm trying out Lubuntu for the first time  and everything is quite confusing  :( 
I am assuming that the problem, with the CD burning, has something to do with the .iso  file, because i have earlier used the same computer, same CD brand, and a other .iso file, but i had the choice to pick the burning speed (from 4x to 24x )
What do you think about that?
The easiest way would be to burn the lubuntu13.04.iso file to a CD but with lowers speed :) [/FONT][/COLOR]

---

### Post by patspiper on 2013-08-07
1st of all, always check the md5 checksum of the downloaded iso with that on the download website to make sure the iso is intact. Ubuntu MD5 checksums can be found in:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Since you have the live CD up and running, copy your iso file to your home folder, then open a terminal (CTRL+ALT+T) and type:
```
cd ~
md5sum nameoftheiso.iso
```

and make sure the produced md5 checksum matches with what you have seen on the ubuntu website.

Then type:
```
sudo fdisk -l
```
which should list your disks. The USB flash disk will be something like /dev/sdb1. If that's the case, you use /dev/sdb (without the 1) in the command below.
```
isohybrid ~/nameoftheiso.iso
sudo dd if=~/nameoftheiso.iso of=/dev/sdb oflag=direct  bs=1048576
```

WARNING: Make sure you understand the commands as any mistake could result in your hard disk data being erased

---

### Post by patspiper on 2013-08-07
After posting above, I read that Ubuntu iso's are already hybrid ones. So there is no need for the isohybrid command.

Furthermore, instead of using dd command with its associated risks, you can install from the ubuntu software center usb-imagewriter which should be able to write the hybrid iso to the usb flashdisk, and has a GUI.

---

### Post by nikola2 on 2013-08-07
lubuntu@lubuntu:~$ md5sum lubuntu-13.04-desktop-i386.iso iso
md5sum: lubuntu-13.04-desktop-i386.iso: No such file or directory

I asked my friend to download and burn the lubuntu.iso  file... so we will see what happens :KS
I am not quite sure i understand the step with the bootable USB :neutral:  :?

---

### Post by patspiper on 2013-08-07
> **nikola2 said:**
> lubuntu@lubuntu:~$ md5sum lubuntu-13.04-desktop-i386.iso iso
md5sum: lubuntu-13.04-desktop-i386.iso: No such file or directory

Did you copy the iso file to the home folder?

On the other hand, you can compute the md5 checksum on Windows using:
[http://www.nullriver.com/downloads/Install-winMd5Sum.exe](http://www.nullriver.com/downloads/Install-winMd5Sum.exe)

or

[http://sinf.gr/en/hashcalc.html](http://sinf.gr/en/hashcalc.html)

---

