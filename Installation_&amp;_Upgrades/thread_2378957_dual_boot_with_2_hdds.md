---
title: "dual boot with 2 hdds"
date: 2017-11-29
forum: Installation &amp; Upgrades
---

### Post by kwstas on 2017-11-29
hey all
im on a dual boot 32bit pentium4 with xp and lubuntu which  works fine!
recently i decided to put a second hhd(separated in ntfs and ext4) and install the minimum ubuntu package to it so as to try compiling the minimum to have it just for booting on mame.
i just finished the installation but

1. i get the "mame" partition 1st in grub (i prefer not)
2. when i boot on it, it comes to a black screen (ctrl+alt+del works)

is what i need to do possible? any ideas of what goes wrong?

edit: i tried to reinstall but same happened.
       i tried the option "recovery mode" from grub menu and "root" and "maintenance" and i got this:
[time] timed out waiting for device dev-di******
[depend] dependency failed for /dev/disk/by-*****
[depend] dependency failed for swap.

it seems that after this step it boots normally but still the same if booted from normal 1st grub entry!

---

### Post by yancek on 2017-11-29
What do you mean by "the minimum ubuntu package"?  Is this a basic install of an Ubuntu Desktop?  If so, which release?  I doubt any current release would run on hardware that old so if that's not what you did, post details.  What exactly do you mean by "mame"?  Can you post some details on your hardware, graphics card, memory, cpu?

---

### Post by deadflowr on 2017-11-29
Do you mean mame as in the game emulator?
As in the goal is to have an install boot directly into mame like a kiosk mode setup, or something like that.

---

### Post by kwstas on 2017-11-30
it was the "mini.iso" the last LTS 16.04 from [here]("https://help.ubuntu.com/community/Installation/MinimalCD").
im sorry i wasnt clear enough, yes it's "m.a.m.e" the arcade emulator. I thought i could give it a try to have it booting directly after grub so as not to load anything more since this pc is quite old.
pentium 4 3ghz 2g ram with intergraded graphics card.
30mins ago i tried to install the "mame" on the windowsxp partition and everything finished(instalation,snaps, roms) in 10 minutes! 
i just hope to find the way to make it as i want bootable in its own linux partition...

---

### Post by again? on 2017-11-30
If I'm understanding right.... you can still boot into Lubuntu but the grub menu order changed after you installed the mini.iso and you would like Lubuntu first.
If that's the case...
Boot into Lubuntu.
Use disks if it's installed to check which drive the Lubuntu partition is on.
or check via terminal:
```
sudo fdisk -l
```

Then reinstall grub to the drive Lubuntu is on.
```
sudo grub-install [COLOR="#FF0000"]/dev/sda[/COLOR]
```
where [COLOR="#FF0000"]/dev/sda[/COLOR] is the drive the Lubuntu partition is installed to.
*****Note**: Use the drive sda or sdb etc ...not sda**1** sda**2** sdb**1** etc which is the partition.

---

### Post by kwstas on 2017-12-03
so if i understood correctly i will just have to re-install grub from the system that i need to have the priority, right?

---

### Post by yancek on 2017-12-03
> so if i understood correctly i will just have to re-install grub from the system that i need to have the priority, right? 		

Correct, if you want Lubuntu in charge of the bootloader, boot into Lubuntu and run the command suggested above AFTER verifying which drive it is on, sda or sdb.

---

### Post by kwstas on 2017-12-03
thank you i'll try that!

---

