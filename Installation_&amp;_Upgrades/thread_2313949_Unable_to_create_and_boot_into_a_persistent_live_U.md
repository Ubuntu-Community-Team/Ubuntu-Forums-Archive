---
title: "Unable to create and boot into a persistent live USB"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by gordan-vrbanec-vepar on 2016-02-17
Hello!

I'm having trouble creating a live Ubuntu USB, but with a persistent casper-rw partition so i can have it larger than 4 GB.

I'm following all the guides.

First i make a bootable usb with universal USB installer (pendrivelinux).

Then i boot into a live CD so i can use gparted and resize and make a partition.
I first delete the casper-rw file, then i make the casper-rw partition and apply all changes.

I leave some space on the fat32 partition where the system is just in case.

Now, according to all the guides, that should be it, the next time i boot into the USB the live session should use the ext4 casper-rw partition instead of the file.
Every time i do this i end up in the (**initramfs**) command prompt and the system won't boot up.

If i leave the file and do nothing with partitioning, it loads up fine.
I even tried the reverse, to first make an ext4 casper-rw partition, then make a bootable USB, still the same. Goes to initramfs...

I tried this with Ubuntu 14.04.3 and Ubuntu 15.10, both 32 bit. I also have Ubuntu 12.04.5, haven't tried this one, but i have the feeling it's going to be the same.
I'm using a 32 GB USB. Does this have to do something with anything?

Please, what am i missing? Why doesn't it work?
Is there an alternate method of doing this? Also, it would be nice if it could boot directly into Ubuntu without needing to select "try before installing" but i'd be happy just to get it to work, and have persistance so i can install all the necesarry programs and have it there the next time it boots into ubuntu.

I really need this to give to my friend so he can do some work since the computer he has is locked up with passwords (it's a company computer), and he can't install anything any more. And since Blender is also available for linux, i thought this would be a good way for him to continue his work, but i can't figure out why i can't make this larger partition.

Please help!

---

### Post by sudodus on 2016-02-17
Try mkusb :-)

It will do all the configuring for you and you get a system with a casper-rw partition and also a usbdata (ntfs) partition for transfer of data to/from running Windows systems.

[mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by gordan-vrbanec-vepar on 2016-02-17
Thank you! I will try that. :)

Right now i am in the process of just installing Ubuntu on an USB instead of doing it live USB mode. But i used ext4 and it is very sluggish. Now it's installing with ext2 and i'll see if that makes a difference. I read somewhere that it does, that the journaling file systems make USB OS slow...

But i would just rather use live USB because it's way faster and that extra transfer partition will come very handy for the specific task it is intended for, so after that finishes (it already started so i might as well let it finish) i'll see how it performs. If it's not as good i'll try mkusb.

---

### Post by ubfan1 on 2016-02-17
You can turn journaling off when you make the ext4 (-O ^has_journal), or use probably tune2fs to turn it off afterwards. ext2 and ext3 have used the ext4 driver code for awhile now, so some old warnings do not still apply.

---

### Post by gordan-vrbanec-vepar on 2016-02-17
Thanks for the tip ubfan1. I'll keep it in mind in the future.

But I ended up making a live usb with "mkusb".
Works like a charm! :) Persistance is there, i already installed Sketchup and Blender, and restarted a few times to make sure everything is there.

And it is. All the data i saved, all the programs i installed and the user i created are all there.
The only thing i don't see is the transfer partition. Either i missed it somehow while looking or i messed up something. But it doesn't matter much, i can always write directly to the hard disks from that USB. I just have to enable writing to NTFS, i did it before, i'll just have to look it up again. Or just use another USB for that, whatever...

Thanks for all the help!

---

### Post by sudodus on 2016-02-17
Congratulations to a working system :KS

But I think you should be able to see the 'transfer partition' too, unless you used 100% of the drive space for persistence. See the attached file (from testing my Lubuntu 14.04.4 LTS)!

As you see, there are two shell-scripts, that help you backup and restore the persistent data. It is easy to damage the persistent data, particularly if you unplug the pendrive before the computer has shut down completely, but also other problems can damage the file system in the casper-rw partition. So backup your system at regular intervals and when you have added a lot of important things :-)

If you run the following command, when running the persistent live system, you should 'see' it. Post the output in a reply, if you need help to interpret the result.

```
sudo lsblk -fm
```

---

### Post by gordan-vrbanec-vepar on 2016-02-22
I'm sorry for the late reply...

It was me, i was mistaking a volume for another, and thought the transfer partition didn't get created.

It did. I just didn't see it, so, yeah, brainfart... :P

I checked the partition in Windows too, it's there. :)

---

