---
title: "Installed, but now I'm stuck HELP!!!!!!!!"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by l3acklash on 2012-09-08
Hey guys,
Look, I am the newest of the new to come to Ubuntu. I have drooled over ubuntu for YEARS, Just never really got around to doing anything with it. Anyways. I just recently installed ubuntu 12.04. It was working GREAT! well.. up until i rebooted my machine. Now im confused and don't know where to go. I would greatly appreciate any help that can be given.
 
Anyways, whenever I turn the machine on now, it wont detect my disk drive and sends me straight to this purple "GNU GRUB" screen (and yes i have gone through the bios and selected the disk drive to be my main boot drive.. still nothing) 
 
Heres a direct overlay of what im dealing with when at the purple "GNU GRUB" screen:
 
GNU GRUB
---------------------------------------------------------------------------------------------------
Ubuntu, with Linux 3.2.0-23- generic-pae
Ubuntu, with Linux 3.2.0-23- generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
--------------------------------------------------------------------------------------------------
 
Instinctively I select the first "Ubuntu, with Linux 3.2.0-23- generic-pae. That sends me to this command window:
 
mount: mounting /dev/disk/by-uuid/8ef68434-a383-41a0-bfb2-0e491648ca3a on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try pressing init= bootarg
 
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs)

---

### Post by darkod on 2012-09-08
Double check in BIOS if your disk is recognized correctly there or not. I am not talking about the device boot order, look whether the actual disk is recognized. If it doesn't exist in BIOS, it's like it's not there so there is nothing to boot.

If the disk is correctly in BIOS, when the grub2 boot menu shows, try pressing 'c' for command mode. At the prompt execute:
```
ls
```

Does that list the disk and partitions like (hd0),(hd0,1),(hd0,2), etc?

---

### Post by l3acklash on 2012-09-08
Thanks for trying to help, but i still don't understand what your talking about. My disk drive is located in the bios. And in the command prompt I typed in Code: gave me the error of "invalid command prompt"

Can you walk me through step by step?

---

### Post by l3acklash on 2012-09-08
Also, your image of the Code that im sopposed to type in isnt showing up. just says "is"

---

### Post by darkod on 2012-09-08
That is the command you need to type, just two letters. The smallcase LS, it's not is, it's ls.

---

### Post by arpanaut on 2012-09-08
No it is a ls small L
as in list.

oops, too slow

---

### Post by l3acklash on 2012-09-08
oh ahaha my bad :p Thanks for clearing that up. Yeah this is what i got:

grub> ls
(hd0) (hd0,msdos5) (hd0,msdos1)

---

