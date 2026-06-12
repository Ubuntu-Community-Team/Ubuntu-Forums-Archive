---
title: "Help With Grub!!!"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by cisforcojo on 2006-09-21
Hey all,

I am running an XP / Ubuntu dual boot and was trying to set up a splashscreen for grub. I ran:
sudo grub-install /dev/hda0 

and it told me:
/dev/hda0: Not found or not a block device.

then:
sudo grub-install /dev/hda1

This is the location of my windows partition.

I now cannot boot into XP or even see any of the files.
PLEASE tell me this is reversible.

Any help you can give me would be GREATLY appreciated.

---

### Post by jd65pl on 2006-09-21
This may help you fix that one

[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

Thanks

J

---

### Post by wkulecz on 2006-09-21
I think he has to restore Windows first as he may have over written the windows boot loader.

Get windows to boot again.
Restore Grub.
And then add the "Other" stanza to /boot/grub/menu.lst to "chainloader +1" to windows.

--wally.

---

