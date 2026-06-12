---
title: "Multiple OSs, Multiple Grubs"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by ajeannotte on 2008-02-09
I have a system.

First hard drive has 3 partitions, Windows XP then Ubuntu 7.10 then SWAP.
Second hard drive has SWAP, Kubuntu, then it HAD (gone now) Ubuntu Studio.
Third hard drive has user data, that's it. 

After installing Ubuntu the first time, Grub picked up windows no problem. Not that i care anymore since i haven't used windows in ages, but it's part of the story. 

After installing Kubuntu a little while ago, Grub did its magic again and i saw all three OSs and could boot into any of them. This is ideally where i want to be. 

After installing Ubuntu Studio (for kicks) and not really being able to get anything to work, i decided i'd overstepped my bounds and get rid of it. Played around a little, couldn't figure out how to reinstall Grub by itself or tell it to use the Grub version on Kubuntu (which still LOOKS correct when in open it in gedit)..... so what i did was wipe the partition with Kubuntu on it, and reinstall it. The idea was to reinstall it and Grub would do its magic again and i'd be back to where i was before i installed Studio.

But now it's all buggered up. I assume Windows still works, but i really don't care, haven't tried it. Ubuntu still works. But booting into Kubuntu didn't work, even though the new Grub looks like it did when it was working perfectly. 

I went into /boot/grub/menu.lst and edited the hd(0,0) that was overwritten in what was apparently a bad update, set it to hd(1,1) and rebooted. On reboot it came up with the blue graphical kubuntu loading screen, then went into something with a prompt called 'initramfs'. 

I have no idea wtf is going on. 
Help! i'm drowning in a puddle of Grub!!

Side note: if i ever get into a situation similar to this again, playing with new OSs etc..., how to i tell Grub to stop loading from one partition and start loading from a previous one?

---

### Post by rucadulu on 2008-02-10
Please post your menu.lst file this will help me see what grup is looking at. The file is located under /boot.

---

### Post by jesusfreak107 on 2008-02-10
[http://www.geocities.com/lode_leroy/grubinstall/](http://www.geocities.com/lode_leroy/grubinstall/)

Install Grub on the Windows installation (above link), and set your BIOS to boot off of it. even though you do not use Wimpdows, you can use that Grub to read all installs on all disks.  We have it working on 3 computers at our house. you might have to edit the file a tad, though.

Also, just try setting your BIOS to boot off of the Ubuntu or Kubuntu partions/drives, and see if that works.  if the Grub is still intact on either, it might just work.  but that is so simple, there is no way that could be the answer.
:guitar:
:lolflag:

---

