---
title: "MBR disappeared, grub-install didn't help"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by vidak on 2007-11-06
I've upgraded a Fujitsu-Siemens laptop to gutsy, and after upgrade grub seems to be disappeared from MBR (after starting a boot menu appears, to choose boot device from C:,floppy, CDROM. When choosing C:, the same menu reappears.). I tried to re-install grub using a live cd and grub-install --root-directory=/media  /dev/hdb (after mounting root into /media of course). After all, the laptop won't boot, but grub-install and plain grub gives no error. I tried fsck, but it seems that the HD is all right... Any ideas? :confused:

---

### Post by LaRoza on 2007-11-06
Try the Super Grub Disk.

---

### Post by vidak on 2007-11-06
Forgot to write, but I tried that also. No luck. 
The automatic procedure didn't work, so I tried manual mode, but it wasn't able to even find the hard disk (the live cd works OK with it, still)

---

### Post by LaRoza on 2007-11-06
Can you just reinstall Feisty? If it worked before, it seems like the best choice.

---

### Post by vidak on 2007-11-06
We tried that also:cry: Still nothing...
I was thinking about getting and mbr and dd-ing to the first bytes of hdb, but to be honest, I'm quite afraid of doing so if there is _any_ other possible solution...

---

### Post by meierfra on 2007-11-06
I'm not sure that this applies in your case, but it might be worth a look:

[http://ubuntuforums.org/showthread.php?t=442945#9]("http://ubuntuforums.org/showthread.php?t=442945#9")

---

### Post by 127.0.0.1 on 2007-11-06
Shouldn't poping in a ubuntu LIVE cd and running command fdisk /mbr work? or not?

---

### Post by GI_Josh on 2007-11-06
This might seem stupid, but your ESC key isnt' stuck on is it?

---

### Post by vidak on 2007-11-07
> **127.0.0.1 said:**
> Shouldn't poping in a ubuntu LIVE cd and running command fdisk /mbr work? or not?

With /mbr you mean the boot partition? Unfortunately we don't have one... But I've run fsck on the filesystem and it seemed to be OK...

---

### Post by vidak on 2007-11-07
> **vidak said:**
> We tried that also:cry: Still nothing...
I was thinking about getting and mbr and dd-ing to the first bytes of hdb, but to be honest, I'm quite afraid of doing so if there is _any_ other possible solution...

Sorry, I wrote incorrectly: we tried a gutsy-cd for installing again. Feisty will be the next one, probably... :)

---

### Post by logos34 on 2007-11-07
If this is a laptop shouldn't your hard disk be hda (or sda)?

**sudo fdisk -l**

instead of grub-install try this method:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by vidak on 2007-11-07
> **meierfra said:**
> I'm not sure that this applies in your case, but it might be worth a look:

[http://ubuntuforums.org/showthread.php?t=442945#9]("http://ubuntuforums.org/showthread.php?t=442945#9")

That's a great howto, indeed. Our case is not the same, since there is some only one HDD in the laptop. However, following that howto, I reinstalled MBR using grub the same way I did a few times before. After rebooting (and forcing BIOS to check ONLY the HDD for boot device), a miracle happened, and I met finally the grub boot menu. Somehow, when having CD as primary boot device, the BIOS didn't look at the HDD, it seems. I'm not sure however, why did it go wrong - and how (and first of all, why) it was good again...

Anyway, thanks for all the help, I'll go now and probably have a huge glass of wine :D

---

### Post by vidak on 2007-11-07
> **logos34 said:**
> If this is a laptop shouldn't your hard disk be hda (or sda)?

**sudo fdisk -l**

instead of grub-install try this method:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

Well, it probably should, but it isn't. There is no hda - quite weird thing... :confused:

---

### Post by vidak on 2007-11-08
OK, back with the big happiness... The problem is back again. Booting the laptop again, the Boot device menu re-appeared, and HDD fails to boot... Could this mean HDD failure? 

What can be done??? ](*,)

<edit>
it seems that the BIOS doesn't even recognize the HDD when grub fails to load...
</edit>

---

### Post by vidak on 2007-11-08
My last was that I made a grub boot-cd, which recognized only fd0-7 drives, no hd[0-9] or sd[0-9]
I used this manual for the cd:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---

