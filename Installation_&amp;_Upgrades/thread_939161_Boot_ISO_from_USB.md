---
title: "Boot ISO from USB"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by linko47 on 2008-10-05
I have a Lenovo X61 with no optical drive.  Here is the solution to booting ISO's. (Taken from ubuntu-eee)

Remember to replace sdb1 with wherever your flash drive is located.  Check using "sudo fdisk -l"

```
sudo apt-get install syslinux mtools
```

Download isotostick.sh
```
wget http://startx.ro/sugar/isotostick.sh
```

Make the script executable
```
chmod +x isotostick.sh
```

Format your flash drive. (mine is sdb1)  You can check via "sudo fdisk -l"
```
sudo mkdosfs -F 32 -n <give your flash drive a name> /dev/sdb1
```

Remember; sdb, not sdb1:
```
sudo parted /dev/sdb set 1 boot on
```

Transfer the image to your flash drive:
```
sudo ./isotostick.sh <path to your image.iso> /dev/sdb1
```

Install syslinux
```
sudo syslinux /dev/sdb1
```

[http://www.ubuntu-eee.com/wiki/index.php5?title=Install:_from_a_Live_Ubuntu_image_on_a_USB_stick](http://www.ubuntu-eee.com/wiki/index.php5?title=Install:_from_a_Live_Ubuntu_image_on_a_USB_stick)

---