### Post by darkod on 2012-09-08
OK. At that grub> prompt run these commands one by one and see if that boots it:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
linux vmlinuz root=/dev/sda1
initrd initrd.img
boot
```

If that works, we can try sorting out grub2.

---

### Post by l3acklash on 2012-09-08
everything works up until the: 

linux vmlinuz root=/dev/sda1

Command prompt, says: invalid filename "vmlinuz"

---

### Post by darkod on 2012-09-08
OK. Lets see what kernels do you have. If you can, copy paste, or write down, the output of:
```
ls (hd0,msdos1)/boot
```

That should show all kernels present in the /boot folder. We need to see what's there so that we know what to try to boot.

---

### Post by l3acklash on 2012-09-08
grub> ls (hd0,msdos1)/boot
grub/ System.map-3.2.0-23- generic-pae abi-3.2.0-23-generic-pae config-3.2.0-23-generic-pae memtest86+.bin memtest86+_multiboot.bin vmlinuz-3.2.0-23-generic-pae initrd.img-3.2.0-23-generic-pae

---

### Post by darkod on 2012-09-08
OK, modify these two commands:
```
linux /boot/vmlinuz-3.2.0-23-generic-pae root=/dev/sda1
initrd /boot/initrd.img-3.2.0-23-generic-pae
```

The rest of the commands are the same. See if that boots it.

---

### Post by l3acklash on 2012-09-08
Back to the same thing!! man, this is madening. It went through a slew commands by itself. than now im back to the start again..

---

### Post by l3acklash on 2012-09-08
I really, REALLY do not have the money to go out and purchase a new hard drive just because ubuntu has the hard drive locked basically. I've tried taking this hard drive out and putting it in another laptop that was working completly fine, nothing wrong and i have the same problem. I put even a windows dvd in the drive to see if it would would load the installation so i could wipe the drive through the windows installation and start from scratch. But to no avail. Disk drive that worked perfectly fine in that laptop wont be recognised since i put the hard drive in. but now i put it back in the original laptop that i started with. and here i am.

---

### Post by darkod on 2012-09-08
> **l3acklash said:**
> Back to the same thing!! man, this is madening. It went through a slew commands by itself. than now im back to the start again..

Are you sure it's correctly installed? If I understand your first post correctly, it only worked once after the install and after the first reboot it stopped working right away?

So far from the command you ran at the grub> prompt it looks like it detected the partitions and kernel files correctly. It should have booted successfully, under the assumption the system is actually fully and correctly installed.

You might wanna try a new fresh install at this point. I don't know what else to try since you seem to be sure the disk is working OK but on the other hand it doesn't work in another machine too. Can this be some issue with the disk?

---

### Post by l3acklash on 2012-09-08
Thats the thing man. I would have done a fresh install looong ago if i could. I can't even access the desktop. Once I hit the power button it takes me directly to the Grub screen. Like I said, I put the disk in the drive, the drive is located in the bios, so it should load up, right? yeah, nothin. takes me directly to the purple grub screen. I don't know where to go from here. If there was a way to delete the install through the command prompt without damaging the hard disk i would just so i can get passed the grub screen.

---

### Post by l3acklash on 2012-09-08
I guess I misinterpretted what I said about the hard disk. I meant to say that It's locked up and i can't get past the grub screen even if i take it out and put it in another laptop that has a completly fine and working disk drive. So obviously the disk drives work, it seems like this Grub screen has the whole computer on lockdown sort of thing, and won't let the disk drives run.

---

### Post by l3acklash on 2012-09-08
can you think of a way to make the disk drive run through command prompt? is there a command?

---

### Post by darkod on 2012-09-09
OK, hold on, I'm starting to lose you. :)

Option 1. Lets do a new clean install. If you try to boot the computer with the cd-rom, can it boot the installer? It should, regardless what's on the hdd because when booting from cd-rom only the cd matters. Then you can do a new install.

Option 2. If nothing else works, and you are happy deleting all data on this disk, just connect it to another computer as a second disk (don't replace the main one), boot the OS, and delete all partitions on the disk which has the problems. That shouldn't lock the computer since you are running it from its own disk and OS. If it does lock it, it might be related to hardware issues with the disk that has the problems.

I have had a case like that, the disk looks normal until you try to access it and then locks out and starts missing. It was broken.

---

### Post by l3acklash on 2012-09-09
Haha, good thing I'm talkin to you eh? I completly forgot i could through the hdd into my computer and wipe the drive that way. Buut, now I have another (smaller, probably quicker) fix. So I popped the drive into my computer, formatted it. deleted every partition that was visible. And STILL when i throw it back into my laptop I got this message. 

error: unknown filesystem
grub rescue>


P.s, I don't own a mac, all of my computers are PC's. And I formatted the drive through windows disk management. but after the format (my drive is 500 gigs) theres still 104 megs left of used space that I can't manage to delete. Am I doing something wrong?

---

### Post by l3acklash on 2012-09-09
Damnit, I guess the disk drive is messed up or something, because even without the hard drive in the laptop it should STILL run the installer off the disk. I'm confused though, because when I power the laptop on, you can distinctively hear the laser head reposition itself. You know.. that distinct sound any disk drive makes for the first second when you power a computer on than goes away. Yeah, that sound. I can hear that. But when I put a disk in the drive and close it, and try restarting it, nothing shows up! Just that stupid black screen with that blinking curser at the top left!

---

### Post by PyroSamurai on 2012-10-10
Burn a new CD and try to reinstall. It might be that the CD you use was or has gone bad. Also don't forget to check the BIOS setup. The option might not be shown when you boot but it is still there. Try the new CD first though.

---

