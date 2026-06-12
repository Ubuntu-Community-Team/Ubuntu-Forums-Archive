---
title: "Dual boot using Windows boot loader, not GRUB"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by pwrstick on 2010-11-08
Ahoy,

I'm trying to dual boot Win7 and Ubuntu WITHOUT using Grub.  This is to support Bitlocker encryption.

I followed [this guide]("http://blogs.technet.com/b/voy/archive/2006/10/13/how-to-use-windows-vista-s-boot-manager-to-boot-linux.aspx"), and now when I select Ubuntu I get a Grub> prompt and no ubuntu.

I feel like I'm halfway there, I just need to get Grub to load correctly or something.  Anyone else accomplish this successfully?

Thanks!

---

### Post by oldfred on 2010-11-08
I prefer grub2, but if you have to use bitlocker this may be the better way.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by pwrstick on 2010-11-08
I discovered that the Windows dualboot works sort of, and I'm now suspecting Grub.

When I installed Ubuntu it was the only operating system, so I installed grub manually.  I think it was 
```
grub-install /dev/sda1
```
But I'm wondering if that's the wrong way with Ubuntu 10.10.  Do I have to use Grub2?

Anyway, when I'm at the Grub> screen I can manually boot Linux:
```
kernel /boot/vmlinuz-2.6.35-22-generic-pae root=/dev/sda1
initrd /boot/initrd.img-2.6.35-22-generic-pae
```

So maybe I have a simple GRUB question now, but should I be able to make a menu.lst or something that will automatically enter those commands for me?

BTW I've discovered that there is a /boot/grub/grub.cfg file, and that the supporting /etc/grub.d and /etc/default/grub files/dirs are there.  I even tried Grub> configfile /boot/grug/grub.cfg and it didn't like that.

---

### Post by oldfred on 2010-11-08
Windows boot loader in the MBR just jumps to the code in the boot sector of the active partition(boot flag). If sda1 was your window partition you have overwriten windows code, so you will not be able to boot windows. If installing grub to a partition like sda1 not the MBR you should install to the partition with Ubuntu. You could then move the boot flag if it is a primary partition and windows should boot grub. Lilo works better for being in the MBR as it will accept a boot flag in a logical partition. Not sure if windows even sees a boot flag in a logical partition.

---

### Post by cybergnome on 2010-11-09
See my reply on your other post.  The Win boot loader can't read the ext file system (it's DOS based), so if the MBR code calls the Win boot loader, another boot loader, such as Grub2, will need to be chained to it to boot Linux.  It is quite doable.

---

### Post by pwrstick on 2010-11-10
> **cybergnome said:**
> See my reply on your other post.  The Win boot loader can't read the ext file system (it's DOS based), so if the MBR code calls the Win boot loader, another boot loader, such as Grub2, will need to be chained to it to boot Linux.  It is quite doable.

I think chaining may be what I'm currently doing?  Upon boot I am presented with the Microsoft boot loader.  From here I can boot and use Win7 just fine (which is encrypted with Bitlocker), or boot to the Grub command line.  At the Grub command line I can load Ubuntu using the code snips above.

So, I can get into both operating systems, but I just have to make Grub work.  I.e. Windows is calling Grub but Grub doesn't seem to know how to load Ubuntu (menu.lst? grub.cfg?)

If you look at the link I originally posted, I'm pulling 512Bytes form the ubuntu partition that has Grub installed on it (/dev/hda1), and placing that in a file on the Windows partition.

---

### Post by pwrstick on 2010-11-10
> **cybergnome said:**
> See my reply on your other post.

[The other Post]("http://ubuntuforums.org/showthread.php?t=1599752"), deals with Bitlocker and Dual Booting.

---

### Post by cybergnome on 2010-11-10
From what you posted, you're on the right track.  You have a line in your Windows boot menu that calls Grub, but you didn't indicate which Grub.  I saw you posted a question earlier about having to use Grub2 with 10.10.  The answer is no, but Grub2, which is native to 10.10 is significantly different from legacy Grub.  The configuration file is named differently, and is not meant to be edited (there are other files to use for customization), etc.  While legacy Grub and Grub2 will work together, configuration specifics depend on which is which.

Ultimately, there are options, and the choice is yours.

---

### Post by wkhasintha on 2010-11-11
I agree with cybergnome here

---

