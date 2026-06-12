---
title: "grub rescue message after trying to install 11.10"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by eji767 on 2011-11-13
dear all

i am pretty new to linux and very happy with it, but still very much learning the ropes.

i have been running 11.04 alongside windows 7(which i had to keep for work stuff!) on an asus eee pc and just downloaded the pendrive installer to install v11.10 as i couldn't seem to access the software centre from ubuntu any more.

when i tried to boot my netbook from the usb, the grub rescue msg keeps coming up and now that's all i get.  i have tried looking really hard around the forums but can't seem to find an answer i understand on how to fix this! 

i apologise for my basic understanding level but would be hugely appreciative of any help at all to get ubuntu back up and running. 

many thanks

---

### Post by darkod on 2011-11-13
If you already have a working ubuntu installation (your 11.04 is still working right?), it's better to create usb sticks from ubuntu, not using the pendrive installer. I guess the pendrive installer messed something up while creating the boot process.

Do you have the downloaded ISO inside ubuntu or windows? If it's in windows it's better to move it into ubuntu.

Then just boot your 11.04 and use the Start Up Disk Creator. You select the ISO and the destination usb stick and that's it.

---

### Post by eji767 on 2011-11-13
hi there darkod

thanks for your reply.

as i said, i'm afraid my knowledge level is pretty basic. i used the start up disk creator and the 11.10 iso.

but when i tried to reboot from the usb, it came up with the :

error: file not found
grub rescue

prompt.

now that's all my computer shows, whether i boot with the usb in or not. i've tried changing the bootup priority in the bios but to no avail.

so i'm stuck at the grub rescue prompt and can't seem to get anything to work - windows or ubuntu.  any advice on how to either get out of or to fix grub rescue would be great.

thank you

---

### Post by darkod on 2011-11-13
If you can't boot windows nor ubuntu, or the usb stick, do you have another computer? Can you burn a CD from the ISO, or try making the usb stick again?

You need to boot the computer that has the error with either a cd or usb stick. Then from ubuntu live mode you can check the partitions on the hdd with:

sudo fdisk -lu (small L)

---

