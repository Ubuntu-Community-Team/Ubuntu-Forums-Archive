---
title: "Compaq(HP) mini 311c Long Boot and Freezes after installation"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by grayscale2 on 2014-10-06
Hello guys!
This is some freezes after installation on my netbook and very long boot.
Intel processor 1.6GHz, 2Gb RAM
I tried Ubuntu 14.04 and 14.10 beta x86

Additional information:
[https://www.youtube.com/watch?v=4bJKsVK728g&featu](https://www.youtube.com/watch?v=4bJKsVK728g&featu) - Youtube video of issue 14.04
[https://www.youtube.com/watch?v=SCx7cMLCf9U&feature=youtu.be](https://www.youtube.com/watch?v=SCx7cMLCf9U&feature=youtu.be) - 14.10 ubuntu studio

boot.log: [http://pastebin.com/eUDVAq9c](http://pastebin.com/eUDVAq9c)
top: [http://pastebin.com/TXBP9x9M](http://pastebin.com/TXBP9x9M)
dmesg: [https://yadi.sk/i/461QvdqGbr7XZ](https://yadi.sk/i/461QvdqGbr7XZ)
lightdm.log: [http://pastebin.com/sNRGp7x3](http://pastebin.com/sNRGp7x3)

```
sudo fdisk -l
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb4535672

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 973107199 973105152  464G 83 Linux
/dev/sda2       973109246 976771071   3661826  1,8G  5 Extended
/dev/sda5       973109248 976771071   3661824  1,8G 82 Linux swap / Solaris
```

```
lspci -k | grep -E "VGA|3D"
02:00.0 VGA compatible controller: NVIDIA Corporation ION VGA [GeForce 9400M] (rev b1)[COLOR=#000000][FONT=dejavu sans mono]
[/FONT][/COLOR]
```

---

### Post by Vladlenin5000 on 2014-10-06
You're using the open source graphics driver for nvidia cards/chips - nouveau - and your peculiar integrated nvidia chip probably needs the nvidia's proprietary driver.
Go to System Settings > Software&Updates, click the rightmost tab "Additional Drivers", wait a few moments then select the recommended proprietary one from the list, let it download&install, then reboot.

Please test and report back.

---

### Post by grayscale2 on 2014-10-08
Hello! there are no effect with proprietary drivers, I am going to try old versions of driver

---

### Post by Vladlenin5000 on 2014-10-08
Before that try installing any proposed update.

---

