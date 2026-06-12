---
title: "Hal? wants password for windows drive"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Cauda_Draconis on 2008-11-01
I have a problem with mounting my windows drive. It mounts and everything, but the first time I try to get to it after I boot, it asks for my admin password. When I click on it in Dolphin, it comes up with a message that says:
**dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/volume_uuid_C0D8DC0FD8 org.freedesktop.Hal.Device.Volume.Mount string: string: array:string:locale=en_CA.UTF-8** needs administrative privileges. Please enter your password.

This annoys me because it won't access any of my files on my windows drive until I enter the password. It means that, since I keep all my pictures, music, and wallpapers on my windows drive, I have to change my desktop wallpaper every time I log on, and have to reenter the folder for the picture plasmoid. It's really irritating.

Does anyone know how to make it not ask for the password?

---

### Post by taurus on 2008-11-01
How do you mount your Windows drive?  Do you mount it from /etc/fstab?

---

### Post by Cauda_Draconis on 2008-11-01
It seems to automount, but I don't think it's from Fstab. I think it uses whatever the default way is in Intrepid.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=14bd1de2-1a90-4a42-a672-83fc6c78e883 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=baa362c7-55a7-40a7-9ff7-069f4679e927 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

