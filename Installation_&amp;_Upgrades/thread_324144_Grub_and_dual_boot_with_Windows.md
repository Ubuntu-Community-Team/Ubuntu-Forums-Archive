---
title: "Grub and dual boot with Windows"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Amorphous_Snake on 2006-12-23
I didn't have this problem before as I always had a separate PC for Windows and another for Linux. I tried Kubuntu and then openSUSE on my Windows PC as a dual boot. With Kubuntu, it worked fine. With openSUSE, I had problems and ended reinstalling Windows.

Here is a little info on my setup, I have 2 HDDs, hda is 120 GB and is partitioned as 20 and 100 GB NTFS. hdb is 20 GB and is currently occupied with openSUSE, although it won't boot by iteslf and I have to insert the DVD and select "Boot Installed System".

I am not asking for help with openSUSE. This is an Ubuntu forum! But what I want to know is how can I dual boot Windows and Linux from 2 separate HDDs without missing up with the default Windows boot loader. i.e. Windows will boot as usual if I disable the Linux HDD. I want everything not related to Windows to be in a separate HDD without touching the system at all. It's not that I don't trust Linux (I have a separate PC running Ubuntu 6.10 24/7). But I am not the only user of this Windows PC, and the other users are not comfortable with Linux and I am not converting them.

So, can such thing happen (separate HDDs, separate boot)?

I asked this on suseforums but no one cared to reply!

---

### Post by PurplePenguin on 2006-12-23
You can dual boot Windows and Linux - whether they're on the same HDD or not really makes no difference.  Furthermore, your users will have no idea whether Linux is on the same drive or another; they won't even see it from Windows.

---

### Post by confused57 on 2006-12-23
> **Amorphous_Snake said:**
> I didn't have this problem before as I always had a separate PC for Windows and another for Linux. I tried Kubuntu and then openSUSE on my Windows PC as a dual boot. With Kubuntu, it worked fine. With openSUSE, I had problems and ended reinstalling Windows.

Here is a little info on my setup, I have 2 HDDs, hda is 120 GB and is partitioned as 20 and 100 GB NTFS. hdb is 20 GB and is currently occupied with openSUSE, although it won't boot by iteslf and I have to insert the DVD and select "Boot Installed System".

I am not asking for help with openSUSE. This is an Ubuntu forum! But what I want to know is how can I dual boot Windows and Linux from 2 separate HDDs without missing up with the default Windows boot loader. i.e. Windows will boot as usual if I disable the Linux HDD. I want everything not related to Windows to be in a separate HDD without touching the system at all. It's not that I don't trust Linux (I have a separate PC running Ubuntu 6.10 24/7). But I am not the only user of this Windows PC, and the other users are not comfortable with Linux and I am not converting them.

So, can such thing happen (separate HDDs, separate boot)?

I asked this on suseforums but no one cared to reply!

Maybe this thread can help:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You could try setting the bios to boot first to the slave drive (with Suse installed), then make a grub entry to boot Windows in the /boot/grub/menu.lst(or does Suse use grub.conf?).  You could set the Suse drive on the primary master & Windows on primary slave, but you probably would need to make some adjustments in your grub menu to reflect the change(or reinstall Suse connected to the primary master).

I've never used openSUSE, but the principle should be the same.

---

### Post by ben a on 2006-12-23
hi, 
i recently had a xubuntu-cd from a colleague; it was just because i wanted to know more about linux etc. i installed xubuntu on my, second, windows 98-pc pentium2. this pc has 2 hard disks, win98 and xubuntu installed separately.
i'm very interested in the way how to adjust the menu.lst. i knew something about DOS but since windows most of the things ran out of my mind.
if you could hand me an example of a good working menu.lst i would be very grateful.
it could save me a lot of time while searching on the web.
so if you could - thank you very much.
greetings, ben.

---

### Post by cotcot on 2006-12-23
If you use the alternate install CD you have the opportunity to install the bootloader on another location than the MBR : for example a floppy or a usb-stick. Putting in the boot floppy or boot stick will give you the grub menu ;  leaving out will boot windows. Floppy or Usb Stick should be checked for boot before de hard disk.

---

### Post by bulldog on 2006-12-23
> **ben a said:**
> hi, 
i recently had a xubuntu-cd from a colleague; it was just because i wanted to know more about linux etc. i installed xubuntu on my, second, windows 98-pc pentium2. this pc has 2 hard disks, win98 and xubuntu installed separately.
i'm very interested in the way how to adjust the menu.lst. i knew something about DOS but since windows most of the things ran out of my mind.
if you could hand me an example of a good working menu.lst i would be very grateful.
it could save me a lot of time while searching on the web.
so if you could - thank you very much.
greetings, ben.

In your situation you have to install windows first,then make the ubuntu disk the master boot device in your BIOS or swap places with the windows disk fysically on the cable which them connects to the motherboard.
Than install ubuntu and GRUB will be installed in the MBR of this disk because it's master and (hd0).
Than change the menu.lst windows entry like the following example and your done.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by Amorphous_Snake on 2006-12-23
Thanks a lot guys for the links.

I can't believe it! Even when asking a non-Ubuntu question I got an answer. Ubuntuforums.org is the main reason that I will be forever loyal to Ubuntu.

Thanks again.

---

