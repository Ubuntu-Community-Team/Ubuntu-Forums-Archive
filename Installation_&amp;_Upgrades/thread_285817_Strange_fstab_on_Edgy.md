---
title: "Strange fstab on Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Sargonmetal on 2006-10-27
Hi,

Yesterday I updraged to edgy and almost everything went fine. Today I've found this looking at my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
UUID=349c3b9c-5442-4568-b838-3abfd741b29a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=bcc34a28-f0d7-4fc7-ac37-cce7a9a3c2ec /boot ext2 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=F22C193A2C18FB75 /media/windows ntfs nls=utf8,umask=0222 0 0
# /dev/hda3 -- converted during upgrade to edgy
UUID=37d5bdfd-e858-4f8d-abad-99f6beeb3cff none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Anybody can tell me what this is?

And, I also have plugged an USB pendrive and 2 new devices have appeard to me: usbdisk and AV-FLASH. Why is that happening?

Thanks a lot! I'm a newbie and don't have any idea of these things!

---

### Post by kidders on 2006-10-27
Hi there,

You may be referring to the UUID references, which are just an alternative way of describing where filesystems are. The effect is slightly different than specifying their /dev paths though, since a filesystem's UUID will change should anything odd happen to it.

I suppose the idea is that, should you reformat, physically swap, or otherwise alter a partition, Ubuntu won't carry on treating it as though nothing had happened.

---

### Post by Jose Catre-Vandis on 2006-10-27
So if we want to edit fstab in the future can we still do so using /dev/hd* type syntax, and does Edgy automatically spot changes, even the addition of new hard drives? and what about permanently mounted shares etc?

---

### Post by kidders on 2006-10-27
It would surprise me if Edgy did that. The fstab file format is pretty standard across all Linux and Linux-like systems. You can rewrite it to look whatever way you want, and it will be interpreted consistently by almost any operating system.

If you prefer to use /dev device addresses, then you can safely switch back, just as you can use UUID-based addresses in Dapper. Just make sure you understand the distinction between both systems.

I hope that helps.

**Edit:** I forgot to say that there's no reason you can't mix & match device naming conventions. Take a look at mount's man page for more detail :-)

---

### Post by Jose Catre-Vandis on 2006-10-27
Ok, so how do you interpret the UUID addresses, and therefore write new ones ?

---

### Post by kidders on 2006-10-28
They're just standard UUIDs, so there's nothing to interpret from them really. If you want to get one you didn't set yourself, something like **tune2fs -l /dev/sda1 | grep UUID** will give it to you.

---

### Post by Sargonmetal on 2006-10-28
Thanks for the info. Didn't know about tune2fs.
So, there's nothing to worry about :)

---

### Post by Jose Catre-Vandis on 2006-10-28
> **kidders said:**
> They're just standard UUIDs, so there's nothing to interpret from them really. If you want to get one you didn't set yourself, something like **tune2fs -l /dev/sda1 | grep UUID** will give it to you.

Thanks :)

---

