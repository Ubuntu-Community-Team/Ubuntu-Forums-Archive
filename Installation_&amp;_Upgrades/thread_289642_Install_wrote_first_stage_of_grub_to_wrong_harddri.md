---
title: "Install wrote first stage of grub to wrong harddrive MBR"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Zaz on 2006-10-31
Main problem, short story:

I want to have ubuntu installed on my external USB harddrive, so that if the external drive is inserted, ubuntu will boot, and if it isnt inserted, windows xp (installed on the computer's normal harddrive) will boot.

When I tried to do this, the installer wrote the first stage of grub to the MBR on the internal harddrive, but the rest of grub (i think) to the external harddrive.

How do I fix this?

--------------

Long story:

I tried to install ubuntu 6.10 for 64-bit processors on my Acer Ferrari 3400.
...or rather, since i didn't want to change the operating system already running on the computer, i tried - and succeded - to install ubuntu to my 14 Gb USB2 external hard drive / mp3-player(a philips hdd100).
Both these harddrives are recognized by bios during boot.

The procedure was as follows:
I booted from the 6.10-64bit desktop version live CD, and started the installer, chose my name, password, location and all those other things you are asked during the install.
Then it asked me if I wanted to install to the internal harddrive, the external harddrive, or some other option I cant remember(something about longest empty space). I chose to install to the external drive, pressed next and ok a few times, and it started installing.

Now when I boot with the USB-drive connected the following happens: Grub loads, and displays the different choices for operating systems; ubuntu, ubuntu safemode,ubuntu memtest and windows xp.. Perfect.
But if I remove the external harddrive/USB-drive, grub tries to load, then gives me the error 21 (or something, it doesnt find the rest of the stages anyway), This is obviously not what I wanted.
I suspect, as stated above, that grub installed stage one to the wrong MBR.

When I boot windows, everything looks good, and all my partitions are working, will they still do that if I run some kind of 'restore MBR' utility?

Can I repair the internal HD MBR to boot only windows xp?

Can I repair the external HD MBR to boot grub or only ubuntu?

Can I do these repairs without destroying the already existing partitions on the internal HD.

Is this the right forum to post these questions in?
(If not, does anyone have any helpful links?)

---

### Post by daou on 2006-10-31
The surest way to separate boot managers and force GRUB on a single hdd is to disconnect or disable all other hdds from BIOS. I dual boot with WinXP and Ubuntu, both have own MBRs on their respective hdds. This means neither is dependent on the other.

---

### Post by Zaz on 2006-10-31
Yes, of course... but this computer is a laptop. It's rather complicated to remove the harddrive, even temporarily.

---

### Post by daou on 2006-10-31
Can you disable a harddrive from BIOS on the laptop?

---

### Post by Zaz on 2006-10-31
I probably can, but even if I could, the internal drive MBR is already contaminated with grub. :b

---

### Post by daou on 2006-10-31
Remove the USB drive. To fix the MBR on XP hdd,

a) Reboot with the XP CD and run the Recovery Console
b) Run fixmbr
c) Run fixboot
d) Reboot and then Windows should load fine

Then you disable the internal hdd, plug in the USB drive, and use the following guide to install GRUB on your USB drive:

