---
title: "Edgy Install using Netboot and Alternate Install ISO CD"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by marquivon on 2007-01-31
Hi

I've spent a good amount of time figuring out how to use the Alternate Install CD and the Netboot Kernel to do the Ubuntu Installation; and have been unsuccessful.

I'm in a network where there are 8 PCs on which Ubuntu Edgy needs to be installed (sole installation, no dual boot). None of the machines have a CD Drive, so I made a USB Drive bootable and copied the Ubuntu Netboot Kernel on it and was able to successfully boot the machines. Second, I downloaded the Alternate Install ISO and copied the dists/ and pool/ to my web server's directory which can be accessed via [http://10.0.0.1/ubuntu](http://10.0.0.1/ubuntu).

Now when I start the installation and provide the my own mirror ([http://10.0.0.1/ubuntu](http://10.0.0.1/ubuntu)) the files start to copy. However, it gives an error while copying the file
/ubuntu/pool/main/l/linux-source-2.6.17/cdrom-core-modules-**2.6.17-10-386-di_2.6.17.1-10.34_i386**.udeb
The version that is available in the repository is
/ubuntu/pool/main/l/linux-source-2.6.17/cdrom-core-modules-**2.6.17-10-386-di_2.6.17-10.33_i386**.udeb

I'm not sure why exactly it is asking for that particular file when a previous version exists and I've not specified any outside mirrors from which the files should be downloaded. There's no mention of cdrom-core-modules-2.6.17-10-386-di_2.6.17.1-10.34_i386.udeb in the dists/ directory too. 

Even if I somehow download all the files required by it using an online Ubuntu Repository (it keeps on asking for ~20-25 packages), at nearly the end it gives an error linux-image-generic could not be installed! In the logs it mentions that it could not be authenticated and -f was used without --force-yes.

I don't know whether it is even possible to do an installation in this manner? This has always prevented me to do fast Ubuntu installations on a larger scale.

Any help/pointers would be appreciated.

Thanks

Vivek Kapoor

---

### Post by marquivon on 2007-02-01
Atlast I was able to figure out how to do Network Installation of Edgy without DHCP, without a CD Drive and using the ISO provided by Ubuntu.

The softwares that you may need to download are **syslinux, mtools, ms-sys**

Following are the steps
**Step A.** Make a Bootable USB Pen Drive
[LIST=1]
[*]Partition the USB Drive and make the partition bootable using fdisk. Make sure the partition that you'd make bootable is a Win95Fat16 one (Mode **e** in fdisk). The link [http://linux.web.psi.ch/livecd/usbdisk.html](http://linux.web.psi.ch/livecd/usbdisk.html) was of big help.
[*]Now put Win95 MBR in the drive by using **ms-sys -9 /dev/sda1**
[*]Format that partition using **mkdosfs /dev/sda1**
[*]Make it bootable using syslinux by typing **syslinux /dev/sda1**
[*]Download the Netboot Kernel for Edgy and extract **initrd.gz** and **linux**. The URL is [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)
[*]Mount the USB Drive's Parition through **mount /dev/sda1 /media/usbdisk**. Copy the initrd.gz and linux onto the parition
[*]Create a file called syslinux.cfg inside the parition and add the following values into it
```

DEFAULT netboot

LABEL netboot
 menu label ^Start Ubuntu via Netboot
 kernel linux
 append initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --

```
[*] So essentially there'd be only 4 files inside the USB Drive, viz. initrd.gz , ldlinux.sys , linux , syslinux.cfg
[/LIST]

**STEP B** : On your Web Server, mount the ISO and make it available
[LIST=1]
[*] cd /var/www
[*] mkdir ubuntu
[*] mount -o loop /path/to/ubuntu-6.10-alternate.iso /var/www/ubuntu
[*] This should be accessible via [http://yoursystemIP/ubuntu](http://yoursystemIP/ubuntu)
[/LIST]

**STEP C** : Boot using the USB and start the installation
Now there are two problems.
(a) If you start the Edgy Installation using the netboot kernel, it'll search for archive.ubuntu.com and get the Release files from there. If the Release file that is available at archive.ubuntu.com is later than what's available on the CD, then you'll face problems while downloading packages. So, the network installation will fail if you use the CD as the repository.
(b) The linux-image-kernel which is available in the CD, probably does not have correct GPG key/md5sum. Due to which later in the installation it gives an error that it could not be authenticated and the installation fails.

The solution to both the problems above is covered below

[LIST=1]
[*] Boot using the USB. You should be able to see the installation screen where it asks for the Language. If not, try the Ubuntu Wiki where booting using the USB is explained alongwith the Netboot Kernel Image.
[*] Proceed through the normal installation steps. Once the Network Configuration step comes, if you've a DHCP server, it'll automatically pickup the IP Address. Don't let that happen (Press Cancel). If the DHCP Config is done and it asks for the system's name, click **Go Back** and configure the network manually.
[*] If you have the details about the IP Address, well and good, else on the VT2, type **ifconfig** and **route -n** to know about the IP Address, Subnet Mask and the Gateway
[*] **Don't Provide the DNS Entry** as it will allow the system to go through internet and get connected to archive.ubuntu.com which we do not want.
[*] While asked for mirror from which to do the installation, go to the Top and add the information manually.
[*] Once the Base Installation is in progress, switch to Virtual Terminal 2, by pressing ALT+F2. Press ENTER and add the following
**echo 'APT::Get::AllowUnauthenticated "true";' >>/target/etc/apt/apt.conf**
(All Credit goes to dixonp who suggested the same here -> [http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343))
This will ensure that no GPG Related issues pop-up and installation happens smoothly.
[/LIST]

That's it. This will help you in a scenario where
[LIST]
[*]Bandwidth is limited and you don't want to connect to Internet everytime you need to do the installation
[*]You were able to get an Alternate Install ISO (or a CD), but there are no CD Drives on the machines you wish to install Ubuntu
[*]You wish to do fast Ubuntu Installations but they should be interactive (Otherwise you can look into Kickstart Installs)
[*]The DHCP network is not in your control to setup a PXE Install
[/LIST]

---

