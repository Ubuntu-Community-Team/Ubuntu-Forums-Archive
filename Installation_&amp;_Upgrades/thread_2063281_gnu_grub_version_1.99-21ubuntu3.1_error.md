---
title: "gnu grub version 1.99-21ubuntu3.1 error"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by strmy on 2012-09-26
Hi!
i have a problem at startup of ubuntu 12.04 64bit.
 when i start the computer it says:

GNU GRUB VERSION 1.99-21ubuntu3.1
Minimal BASH- like line editing supported. for the first word, TAB
lists all possible command completions. Anywhere else TAB list possible device or file completions.

if i press tab, it shows a list of some words that don't make sense to me.

when i insert a liveCD there is no response. yes i have selected CD boot in bios, but it starts from hard disc anyway.


Please help.

J.

---

### Post by darkod on 2012-09-26
Were you deleting any partitions? Maybe you deleted the ubuntu partition by accident? Were you changing the boot order in BIOS? Maybe you have good grub2 on one disk and broken grub2 on another one, and you are simply booting from the wrong disk.

It's not possible that it can't boot from the cd. If it can't, then either you are not doing it right, or your cd-rom is faulty, or the cd is faulty. The computer should always be able to start from cd when you tell it to, regardless what is happening with the hard disk.

But if you want, you can try fixing this without the liveCD (although it would be much easier if you can boot the cd in live mode).

At that grub prompt, what does it show if you execute:
ls (small LS)

---

### Post by strmy on 2012-09-26
ls:
(hd0) (hd0,msdos5) (hd0, msdos1)

I've instaled upgrades, have only 1 disk, couldn't delete partition, because ... well i just don't know how to do that :D

i'll check cd and report.

---

### Post by darkod on 2012-09-26
So, you have only one disk (hd0) which has two partitions, #1 and #5. I guess you have only ubuntu, not a windows dual boot.

In that case, try these commands to boot. Execute them one by one:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
linux vmlinuz root=/dev/sda1
initrd initrd.img
boot
```

See if that boots you.

---

### Post by strmy on 2012-09-26
after   linux vmlinuz root=/dev/sda1
i get: invalid file name 'vmlinuz'

---

### Post by darkod on 2012-09-26
OK. Before you start executing the commands, check the exact file names with:
ls (hd0,msdos1)/boot

You should see something like vmlinuz-3.2.0-xx-generic and initrd.img-3.2.0-xx-generic. Note them down.

After that, when you know which files are there exactly, modify the last two lines before boot as:
```
linux /boot/vmlinuz-3.2.0-xx-generic root=/dev/sda1
initrd /boot/initrd.img-3.2.0-xx-generic
```

The rest of the commands are the same. In these two just use the filenames you found with the ls command.

See how that goes.

---

### Post by strmy on 2012-09-26
i get list of files, like 20 of them. they're all similar(starting with system.map/abi/config/initrd.img/vmlinuz), but have different numbers - from 20 to 31.

if i use any of these, starting with vmlinuz i get:
error: file not found.

---

### Post by darkod on 2012-09-26
Make sure you use the correct syntax for the filename. If it's there, it should work. Try the ones with the highest -xx- number first, if that doesn't work, the next lower, etc.

Also, try this modification:
```
linux (hd0,msdos1)/boot/vmlinuz-3.2.0-xx-generic root=/dev/sda1
initrd (hd0,msdos1)/boot/initrd.img-3.2.0-xx-generic
```

Just make sure you use the correct filenames and it should work.

---

### Post by darkod on 2012-09-26
I'm signing off, just to add this. If those commands managed to boot your ubuntu, open terminal and reinstall grub2 to the MBR with:
```
sudo grub-install /dev/sda
sudo update-grub
```

If you can't boot with those commands, then you might have a more serious problem, not just grub2 not booting.

---

### Post by strmy on 2012-09-26
can I try one after the other, or must I type everything for each try, when i try different numbers?

i tried with nr.31 and 1. of these two rows was ok, for second one i got:
couldn't read file

---

### Post by darkod on 2012-09-26
It has to be in separate tries. That group of commands end with "boot" which will try to boot using the files loaded previously. So you can't try all of them at once.

Also, the vmlinuz and initrd.img files need to be paired, they need to have the same version number. For example, if you use vmlinuz-3.2.0-31-generic you have to use initrd.img-3.2.0-31-generic also. You don't need to try the newest one, you can also use the oldest, with smallest number. Is it like 3.2.0-20 or something like that.

---

### Post by strmy on 2012-09-27
i have no idea what happened now, but it works...

liveCD i tried yesterday was ok on other computers, but i made another one just to try, and the computer started. the strange thing is, that i haven't really done a thing, i've just shutdown the computer, and after that it worked without CD :D

thanx for your help anyway!!

J.

---

### Post by weric93 on 2013-02-01
I am having a similar issue and I tried following the commands listed on this thread, but when I use the ls (hd0,msdos1)/boot command I don't get anything. I am reinstalling this but have tried multiple versions and configurations and am having no luck.
 
Please let me know if you have any more suggestions.
 
Thanks
Weric

---

### Post by Mashai on 2013-06-26
Hey! So, after an update, I restarted to the same issues! I've followed @darkod's directions and it spit me out at something that says BusyBox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash). So, what's my next step?

Aditional info: I am NOT partitioning! Its all strictly Ubuntu on my disk, only one partition.

---

### Post by awilo on 2013-08-19
ls:
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0, msdos5) (hd0,msdos1) (hd1)

---

