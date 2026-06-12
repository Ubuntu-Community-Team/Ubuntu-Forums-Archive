---
title: "Installing to USB hard drive"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by ewfjesfjoewijedkljlj on 2006-12-03
I'm trying to install 6.10. I tried to follow the instructions in [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811) but the CD no longer has a rescue option, and there is no longer a directory /etc/mkinitramfs. Plus, it installed grub onto my internal hard drive, even though I'm pretty sure I asked it to install to /dev/sda (the USB drive). What do I have to do to get it working? What do I do to install GRUB on the external USB drive, first of all. Then, what do I need to edit to get Ubuntu booting from the USB drive?

BTW, I did do "sudo grub-install /dev/sda --prefix=/target" once, and it didn't give any errors, but it didn't boot. I have a Dell Inspiron 1150 laptop, which can supposedly boot from USB, although I don't see USB in the one time boot list.

---

### Post by pegazuz on 2006-12-13
> **ewfjesfjoewijedkljlj said:**
> I'm trying to install 6.10. I tried to follow the instructions in [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811) but the CD no longer has a rescue option, and there is no longer a directory /etc/mkinitramfs. Plus, it installed grub onto my internal hard drive, even though I'm pretty sure I asked it to install to /dev/sda (the USB drive). What do I have to do to get it working? What do I do to install GRUB on the external USB drive, first of all. Then, what do I need to edit to get Ubuntu booting from the USB drive?

BTW, I did do "sudo grub-install /dev/sda --prefix=/target" once, and it didn't give any errors, but it didn't boot. I have a Dell Inspiron 1150 laptop, which can supposedly boot from USB, although I don't see USB in the one time boot list.

Did you ever get it to work?  I couldn't even finish an install to my external hard drive.  It always failed during disk preparation even after I finally got drive partitioned using Mepis. Mepis would install fine on my Passport external and installed grub loader on first partition of external hard drive but it couldn't mount boot partition to finish booting and I don't know enough yet to fix that.

I wanted to try Ubuntu cause the live CD had an option to boot from first available hard drive.  This would bring up the grub loader on the external but it still wouldn't boot up.

Since I can't get external to boot up I am looking for a boot cd that will boot up external drive  and then allow external drive to run installed program.

---

### Post by ed_agamemnon on 2006-12-13
i just followed [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28Persistent%29]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28Persistent%29") successfully.

---

### Post by pegazuz on 2006-12-13
> **ed_agamemnon said:**
> i just followed [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28Persistent%29]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28Persistent%29") successfully.

I tried Kubuntu version 6.06 I think and it installed fine and more important it also booted right up with no tweaking or additions.  I figure I would just try use it awhile and learn more about using linux before trying any thing else.  

Any idea why Kubuntu installs with no problem and Ubuntu 6.10 and Puppy linux both failed to install using same process.  I also wonder why Kubuntu wil boot up when Mepis wouldn't.

---

### Post by gn2 on 2006-12-13
The best solution I know for USB installation is PCLinuxOS which can install automatically to USB as part of the standard install process.

---

### Post by pegazuz on 2006-12-13
> **gn2 said:**
> The best solution I know for USB installation is PCLinuxOS which can install automatically to USB as part of the standard install process.

I tried this PCLinux OS  and its Minime version too on USB drive.  It works great on my home made desktop that is three years old, but would not even boot up on my new Acer Laptop for reasons I don't understand.  Maybe a newer version might work in the future?

---

### Post by gn2 on 2006-12-14
> **pegazuz said:**
> I tried this PCLinux OS  and its Minime vesrion too on USB drive.  It works great on my home made desktop that is three years old, but would not even boot up on my new Acer Laptop for reasons I don't understand.  Maybe a newer version might work in the future?

Strange, did you try the various boot options?

---

