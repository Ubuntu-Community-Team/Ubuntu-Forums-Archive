---
title: "Screen shut down after &quot;try ubuntu&quot;, maybe UEFI problem"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by robert72 on 2014-03-17
So I'm trying to create an USB bootable Ubuntu to have the possibility to work on the same environment but on 2 differents computers. I tryed Ubuntu 13.10 and 13.04 on a 32Gb USB key installed with Unebootin and Universal-USB-Installer.
When I restart my computer (an HP ENVY 17 on windows 8) i switch to an ubuntu grub and when i select "try ubuntu" the screen turn off but the computer is still on. I tried the USB with Ubuntu 13.10 installed with Universal-USB-Installer on my other computer that i made myself (it have an Asus motherboard). Here in the boot mode i can select :
-USB Hard Drive (UEFI) - Lexar JumpDrive
-USB Hard Drive - Lexar JumpDrive
When i select the UEFI one it's the same as on my HP but when i select the one without UEFI it launch Ubuntu. The problem is that on my HP i can't select the one without UEFI, it doesn't appear inthe list.
An other question is, is it a good solution for what I search : a full working Ubuntu OS on an USB key to work on many computers with only one environment ?

---

### Post by fantab on 2014-03-17
When Ubuntu installs (for that matter any OS) it installs according to the Hardware present on the computer. So if there is different hardware, especially Graphics cards, on the 'other' computer then the USB install will NOT work, as the Ubuntu install is not configured to run with different Hardware.

On the other hand, Live Ubuntu can work on any computer but is slower than the 'installed' Ubuntu.

So if you want Ubuntu to run on multiple computers from USB then probable solution is to 'Burn' the .iso with 'persistence'.
[URL="https://help.ubuntu.com/community/LiveCD/Persistence"]https://help.ubuntu.com/community/LiveCD/Persistence
[/URL]

---

### Post by robert72 on 2014-03-18
Thanks for this tuto, I think this is the closer we can go but it's not really what i had in mind. I whant to use the GPU too, so i think I'll make a Ubuntu parition on both computer and install all in both.
Now the problem is that I can't install Ubunutu on my HP ENVY. I had burn a live CD of Ubuntu 13.10, when the computer boot on the CD there is an error print for less than 1 seconde :
Could not open "\EFI\BOOT\fallback.efi" : 14
error: variable `root' isn't set
And then it go to a GNU GRUB version 2.00-19ubuntu2 where i can select : Try Ubunutu, Install Ubuntu, OEM install, Check disc. When i select Try or Install the screen shut down but the computer still work.
When i try the same LiveCD on my other computer there is only this error : error: variable `root' isn't set. And then it go on the same grub but here if i select try or install, the screen stay on and i can try or install.
What can I do to Install Ubuntu on my HP while the screen turn off ?

EDIT : I tried to connect a TV in HDMI to my computer and when the screen of my computer turn off, the screen of the TV turn on with the Ubuntu waiter, after 2 minutes the screen off the TV turn off and the CD player stop turning the CD.
EDIT 2: After 10 minutes I unpluged the HDMI and this appear on my laptop screen :

[[img]http://s4.postimg.org/kzli3eyyh/20140318_103122.jpg[/img]](http://postimg.org/image/kzli3eyyh/)

---

### Post by fantab on 2014-03-18
Installing on both the computers is an excellent idea.
It is possible that the ubuntu.iso didn't BURN properly to the USB. Burn again after checking the [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") to determine the integrity of the downloaded .iso. If the sums don't match then re-download ubuntu.iso.

Installing Ubuntu on a 'EFI' machine is slightly different from installing on 'BIOS' system. On a UEFI computer boot ubuntu in EFI mode only.
More Info:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also search this forum with your machine model... 

Some Graphic cards need the '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")' kernel option and work in 'failsafe graphics' untill you install Ubuntu and the necessary graphic drivers.

---

### Post by archcynic on 2014-03-18
I installed Xubuntu on a HP Envy 17 myself at the weekend. After the 'grub' selection to 'try ubuntu' (or install) the screen went black. You will be surprised to hear that the install screen is being presented to you but with 0 [Zero] brightness. If you increase brightness (F3) a few times the install screen will become visible. (Thanks to other forum members for spotting that 'feature')

---

### Post by oldfred on 2014-03-18
There is a bug report and some suggested work arounds.
 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

---

### Post by robert72 on 2014-03-19
Thanks archcynic, you were right, i could increase the brightness of the screen to see Ubuntu and the five orange dot blinking but after 5 minutes all five dots stay orange and then the screen turn black. At this point i couldn't change the brightness with F2 or F3 but the computer is still on.

---