[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Zaz on 2006-10-31
<3

But can I be sure that fixmbr won't delete the partitions on the internal harddrive?
All I could find out from microsofts website was that I would probably get a warning if that was about to happen.

---

### Post by devils_casper on 2006-10-31
fixmbr will fix Master Boot Record only. dont worry !  go ahead. its very easy to re-install GRUB in external drive. first fix internal drive and post back...



casper

---

### Post by daou on 2006-10-31
Microsoft's note about fixmbr is just about covering their backsides just in case something goes wrong. I've used fixmbr and nothing besides fixing MBR happened.

---

### Post by rmjokers on 2006-10-31
Just to be safe, you can always look at the current partitioning scheme with fdisk and write down the start / end sectors for each partition.  That way if something screws up the partitions, you can just restore them with fdisk.  Remember that a partitioner doesnt write anything in the partitions, it just writes a new layout in the MBR which is the first sector of the hard drive (outside of the filesystems).

---

### Post by devils_casper on 2006-10-31
[QUOTE=rmjokers]Just to be safe, you can always look at the current partitioning scheme with fdisk and write down the start / end sectors for each partition. That way if something screws up the partitions, you can just restore them with fdisk. Remember that a partitioner doesnt write anything in the partitions, it just writes a new layout in the MBR which is the first sector of the hard drive (outside of the filesystems).[/QUOTE]

why are you suggesting all this? it doesn't make any sense. did you find any problem with fixmbr ? 




casper

---

### Post by rmjokers on 2006-10-31
I am just suggesting precautionary measures one might take if they are really concerned about their data.  I also wanted to make it clear that the microsoft FIXMBR utility never actually destroys any data on the drive, only the boot loader program at the beginning of the first sector of the drive and the partitioning information itself which resides in an array at the end of the first sector of the drive.  As long as you keep these numbers around, you can install whatever boot loader you like and make sure that the numbers are restored afterward.  Its not necessary unless you are paranoid like me...

---

### Post by Zaz on 2006-10-31
Yes, fixmbr did the trick and repaired the mbr back to pre-grub status.
However, I've also discovered that the computers bios doesn't allow for disabling the internal hard-drive.

I now wonder how to install grub on the external drive only.
The current installation will boot to the menu which allows for choosing os, but whichever os I choose it says Error 17: Could not mount filesystem. (Except for windows, which is 'unrecognizable')

---

### Post by daou on 2006-10-31
It's a tough cookie if you have no way of disabling the other hdd because your BIOS is apparently set to boot from it first, and there is probably no way to change it. What I believe happens is that GRUB sees that the computer boots off the internal hdd first, and that is why it writes over the internal hdd's MBR.

What needs to be done is getting GRUB to write to the internal hdd MBR and all its boot files to the internal hdd as well. If I remember correctly, you can tell GRUB to install itself to a certain hdd. You can install GRUB from the LiveCD.

What this means you won't be able to boot the Ubuntu from the external hdd with another computer, only with the laptop you are using.

Check this howto on installing GRUB (it shows you how to tell GRUB where to install itself): [http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by Kerry Lange on 2006-10-31
> **daou said:**
> The surest way to separate boot managers and force GRUB on a single hdd is to disconnect or disable all other hdds from BIOS. I dual boot with WinXP and Ubuntu, both have own MBRs on their respective hdds. This means neither is dependent on the other.

Disconnecting your other drives, installing Ubuntu, then reconnecting your other drives does not necessarily work.  I tried doing this because I was having problems with Grub messing up my XP drive MBR.

When I disconnected my other drives, the install went well and I was able to boot to the single drive where I'd installed Ubuntu.  However, once I reconnected my other drives Grub lost track of where everything is and I ended up with a shell prompt instead of booting to Ubuntu.

---

### Post by daou on 2006-10-31
> When I disconnected my other drives, the install went well and I was able to boot to the single drive where I'd installed Ubuntu. However, once I reconnected my other drives Grub lost track of where everything is and I ended up with a shell prompt instead of booting to Ubuntu.

Probably what happened was that your drive order got rearranged when plugging in additional harddrives. Instead of a drive being hda (or sda) it suddenly became hdb. All that needs to be done then is edit GRUB's menu.lst to boot the OS from the correct drive name.

---

### Post by devils_casper on 2006-10-31
[QUOTE=Zaz]
I now wonder how to install grub on the external drive only.
The current installation will boot to the menu which allows for choosing os, but whichever os I choose it says Error 17: Could not mount filesystem. (Except for windows, which is 'unrecognizable')[/QUOTE]

**daou** posted an excellent link. i was gonna post that only but the problem is, your BIOS not supporting external bootable disk.

[QUOTE=Kerry Lange]
When I disconnected my other drives, the install went well and I was able to boot to the single drive where I'd installed Ubuntu. However, once I reconnected my other drives Grub lost track of where everything is and I ended up with a shell prompt instead of booting to Ubuntu.[/QUOTE]

thats coz of mismatch in device.map file. you have to add an entry for second disk in /boot/grub/device.map file




casper

---

### Post by Kerry Lange on 2006-10-31
Yes, I think you're right but, being a newbie to Ubuntu & Linux, I don't know what the file is that I need to edit (I've been pointed to two files "menu.lst" and "device.map"), where it is, how to get at it, and how to edit it.

When at the shell prompt I can't seem to navigate my way anywhere by using "chdir" or "cd".  I'm stuck with the "Busybox" prompt and don't know enough to do anything.

Can you point me to docs where I can find out what I need to do?

---

### Post by Zaz on 2006-10-31
My problem is now solved, I simply installed 6.06 instead. It installed grub the way I wanted to. Thanks for all the help.

---

