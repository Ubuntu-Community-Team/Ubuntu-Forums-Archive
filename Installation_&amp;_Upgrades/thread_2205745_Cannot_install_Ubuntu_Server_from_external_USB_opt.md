---
title: "Cannot install Ubuntu Server from external USB optical drive"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by mike148 on 2014-02-15
Hi, 

Sorry if i post in a bad section or if i don't say enough about the problem to solve it, it's my first time on the huge Ubuntu forum and english isn't my first languague...

Ok, so, i try to install Ubuntu Server on my old tower but this computer don't have a CD/DVD drive then i use a external USB CD/DVD drive. I already make install of linux distribution with CD or USB live and in the past, i even install Ubuntu Desktop on this tower. The problem is easy to understand, the computer boot on the CD and propose me to start install but when i press ok, it say that he try to found the CD-ROM and after a few moment tell me that he can't mount the CD and propose me to put the CD in...

Then i go to the busybox terminal with ctrl+alt+F2 and see that sr0 exist in /dev but i can't mount it as i found on one post somewhere in the web. I don't understand why i could install Ubuntu Desktop with that external USB drive and not Ubuntu Server... 

I think that i must precise too that the BIOS can't boot on a USB key, only the USB CD/DVD drive appears on the boot device priority in the bios.

If someone have a magic command to try in busybox? or another solution?

And thank you for the time you take to read my post, even if you don't have a solution ;)

ps: If someone know why i can't change my name on the forum? I don't very appreciate mike148 :D

---

### Post by mike148 on 2014-02-16
up? :confused:

---

### Post by Jason_Gibson on 2014-02-16
If it can see the usb cd drive to boot from then it can boot from a flash drive i'm betting. How did you put it on a flash drive? Unetbootin or any other program in my experience was a waste of time. I spent months trying to get a bootable flash drive before someone suggested dd.

```
sudo dd if=/path/to/iso of=/dev/sd? oflag=direct bs=1M
```

do that to the flash drive. /dev/sd? should = the location of your flash drive. you don't need to partition the flash drive to fat or anything. just /dev/sdb or whatever the letter is for the flash drive. it should boot from flash then i'm almost positive.

*EDIT* Be careful with dd though. If you have a typo or mess up where the output file goes you can wipe out your system.

---

