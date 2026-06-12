---
title: "problems installing to usb hard drive (grub issues)"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by jerome bettis on 2005-07-17
hi

well the hard drive in my laptop is making pretty bad noises so i figure it's on it's way out sometime soon.  i have a 120 gig usb drive which has a backup of everything, and i'd like to install linux on it so i can still work while i'm waiting on a new drive.

i have managed so far to get ubuntu installed on a 10 gig partition at the beginning of the drive, and it boots.  i turn the computer on with the drive plugged in, and the copy of grub that is on the usb drive loads and i can sort of boot into the kernel.  however i don't get very far because it doesn't have the usb stuff load right away - i can fix this later.

right now the problem is when i installed grub onto the usb drive, it messes up the copy that is on the laptops hd.  if i boot without the drive plugged in, it says "grub loading stage 1.5 ... error 21"  so i've tried reinstalling grub on this drive, then when i reboot without the usb drive in i can boot of the regular hd.  but when i plug it in it just goes to the laptops drive.   ](*,)  make sense?  if not i can explain better.

i've tried using dd to copy the mbr on both drives and the copying /boot directory when each drive is booting correctly but no dice, the same thing happens after i've replaced the non working stuff with the old copy.

does anybody know what's going on and what i'm doing wrong?  i know this is possible.  right now i have the usb drive bootable and i've just added a menu option to cross over to the laptops hd and boot that copy of ubuntu.  this is fine i guess, but it would be nice to be able to turn this thing on without needing that usb drive to boot.  the order in my bios is: 1. usb 2. cdrom 3. hd 4. network

thanks for any help

---

### Post by dave9191 on 2005-07-17
Can you set the boot order of the drives in bios to have it boot from a usb hdd first. That way it will read the mbr on your usb one and boot from that, and if its not there, then resort to the one inside the machine. 

Dave

---

### Post by jerome bettis on 2005-07-17
yeah as i said the order in the bios is 1. usb 2. cd 3. hd 4. network

i still have no idea what i'm doing wrong ....

---

### Post by dave9191 on 2005-07-17
damn, i hate when people do that and suggest something in a reply that you already put in the first post, and i just did that myself. sorry. 

If you have a /boot on each drive and a mbr using each /boot respectivly, and that boot order then if the usb drive is plugged in it would boot from that and without it it should boot from the hdd. Try to install grub into the mbr on the usb hdd, and then intsall it on the laptop hdd with the usb drive unplugged. 

Dave

---

### Post by jerome bettis on 2005-07-17
yeah that's exactly what should happen but it doesn't.  i've tried doing exactly what you said but something goes wrong.  if i install grub without the usb drive plugged in, the internal drive boots fine.  but then when i plug the usb one back in it just goes straight to the hard drive.  if i install grub on the usb drive, it will boot but then when i unplug it the error 21 happens.

i'm still not sure what the hell's going on.

---

### Post by dave9191 on 2005-07-17
I think that error 21 means that the disk hasnt been found. In theory all of this should work fine, but Ive never tried to put into practice. Maybe someone else can help. 

Dave

---

### Post by Lax D Unit on 2005-07-18
hey man if u look up y post im haveing the same problem... i still dont know how to fix it. what im gonna try doing is disconnecting my master drive re hook up the slave drive as master and see what that does... (crosses fingers hopeing not to lose another drive) ill let you guys kno how that turns out... another thing that i tried to do was install lilo because that is what i used when i had a straight debian copy of linux and that seem to work fine. but for some reason it kept saying that it failed to install?? hmmm...

---

### Post by jerome bettis on 2005-07-18
well i think my bios doesn't boot from usb, at least not from this drive.  i tried the drive plugged into another computer and it booted nicely.  and when i unplugged it, the internal drive booted just like it should.  

it seems that when i had the usb drive "booting" over here it was really reading the mbr of the internal hard drive, which then just told it to boot from (hd1).  i think this is true because the knoppix cd would boot before the drive, when it should have happened after.  also if the drive was unplugged, i would see grub loading stage 1.5 (on the mbr of the internal drive) then error 21 (hd1 not found).  sound logical?

i can work around this, i just boot into the knoppix cd, press c when grub comes up and type
rootnoverify (hd1,4)
chainloader +1

to load the grub that's on the usb drive, as if i booted from it in the first place.  right now i have this as an option on the internal drive and i can boot from it just fine.  a slight headache but i can deal with it.  nice to know when this internal drive blows up (any minute now lol) it will be like nothing happened.

thanks for your help dave.

lax D unit, check the order of your devices and if the usb drive is first but a cd boots before it anyway you're probably having the same problem with the bios.  or grub isn't installed right, you can check this by doing what i said above in the grub shell.  good luck.

also for the record, after you successfully get the usb drive to boot, that's only half the battle.  it won't really do anything since the root filesystem needs the usb stuff loaded to get mounted.  

[http://www.ubuntuforums.org/showthread.php?t=20522](http://www.ubuntuforums.org/showthread.php?t=20522) the second guy in the thread explains it pretty well.  although in my case using the ubuntu install cd was not necessary.  i just chrooted into the usb installation from the one i'm in right now.  also i added ohci_hcd, scsi_mod, sd_mod, sbp2, and usb_storage to the modules file just for good measure.

i'm not sure why right now but when i tried making the initrd for the kernel i've made for this machine it wouldn't work.  but when i used the 2.6.10-4-386 one on the hoary cd it worked, and i'm done messing with this.

---

### Post by dave9191 on 2005-07-18
Well at least you got it work one way or another :) Why didnt I think that you bios might not support booting from a usb hdd. Oh well. Glad you got it sorted. 

Dave

---

