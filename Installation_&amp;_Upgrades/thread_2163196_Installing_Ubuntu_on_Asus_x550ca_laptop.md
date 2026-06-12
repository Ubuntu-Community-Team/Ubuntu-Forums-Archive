---
title: "Installing Ubuntu on Asus x550ca laptop"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by Roranicus on 2013-07-17
Hey there, totally new to Linux here. I recently got this laptop [http://www.asus.com/ca-en/Notebooks_Ultrabooks/X550CA/#specifications](http://www.asus.com/ca-en/Notebooks_Ultrabooks/X550CA/#specifications)

It took me about 10 seconds look at Windows 8 to realize it's finally time to try out Ubuntu, something I've been meaning to do for years. I've been trying to install the 13.4 version yesterday, both from a disk and a flash drive and it just won't recognize them when booting. I did disable secure boot control in the bios, so the issue isn't there. I haven't found a legacy boot option, and I heard it's not always there. I also am using the 64 bit version, as I know the 32 bit version straight up wouldn't work. 

I was hoping to dual boot, after I've been advised to do so just in case some software I need to run will only run on Windows. Initially I wanted to format and stick with Ubuntu. That option is still open if dual booting is too much of a hastle but I would like to know if it's safe to do so on this particular machine first. It's still possible for me to return it and get a different, more linux friendly laptop. 

Thanks in advance.

---

### Post by dino99 on 2013-07-17
Doc to fight with UEFI : [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

how to do a standard ubuntu install: [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by oldfred on 2013-07-17
A lot of Asus users have had differnt results and difficulties. Only the K55N seems to not work in UEFI mode, but only in BIOS mode which makes dual booting extremely difficult as you have to go into UEFI/BIOS each time and turn it on of off.

   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)
Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

---

### Post by Roranicus on 2013-07-17
Thanks guys. I managed to start the install. I do have other bugs but tbh, I'm too tired to worry about it at this point. Turned out legacy boot was called csm boot in my bios. Switching that on allowed me to boot from usb.

---

