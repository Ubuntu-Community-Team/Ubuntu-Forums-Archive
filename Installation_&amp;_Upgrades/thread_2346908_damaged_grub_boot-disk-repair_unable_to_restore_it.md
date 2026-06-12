---
title: "damaged grub boot-disk-repair unable to restore it"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by david-k42f on 2016-12-19
Hi all, I need some help repairing the grub.
I had installed in my laptop windows 7 in dual boot with ubuntu, the first partition had the boot flag, it's where windows 7 is, the second partition is a logical ntfs partition to store data for win7, the I have an extended partition wich is divided in 3 partitions , ubuntu was installed using the 3 of them , the first using mount point "\" the second one being a swap partition and the third one using a mount point "\home".
I took the hdd and installed it in an external case, the system wouldn't boot up, but then I used another laptop (kaby lake 7th gen laptop) and grub worked fine.
So I connected the hdd back in my laptop and used boot-repair-disk to make it boot in my laptop, then boot-repair wasn't able to repair it but now also won't boot in the other laptop...

Here is the report from boot-info...

[http://paste.ubuntu.com/23657007/](http://paste.ubuntu.com/23657007/)

Can anybody who understand this help please?

thank you in advance

david

---

### Post by oldfred on 2016-12-20
The only thing I see is that you do not have a grub.cfg, but do have a /boot/extlinux/extlinux.conf which is not part of standard Ubuntu.

Best to use your Ubuntu 16.04 installer and add Boot-Repair. The in advanced mode run the full uninstall reinstall of grub. Make sure you have Internet as it has to download new copy of grub to install. And if you manually reconfigured any grub settings, back those up first as it will reset to defaults.

---

### Post by david-k42f on 2016-12-20
> **oldfred said:**
> The only thing I see is that you do not have a grub.cfg, but do have a /boot/extlinux/extlinux.conf which is not part of standard Ubuntu.

Best to use your Ubuntu 16.04 installer and add Boot-Repair. The in advanced mode run the full uninstall reinstall of grub. Make sure you have Internet as it has to download new copy of grub to install. And if you manually reconfigured any grub settings, back those up first as it will reset to defaults.
By "add Boot-Repair" you mean that when I boot in the live session of ubuntu 16.04 and start the installer and in the installer there is an advanced mode where I can do this?

thanks

---

### Post by yancek on 2016-12-20
I believe what oldfred meant was that you boot the Ubuntu DVD/flash drive, go to the boot repair site and download it and run it and use the Advanced Mode in the boot repair options.

---

### Post by Roger_Peartree on 2016-12-20
PLEASE just read this Thread. If you follow the instructions you'll be able to repair your Grub. Here's the link: [http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc) Problem solved.

---

### Post by oldfred on 2016-12-20
You can see all the Boot-Repair options on its site.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I think grub options tab has option to purge & fully reinstall grub.

---

### Post by david-k42f on 2016-12-20
Thank you it worked , I booted a live session of ubuntu 16.04 then installed boot repair on the live session and it was able to repair the grub!!
thank you all for the replies
david

---

