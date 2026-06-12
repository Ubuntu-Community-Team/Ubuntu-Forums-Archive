---
title: "Instalation Problems, grub error."
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by presunto on 2006-10-14
hi all, i got 2 problemas here so i'll make just this thread with both. Please everyone try to help me :(

Problem 1-

I triyed to install ubuntu (6.06) on my pc (athlon 64, chipset nVidia, pci-e, vid. card: radeon x800). I put the cd and it loads the kernel when i press start or install ubuntu, it loads and everything goes fine. But, when its time to load the live cd, the output shows an error: can't load x server or something, and it goes to text mode. fdisk /dev/hda doesn't works, and it shows too an i/o error. So i couldn't install, i triyed all i could on 2 hd's.

when i pressed "startx" it comes this output:

'XIO: Fatal IO error 104 (connection reseted by peer) on x server ":0.0"

Fatal server error:
No screen found.'

The drivers are FINE, no problems with that (almost sure)


Problem 2-

So, i thought: "if it doesn't work on amd64, i'll install on a pIII i got here and move the hd to here after."
He installed fine the ubuntu on PIII, he asked for the last reboot to enter ubuntu sistem. Rebooted and here comes the beggining of errors.
After the first boot, i got grub's "error 18" (cylinder problems), my partition was swap (hda1) and / (hda2).

I installed it again, but the /boot partition with 50mb just for him and some free space unformated. It installed fine, but... Grub error 17! I know its a problem that grub doesn't find partition and so...

i got a slack cd, boot it, and input the "linux rescue" comand
he rescued fine, but at the end i got a I/O problem again!
it shows like "FAT: unable to read boot sector.", "hda6: bad acces: block=x..." "kernel panic: VFS: Unable to mount root fs on 03:06" and more error problems with the same kind.


Please help anyone, i need to install ubuntu quikly. and i got NO IDEA what to do. Problem 2 is more important, because i COULD install ubuntu, it must be some dumb error.

Thanks anyone.

presunto

---

### Post by fishcake007 on 2006-10-14
Sorry can't help you with problem 1
Problem 2
What the size of the hard drive you are using? 
It is possible that your PIII bios doesn't support such a large device and is getting confused with the previous MBR that you first setup when you tried to install it on your AMD64. Check with the bios on your PIII to see what size the disk is reported as? 

If it's bios then I'd use the live cd and check with cfdisk or gparted at what's going on with the partion tables, possibly delete all partions and create a new MBR. Then reinstall.

However I'm sure someone can help you with problem one so you shouldn't have to resort to this solution.

---

### Post by presunto on 2006-10-14
my hd is 120gb. but i had slack and fedora before triyng to install ubuntu (i REALLY want to try it on my amd pc with xgl)

and i didn't installed NOTHING on amd pc. can't do it.

I'll try something with that.

plz more answers =)

---

### Post by Kateikyoushi on 2006-10-14
Try to install your a64 in safe video mode or with the alternate install cd. I would search on the forum about the chipset of the motherboard maybe have to boot the kernel with some commands.


List your partitions on the P3 to see how it looks now then lets figure out something with your grub.

Post the output of this.
```
sudo fdisk -l
```

---

### Post by gn2 on 2006-10-14
Are you trying 64-bit OS?

If so suggest 32-bit.

If using 32-bit perhaps try another Distro, it would be easier...

---

