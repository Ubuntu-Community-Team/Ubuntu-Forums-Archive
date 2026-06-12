---
title: "Manually build USB-stick with syslinux cannot copy from cdrom (iso file) Ubuntu 18.04"
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by cbiethmann on 2019-01-23
My task is to install ubuntu server 18.04 LTS on several machines. My idea was to build an USB stick with the iso-image. I followed the instructions from [https://help.ubuntu.com/lts/installation-guide/i386/ch04s03.html](https://help.ubuntu.com/lts/installation-guide/i386/ch04s03.html). To easily cp the iso-image and the preseed.cfg file to the stick alongside with the install image I used the instructions under 4.3.3. As installer image I used the files from [http://archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/bionic/main/installer-amd64/current/images/hd-media/).

The USB-stick boots perfectly and is reading the preseed.cfg file. But when trying to load the packages from the iso-image it throws a error-message.

> There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.

Failed to copy file from CD-ROM. Retry?

When dumping the log to the stick and viewing the syslog the following lines are included.

```
...
Jan 23 13:27:04 cdrom-retriever: warning: Unable to find main/debian-installer/binary-amd64/Packages in /cdrom/dists/bionic/Release.
Jan 23 13:27:04 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-amd64/Packages in /cdrom/dists/bionic/Release.
Jan 23 13:27:04 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-amd64/Packages.gz in /cdrom/dists/bionic/Release. 
...
```

The installer is searching for a directory named 'debian-installer' which is not part of the iso-image. The path in the iso-image for ubuntu 18.04 LTS is 'main/binary-amd64/' as written in the Release-file.

```
...
 4a4dd3598707603b3f76a2378a4504aa       20 restricted/binary-i386/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e        0 restricted/binary-i386/Packages
...
 4a4dd3598707603b3f76a2378a4504aa       20 main/binary-i386/Packages.gz
 d41d8cd98f00b204e9800998ecf8427e        0 main/binary-i386/Packages
...


```

Am I using the wrong installer-image? Is there a way to fix this problem? Or is there a better solution to accomplish an automated install from usb-stick?

I appreciate any suggestions.

---

### Post by cbiethmann on 2019-01-29
After a few days of resource I managed to make a automated install. Just wanted to share my experience.

First I used the wrong cd-image and the wrong installer-image. To be precise I used the new Ubuntu live installer instead of the debian one. The debian installer is the alternative installer when downloading an ubuntu image.

After getting the right cd-image I customized it with the preseed.cfg file. The file worked as expected just by following the documentation. ([https://help.ubuntu.com/lts/installation-guide/amd64/apb.html](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html))
To customize the image I copied the cd to a new folder made my changes and build a new iso-file from it.

```

mkdir ./myimage
sudo mount path/to/image.iso /mnt
sudo cp -rT /mnt ./myimage
sudo cp preseed.cfg ./myimage

```

Before building the new file one has to modify the boot-parameters for the installer to use the preseed.cfg file. The boot-parameters can be found in "isolinux/txt.cfg".

> 
default install
label install
  menu label ^Install Ubuntu Server
  kernel /install/vmlinuz
  append  file=/cdrom/preseed.cfg auto=true priority=critical initrd=/install/initrd.gz ---


If one wants to start the debian installer immediately without waiting 30 seconds to choose the default language and entry, one can modify the "isolinux/isolinux.cfg" and set the timeout to 0.1 seconds with the following line.

> 
timeout 1


Now building the new iso-image.

```

sudo mkisofs -D -r -V "Iso Label" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ./newimage.iso ./myimage
sudo isohybrid ./newimage.iso

```

To work from a usb-stick just copy the image to the device, where sdX is the device name for the usb-stick.

```

sudo cp ./newimage.iso /dev/sdX
sync

```

Now plug the usb-stick in the desired server and boot into the debian installer. If the preseed.cfg file is correct the install will work without any user interaction.

---

