---
title: "Partitions wiped out on Dell Latitude D410, Cannot Boot or Install"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by arvindpdmn on 2016-08-06
I could not install python-dev on 16.04 LTS on my Dell 32-bit machine due to some version mismatch issue. Tried to solve this but in vain. So decided to reinstall it.

When trying to reinstall 16.04 LTS by overwriting old install, installation failed. It said that disk could not be mounted. Powered off and tried again from live CD. I get error which is below.

---

### Post by ubfan1 on 2016-08-06
Are you sure you're booting off the CD?  Looks like a failed disk boot (expected if you wiped the partitions(.

---

### Post by arvindpdmn on 2016-08-07
ubfan1, thanks. I don't have a CD drive but I'm trying some things using bootable USB.

Today I created a boot repair USB. This did an analysis of my 60 GB HDD. Output is here: [http://paste.ubuntu.com/22653570/](http://paste.ubuntu.com/22653570/)

After doing this, I rebooted without the USB. Instead of getting a blinking cursor as before, now the error is as follows:

Missing operating system.
No bootable devices--strike F1 to retry boot, F2 for setup utility.

(Pressing F1 repeats the above message. I guess MBR is gone.)

---

### Post by ubfan1 on 2016-08-08
Somehow you got the syslinux bootloader onto the hard disk.  I'd try to reinstall grub onto sda.  There are lots of detailed instructions for that here in the forums or at askubuntu.com.

---

### Post by arvindpdmn on 2016-08-08
ubfan1, thanks. Actually, I already had Ubuntu 16.04 LTS working. I wanted to wipe it out and do a fresh install. That's when it failed.

I found some instructions about installing grub ([http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)) but they are specifically talking about dual booting with Windows. Will do some more research and try out.

EDIT:
I see that there is no grub but I can't install it either because commands update-grub and grub-install are not available. I did the mounting as noted in the above link. I think just installing grub will not help because I haven't really installed ubuntu. I was in the process of overwriting my old installation with a fresh one. That when the problem occurred. I guess I need a solution to reinstall Ubuntu. I have full backup of data. So I don't mind wiping everything out.

---

### Post by oldfred on 2016-08-08
Besides no grub.cfg or grub menu, it does not look like you have any kernels, or only a partial install.
Not sure if a total reinstall of grub and kernel or other parts of system also missing.

Boot-Repair's advanced mode has a full uninstall/reinstall of grub and you can tick/check install new kernel also.

---

### Post by arvindpdmn on 2016-08-08
oldfred, I remember checking the advanced options. I found the tabs for grub but the contents were empty and no option to install either.

Anyway, I later got the idea of moving back to 14.04 LTS. So I made another live USB with that version and tried installing it. It worked! So, perhaps 16.04 LTS had a problem or more likely the live USB of 16.04 LTS had some corruption. Perhaps 16.04 LTS would have worked if I burned the ISO again.

I'm happy that I recovered my laptop. For those interested, boot and repair is the one that helped me debug: [https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

Thanks to all for your inputs.

---

