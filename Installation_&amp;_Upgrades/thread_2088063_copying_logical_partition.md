---
title: "copying logical partition"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2012-11-25
I have an install on say sda6. I would like to 'copy" this to say sda8.
The reason, is to have a working backup of the partition, so if I do an upgrade or install new app, and it fails, I could always boot to working copy (ala time machine almost) But I believe since their are uids used in many places, not too mention boot loader, this is not possible?

swap is on its own partition.

---

### Post by ibjsb4 on 2012-11-25
One way you can do this is with [clonezilla]("http://clonezilla.org/").

And your right, you must change the uuid after you clone or it will reak havock with the original.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+uuid&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+uuid&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by coffeecat on 2012-11-25
> **pjmlmas said:**
> I have an install on say sda6. I would like to 'copy" this to say sda8.
The reason, is to have a working backup of the partition, so if I do an upgrade or install new app, and it fails, I could always boot to working copy (ala time machine almost) But I believe since their are uids used in many places, not too mention boot loader, this is not possible?

This is easily done, and moreover can be done with a simple file copy using the terminal command "cp". Ignore the naysayers who say it is not possible using cp. I have done something similar many times. But you are right - you must take into account the UUID of sda8.

This is what I would do, and I am assuming that you have already formatted sda8 with the same filesystem as sda6 (ext3 - ext3; ext 4 - ext4) and that it is empty. I'm also assuming that sda6 is your working installation and that is what you boot into at present.

[list=1]
[*]Boot up with a live CD or live USB. You cannot copy the contents of sda6 while you running a system which is on sda6.

[br][/br]
[*]Mount sda6 and sda8. For illustration I'll assume you've mounted sda6 on /media/sda6 and sda8 on /media/sda8. Adjust the commands below as appropriate. Run:

```
sudo cp -av /media/sda6/* /media/sda8/
```

The -a option ensures a recursive copy with all ownerships, permissions, attributes preserved. The -v option reassures you that something is going on since this will take a little while!

[br][/br]
[*]Now run:

```
sudo blkid
```

... to determine the UUID of sda8.

[br][/br]
[*]Now:

```
gksu gedit /media/sda8/etc/fstab
```

**EDIT**: apologies, you are using Xubuntu. Gedit will work with the Ubuntu CD. If you are using a live session of Xubuntu, this should work in lieu of the gedit line:

```
gksu leafpad /media/sda8/etc/fstab
```

**END-EDIT**

And edit the root (/) line so that it has the sda8 UUID, not the sda6 one. While you are in /etc/fstab, check that the swap partition UUID is the same as what you saw from blkid. Save and exit.

[br][/br]
[*]Reboot. Your sda6 grub menu will not yet have an entry for the sda8 "clone". After you have logged in, run:

```
sudo update-grub
```

This will include an entry for your new sda8 "clone" system. Reboot and choose the sda8 system from the grub menu. It may not be clear which this is - it won't be the first one. If you are unsure, highlight the grub entry you think it is and press 'e' to see which partition it is referring to.

[br][/br]
[*]Once you have booted into your sda8 system and checked that everything is working, you can re-install grub with:

```
sudo grub-install /dev/sda
sudo update-grub
```

When you now reboot, the sda8 installation will be first in the grub menu and the sda6 one will be further down the list.

[/list]

Any problems - post back. :)

---

### Post by pjmlmas on 2012-11-25
I am going to try the cp command. clonezilla I need to worry about partitions sizes, not actually usuage.

If cp works, I could use rsync in the future, and just remember live usb and uuid fix before booting sda8?

---

