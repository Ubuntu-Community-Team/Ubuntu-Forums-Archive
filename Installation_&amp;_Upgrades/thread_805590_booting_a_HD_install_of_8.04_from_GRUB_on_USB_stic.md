---
title: "booting a HD install of 8.04 from GRUB on USB stick"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Dragonath on 2008-05-24
Hello,

recently I installed a new SATA hard drive, because the IDE I have been using so far is failing (I think - it's been 2 years now). I have installed 8.04 on the SATA drive, so no worries there.
The problem is that my motherboard (chaintech zenith 7njs) can't boot off a sata drive, so I've opted for using my USB stick to boot the installation up. Should be doable, right?
Now I've been tinkering for a few days, and I think I'm on a right track, as GRUB boots up just fine with the 8.04 boot command I copypasted from the SATA drive's /boot/grub/menu.lst listed in it. It even starts booting up the linux kernel (at least that's what it looks like it's doing), however at one point it shows an error, then defaults to the BusyBox shell.

The error (I'm not sure the first two lines are a part of it, but I've added them just in case):
```
Check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/4a4d367a-cf21-4ca4-87 does not exist
```

Is there something that I should change in the USB sticks menu.lst or is there some other problem with the 8.04 installation?

---

### Post by meierfra. on 2008-05-24
Do you have the kernel on the USB stick?  I believe that the whole /boot folder needs to be on the USB stick (but I'm not sure about that)

---

### Post by Dragonath on 2008-05-25
No kernel, only the /boot/grub directory.

GRUB can load a kernel off a different hard drive than itself quite nicely. You just make the partition with the kernel on it root and specify the kernel's location on it.

I don't think the problem here is that the kernel doesn't load. It starts loading alright, there's something else that's missing.. but I am really unfamiliar with the 8.04 boot sequence and it's needs.

For the record, the GRUB I'm using is version 0.97.

---

### Post by Herman on 2008-05-25
:) What does your booting stanza look like (from near the bottom of your /boot/grub/menu.lst)?
> ALERT! /dev/disk/by-uuid/4a4d367a-cf21-4ca4-87 does not existDoes it really include '/dev/disk/by-uuid/'? 

Or does it have root=UUID=4a4d367a-cf21-4ca4-87?
That doesn't look like a long enough UUID number for an ext3 file system to me either.

It should look something like this,
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``` Would that be the problem? I'm only guessing.

Regards, Herman :)

---

### Post by meierfra. on 2008-05-25
> GRUB can load a kernel off a different hard drive than itself quite nicely. You just make the partition with the kernel on it root and specify the kernel's location on it.

From  what I heard if the bios can't boot a drive, Grub won't be able boot a kernel from that drive either. But I'm not sure since I never encounter that problem myself.

---

### Post by Dragonath on 2008-05-25
This is what I have now. The UUID is indeed longer.

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/hda1 UUID=4a4d367a-cf21-4ca4-87e6-d8a27c468e37 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

As for booting linux off something the bios itself can't boot - [https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")
I've tried the things in here, and so far they haven't worked very well.
Edit: besides, GRUB does manage it so far that I can see the Kubuntu splash loading, it's just that the processes running underneath mess up.

I just have a feeling that success is right around the corner. :)

---

### Post by Herman on 2008-05-25
```
title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=[COLOR=Red]**/dev/hda1**[/COLOR] UUID=4a4d367a-cf21-4ca4-87e6-d8a27c468e37 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet
``````
title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=4a4d367a-cf21-4ca4-87e6-d8a27c468e37 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet
```

---

### Post by meierfra. on 2008-05-25
> As for booting linux off something the bios itself can't boot - [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Thanks for the link. So it seems that your approach works on some computers. I didn't know that.

Luckily Herman seems to be right on track with his advice.

---

### Post by Dragonath on 2008-05-25
I added the /dev/hda1 bit after I read the howto I linked to in my previous post. Without it I get the error in my first post.
The menu.lst entry I pasted is from a more recent test than the error I originally posted - sorry for the confusion.

I have a hunch that the problem might be cured by loading some module that helps the kernel load things from the sata drive. But as I know almost nothing of the linux boot sequence and the modules involved in it, I don't have a clue as to what module might hold the key to solving this.

---

### Post by Dragonath on 2008-05-26
...and I was wrong, it WAS about the mistakenly copied UUID. Booting worked, as I am writing this from the 8.04 install.

Thanks, Herman.

---

### Post by Herman on 2008-05-26
8-) Cool!

---

