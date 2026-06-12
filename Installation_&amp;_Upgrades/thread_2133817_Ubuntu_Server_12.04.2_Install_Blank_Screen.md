---
title: "Ubuntu Server 12.04.2 Install Blank Screen"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by Beacon11 on 2013-04-09
Hey all.

I've seen several posts about this, but either I'm applying their fixes incorrectly or their fixes just didn't work.

I'm trying to install Ubuntu Server 12.04.2 from a flash drive. I get to the point where I'm booting off the flash drive and get to the "Install Ubuntu Server," or "Install in expert mode," etc. screen. I hit "Install Ubuntu Server," and immediately get a blank screen (I've let it sit for a half hour). So I edited the grub entry for that install line, which by default holds (note that I'm typing this out by hand; forgive typos):

```
setparams 'Install Ubuntu Server'

set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet --
initrd /install/initrd.gz
```

I updated it to include the nomodeset option (seems to fix blank screen issues according to numerous forum posts):

```
setparams 'Install Ubuntu Server'

set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed nomodeset quiet --
initrd /install/initrd.gz
```

Nothing changed: I still had the black screen when I hit F10 to boot. I also tried:

```
setparams 'Install Ubuntu Server'

set gfxpayload=keep
linux /install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed quiet vga=771 --
initrd /install/initrd.gz
```

with no changes. Any ideas?

---

### Post by ultrafast on 2013-04-09
Im having the exact same problem and i cant seem to fix it ether and i tried all the options.

---

### Post by Beacon11 on 2013-04-09
> **ultrafast said:**
> Im having the exact same problem and i cant seem to fix it ether and i tried all the options.

Perhaps we're adding those options incorrectly? I've only ever done it in an installed GRUB2, not at the install screen. I've been unable to find information on that, though-- everything I find is only on already-installed systems.

---

### Post by darkod on 2013-04-09
Also, I don't think the file=/cdrom would apply to a usb stick.

I have no idea why this is happening personally. I don't see nomodeset as relevant too since it mostly affects desktop versions. The server version has text installer to start with, so even with limited video drivers it should run the installer OK.

You can try googling the exact computer/board/cpu model whether it has some issues with ubuntu server. A wi-fi adapter if present can sometimes make issues too.

---

### Post by Beacon11 on 2013-04-09
> **darkod said:**
> Also, I don't think the file=/cdrom would apply to a usb stick.

I have no idea why this is happening personally. I don't see nomodeset as relevant too since it mostly affects desktop versions. The server version has text installer to start with, so even with limited video drivers it should run the installer OK.

You can try googling the exact computer/board/cpu model whether it has some issues with ubuntu server. A wi-fi adapter if present can sometimes make issues too.

If I remember correctly, the thing has always mounted as /cdrom. I assume it's due to the fact that, historically, only CDs were used for boot media. They wouldn't create a different mount point just because it's a flash drive.

I'll hunt around Google some more...

---

### Post by darkod on 2013-04-09
Not so sure, but haven't used usb server install too many times neither. If you have the ISO on the stick (not unpacked), it would usually use loop device in grub2 to load.

If the ISO is unpacked (you have the files directly on the stick), it might use that path but in that case check if the /cdrom folder exists. I have done it with unpacked ISO creating grub2 entry manually, and with stick prepared with universal usb installer. For my manual entry it wasn't /cdrom because the files were in different folder, but for the stick created with the universal usb installer I really don't remember.

---

