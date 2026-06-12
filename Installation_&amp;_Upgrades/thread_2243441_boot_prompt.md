---
title: "boot prompt"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by garrett8 on 2014-09-08
hi, im relitivly new and downloaded Ubuntu onto a blank drive, but on startup, the BIOS prompts me to press F1 to boot or F2 to go to setup, it gets kinda annoying, is there a way to fix this? if so how?

---

### Post by grahammechanical on 2014-09-08
Please confirm that by "downloaded Ubuntu to a blank drive" you actually mean that you installed Ubuntu on a blank hard disk.

This is most likely a problem with your BIOS/UEFI boot system. And without more information about your machine there is nothing that can be said that even comes up to the standard of a guess.

How many hard disks? Is there another operating system installed? What happens if you press F1 to boot? Does Ubuntu Boot? What happens if you do nothing? Does Ubuntu load? Have you set the BIOS/UEFI boot system priority to load an operating system from the disk with Ubuntu on? .

On my machine I get a message informing me of the key to press if I want to enter the BIOS set up program. There is an option in my BIOS set up program to disable the showing of that message. I have no idea if this is what you are talking about.

Regards.

---

### Post by LostFarmer on 2014-09-08
Make/Model of computer ?   That error is normally due to a bios setup error.  If a desktop (laptop ?) , I would check the clock time and date, if it is wrong it points to the bios battery is dead.

---

### Post by garrett8 on 2014-09-10
ok like i said im completely new to this so ill start from the begining
i originally booted from a flashdrive, I coppied the os to the computer (there are no other operating systems on this thing) and downloaded it to a hard disk (there are a total of two) from there the boot to ubuntu was a success so i played around and then updated, restarted my desktop pc and it gave me a bios prompt like this:

floppy diskete seek failure
serial ATA dive 1 not found
press F1 to continue, F2 to enter setup

when F1 is pressed it takes me to ubuntus grub and loads the OS

heres the model:
Dimension 3100/E31

many thanks for the chance to learn

---

### Post by Vladlenin5000 on 2014-09-11
Apparently it's looking for drive that's no longer there:
```
[COLOR=#000000]serial ATA dive 1 not found[/COLOR]
```

Please check at BIOS setup whether or not the drive where you installed Ubuntu - not downloaded - is still recognized.

---

### Post by garrett8 on 2014-09-11
ok, well thats my fault, i do know a little about computers and removed a few things that weren't available in the boot sequence, i didnt however remove any missing drives. so its all fixed now, thanks for all the help!

---

