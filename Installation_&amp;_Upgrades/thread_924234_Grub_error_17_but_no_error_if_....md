---
title: "Grub error 17 but no error if ..."
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by dkalasz on 2008-09-19
hello,

I have been trying things from all over the place and have come up empty as far as a solution that works.. plenty of answers just not the right ones for me. anyway here we go with the problem

I have vista 32 installed on the first HD and ubuntu installed on the second both are working and i CAN log into them but only if i have a bootable cd in the cd drive that gives you the "press any key to boot from cd" message if i get this and wait through the message it goes to grub no problems and works fine. Now if i try to let it boot normaly it will get to grub and give me the following

Grub loading stage1.5

Grub loading, please wait

error 17


and at this point a reboot is your only choice.

I have yanked linux and redone my mbr so that windows booted properly again and reformated reinstalled and tried a multitude of other things that have been posted to no avail. 

any suggestions? thanks in advance

Dave

---

### Post by caljohnsmith on 2008-09-19
Sounds like it could be a problem with your BIOS settings. How do you have your HDDs configured in BIOS? Are they set for "auto", "LBA", "RAID", etc? 

Just to make sure that Grub is properly installed to the MBR of your Ubuntu drive, boot your Live CD and try:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes.

---

### Post by dkalasz on 2008-09-19
I've tried what you mention it seems to work but doesnt make a difference allthough when i go into grub it has a message about not recognizing a signature.. i'll have to run it again to get the exact line. and as for my hard drives there set to auto. is there a preference for linux? anyways thanks for your help

---

### Post by dkalasz on 2008-09-19
alright some more information for the stew.. first the onomaly i get when I go through the grub sequence is a message right after i enter the grub command it states " unknown partition table signature" no idea if this is because i have vista or whether its a real problem. now on to what i tried

i switched my hds's to lba in the bios .. no change
I switch the linux drive to boot first now here was an interesting change i got all the way into grub but when i tried to load linux i got an error 17 and a msg saying it was unable to load the drive. and when i tried windows i got a msg that the there was something wrong with the exe.. sorry i didnt write it down.. duplicateable though if it is pertinant . switching it back and booting with the dvd in the drive is still the only way grub works to actually load either operating system.

i will add anything I get .

thank you

dave

---

### Post by caljohnsmith on 2008-09-19
> **dkalasz said:**
> 
I switch the linux drive to boot first now here was an interesting change i got all the way into grub but when i tried to load linux i got an error 17 and a msg saying it was unable to load the drive.
OK, if you can boot your Linux drive, get a Grub menu, but get an error 17 when trying to boot Ubuntu, maybe all you will have to do is modify your Grub's menu.lst to make things work; but I'm still suspicious of something hardware related. 

So as long as you can boot Ubuntu while using your bootable CD approach, boot into Ubuntu and post the contents of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
That will probably give us enough info to help you get Grub working again.

---

