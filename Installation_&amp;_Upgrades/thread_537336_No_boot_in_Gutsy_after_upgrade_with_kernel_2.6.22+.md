---
title: "No boot in Gutsy after upgrade with kernel 2.6.22+"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by topynate on 2007-08-28
I recently upgraded to Gutsy. On rebooting, I found in impossible to mount my hard drive(s)_ - details below. I used the old 2.6.20 kernel instead, and had no further problems.
However, today, having upgraded to the kernel 2.6.22-10-generic, X doesn't work, so I'm motivated to solve this problem :-)

When I turn on the 'nosplash' option in GRUB, the first failure message is:
mount: Mounting /dev/disk/by-uuid/eb522...842 on /root
failed: Device or resource busy.

There follow a few more lines, before I get dumped to a BusyBox prompt. The weird thing is, I checked /boot/grub/menu.lst, and there's no difference whatsoever between the old lines and the new lines, apart from the kernel name.
Does anyone have any clue? I'm typing this from Lynx, by the way, so apologies if it comes out looking messed up. Cheers.

---

### Post by Pumalite on 2007-08-28
sudo dpkg-reconfigure xserver-xorg

---

### Post by topynate on 2007-08-28
Thanks! That's one problem sorted - I feel much better now.

Does anyone have any ideas about the other problem I mentioned?

---

### Post by topynate on 2007-08-29
Bump - here are some pictures I took of my screen yesterday. Apologies for the poor quality.

---

### Post by Pumalite on 2007-08-29
> **topynate said:**
> Thanks! That's one problem sorted - I feel much better now.

Does anyone have any ideas about the other problem I mentioned?

I thought we had your xserver problem resolved. What happened now?

---

### Post by topynate on 2007-08-29
Ah, I think I was a bit unclear. When I upgraded, the kernel version increased to .22 from .20, and that's when I stopped being able to boot. So what I've been doing instead is booting the old Feisty kernel. It looks like that's not going to be an option for much longer though, so I want to find out what's stopping me from booting with the new kernel. The xserver problem was probably just a consequence of running gutsy with an old kernel.

---

### Post by Pumalite on 2007-08-29
Well, lets find out a few things; post:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst
cat /etc/fstab
blkid

---

### Post by topynate on 2007-08-29
OK, that's all cut&pasted at [http://dark-code.bulix.org/6xxfpb-54005](http://dark-code.bulix.org/6xxfpb-54005) . Thanks!

---

### Post by Pumalite on 2007-08-29
I'm trying to sort this out. Do you have 2 or 3 hard drives? Why do you have Linux in sda, sdb and sdc?

---

### Post by topynate on 2007-08-29
Yeah, there's a lot of cruft - I like tinkering. You're looking at the debris from a reinstall on a new disk - sda has the old installation (which is really old, I think hoary), sdb the new, and sdc (the big 320GB drive) has my /home on it. If you look at the bottom of /boot/grub/menu.lst, you can see where the installer detected the old, broken installations on /dev/sda1. The root of my current filesystem is on logical device /dev/sdb1, with uuid eb52257f-880a-44fc-a1db-8d1728e1f842. Clear as mud, eh?

---

### Post by Pumalite on 2007-08-29
Never mind; you have 3 hard drives and you probably have Data in one of them. I don't see a bootflag anywhere. Your .22 kernel points to hd1,0; that would be sdb1. Bootflag should be in sdb1. The rest of the stuff is pretty confusing, but seems to be in order. Let me think for a while.

---

### Post by Pumalite on 2007-08-29
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to set bootflag to sdb1. Let's see what happens.

---

### Post by Pumalite on 2007-08-29
On the other hand, if I were you; I would clear all that garbage in sda and do a clean install of Gutsy in sda and keeping /home in sdc.

---

### Post by topynate on 2007-08-29
OK, flag set. There's some interesting stuff in gparted, for instance the /dev/dm-0, dm-1, etc. Also sdb1 had a warning next to it that it couldn't find a mountpoint - is that bad? I'm going to reboot now, so we'll see, I guess :)

---

### Post by topynate on 2007-08-29
I'm afraid setting the flag made no difference. I think I'm going to go with the reinstall idea - thanks for your help :)

---

