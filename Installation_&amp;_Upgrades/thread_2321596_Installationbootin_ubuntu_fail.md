---
title: "Installation\bootin ubuntu fail"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by bogdan-kushnir-gothfrid on 2016-04-23
i have strugulling for a few days with attemts to install ubuntu. 
problem core: 
  ubuntu liveCD (written on flashdrive, i don't have cd-rom) doesn't see my hard drive. only visible device is falshdrive itself.
what i have tried:
 1. fdisck in liveCD. result /dev/sda for my flash and hundreds of lines with smth like "ram0: 64k....."
 2. change harddrive partition table to mbr and to gpt. no result
3. qflashing\updating\factoryreseting BIOS 
 3. install ubuntu on differnt pc with my hard drive. installation went fine, but when i connect drive to my pc, it fails to boot with reason, that it can't find root. (i tried to declare root manualy, pressing e in grub and editing correct adress - no result)

year ago i have tried ubuntu on this exact pc and all was fine.

pc specs:  
  a10 processor
  gigabyte ga-f2a85x0up4 motherbord
  seagate 2TB SSHD

---

### Post by ajgreeny on 2016-04-23
I suspect this is a UEFI vs BIOS problem which is making the hard drive invisible for you.

Have a good read through the links at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you check the md5sum of the iso file you used to make the USB install medium?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by bogdan-kushnir-gothfrid on 2016-04-23
Ubuntu was downloaded directly from ubuntu official page.
After i look into provided links. I tried this thing.
1. Convert hdd to msdos table. Boot with legacy mod but Livecd doesnt detect hdd. Boot in uefi same result
2.  Tried same with gpt, also got nothing.
3.  Plug my harddrive in my old pc, installed ubuntu from same livecd and plug in hdd in my pc, again got "can't find root". Just from curiosity i came to my friend and try to boot with my hdd, all went fine.
So i suppose problem is with my bios, i just cant get what? Already tried all 3 availible versions.
Only thing that doesnt try, is to turn off security in bios. I just doesnt have that option(only "setup" and "system" avaliable).

---

