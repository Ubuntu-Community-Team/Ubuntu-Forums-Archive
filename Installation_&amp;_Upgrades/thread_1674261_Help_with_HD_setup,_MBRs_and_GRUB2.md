---
title: "Help with HD setup, MBRs and GRUB2"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by Wij on 2011-01-23
Not found a similar problem anywhere else so here goes.

I have a 4 year old PC with two HDs in. The first is a 300GB one with just XP Pro on it as it was when I originally built it. Subsequently I added a 500GB one which now has Ubuntu 10.04 and Win7x64 (and a broken Fedora install).

I'd like to get rid of the old HD with XP on it so I can play about with it for other purposes. I hadn't realised though when I install Ubuntu that it was still set in BIOS as the primary boot HD. The PC is booting from the old HD but then invoking the /boot which sits on the new HD and contains the correct selection of OSs.

I went into BIOS and told it to boot first from the new HD but that only invoked a presumably GRUB 1 menu which offered the option of a broken Fedora install and the broken XP install. Not much use.

How can I make the MBR (presumably, not my strong point) on the new HD invoke the GRUB2 menu which is on the same HD and thereby break my reliance on a totally redundant HD to boot ?

Any help appreciated.

Thanks.

---

### Post by dabl on 2011-01-23
If I understand your goal, you want to install Grub (grub-pc) on the newer hard drive, and have it boot an OS on the new drive.

Review this guide, particularly section 4:

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

You will need to use the command "grub-install", and the "--root-directory= " option.  Suppose your newer drive is recognized in Ubuntu as /dev/sdb:

```
sudo grub-install --root-directory=/ /dev/sdb
```

Study it carefully -- I'm just guessing about your system.

---

### Post by Jinx13 on 2011-01-23
From what I make of it you want to remove the HDD with the MBR on it? 
I could be wrong...
There is a windows program called EasyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) you can edit your bootloader.
You need to move it from the first HDD and assign to the second then using Windows Se7en built in disk management make the second HDD active partition.
 
Or...
 
Remove the first HDD and run the repair option in Windows Setup disk which should rewrite the MBR then install grub with EasyBCD :)
 
Hope this helps.
 
Regards,
Jinx13.

---

### Post by psusi on 2011-01-23
sudo grub-install /dev/sdb should do the trick.

---

### Post by Wij on 2011-01-26
Possibly wasn't the best way of doing it as I wanted to use a dedicated GRUB partition I'd created on the new HD and this way just put the grub files back in the Ubuntu partition but at least this way got me working.

I unplugged the old HD so that the new one was /dev/sda and then booted from a live CD and followed this guide to install GRUB2.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Thanks for the tips. Lots of interesting reading. One day I will make GRUB work the way I want it but I'm happy for now with a system the boots Ubuntu or Win7 without the need for a redundant HD :)

---

