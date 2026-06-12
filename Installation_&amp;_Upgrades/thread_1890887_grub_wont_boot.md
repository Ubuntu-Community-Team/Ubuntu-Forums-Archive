---
title: "grub wont boot"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by zicodani on 2011-12-04
I have just performed an update on ubuntu 11.10. Now I cannot boot either from a CD or from the hard drive. The initial boot screen comes up, then a flashing cursor, and then my monitor says "cannot display this video mode". I tried another monitor and it doesnt work either. Could the update have messed up the graphics card? Any help would be much appreciated. Thanks

---

### Post by MAFoElffen on 2011-12-04
> **zicodani said:**
> I have just performed an update on ubuntu 11.10. Now I cannot boot either from a CD or from the hard drive. The initial boot screen comes up, then a flashing cursor, and then my monitor says "cannot display this video mode". I tried another monitor and it doesnt work either. Could the update have messed up the graphics card? Any help would be much appreciated. Thanks
More likely that it messed up the graphics driver.  Do you know your video card?

No boot from a CD?  Do you get the BIOS Messages displayed? If you do, go into Bios settings and verify the boot order. Desktop or Laptop? If laptop > poweroff > disconnect charger > pull battery for 20seconds > put battery in > connect charger > turn on... If desktop > Powerdown > turn off atx power switch > powerdown moniter > disconnect power cords for CPU and monitor > disconnect network cable > if not integrated video, unseat the card > wait 20 seconds > connect everything back in the reverse order > turn on monitor > turn on atx powersupply > turn on CPU...

... Hold down shift key > at grub menu, select recovery boot option > select boot safemode/low graphics > reinstall drivers.

---

### Post by zicodani on 2011-12-04
Many thanks for the reply. I shall respond to your questions in turn

> **MAFoElffen said:**
> More likely that it messed up the graphics driver.  Do you know your video card?
[B]
Nvidea Geforce 7025[/B]

No boot from a CD?  Do you get the BIOS Messages displayed? If you do, go into Bios settings and verify the boot order. 

**I get the BIOS messages, and I can access the BIOS settings. I verified the boot order**

Desktop or Laptop? If laptop > poweroff > disconnect charger > pull battery for 20seconds > put battery in > connect charger > turn on... If desktop > Powerdown > turn off atx power switch > powerdown moniter > disconnect power cords for CPU and monitor > disconnect network cable > if not integrated video, unseat the card > wait 20 seconds > connect everything back in the reverse order > turn on monitor > turn on atx powersupply > turn on CPU...

**It is a desktop, and I carried out the instructions above, but no effect**

... Hold down shift key > at grub menu, select recovery boot option > select boot safemode/low graphics > reinstall drivers.

**If I hold the shift key down, it says GRUB loading, with a flashing cursor below, then the screen goes blank. I tried another monitor, and the screen says "Cannot display this Video Mode", so it seems I cannot access the GRUB screen**

---

### Post by MAFoElffen on 2011-12-04
> **zicodani said:**
> Many thanks for the reply. I shall respond to your questions in turn

**If I hold the shift key down, it says GRUB loading, with a flashing cursor below, then the screen goes blank. I tried another monitor, and the screen says "Cannot display this Video Mode", so it seems I cannot access the GRUB screen**

You'er going to need to get to a grub menu to add a "nomodeset" option, to be able to boot, to be able to reinstall your graphics driver...

Follow these directions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]
You want to use "nomodeset" to boot the LiveCD. That is the first half of that post.

The second half of that post is directions to mount your installed system. Go ahead and do that.  When mounted, then do:
```

apt-get update
nvidia-installer --uninstall
apt-get remove nvidia-*
apt-get install linux-headers-'uname -r'
apt-get install nvidia-current  
nvidia-xconfig  
echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf[FONT=monospace]
[/FONT]update-initramfs -u

```After that then go to the installed /etc/default/grub and edit it like this:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")[/SIZE][/COLOR][/SIZE][/COLOR]

Modify the commands in that taking off sudo and gksudo, as you were still in the chroot. To get out of the chroout, type "exit". Then 
```

sudo umount /mnt

```Then reboot.

Tell me how it goes.

---

### Post by zicodani on 2011-12-05
thanks a lot for this....I shall get to work on it today and get back to you

---

### Post by zicodani on 2011-12-05
Thanks a lot for the help. In the end, for some reason, it was able to boot from an external CD drive, and I could copy my files  on to an external hard drive, and reinstall Ubuntu 10, which I prefer because it seems a little quicker, and I have no interest in Unity right now, especially with my low spec equipment. Thanks a lot again.

---

