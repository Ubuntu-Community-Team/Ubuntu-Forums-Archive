---
title: "PXE - No network in initramfs on new machines"
date: 2021-11-10
forum: Installation &amp; Upgrades
---

### Post by Flauschie on 2021-11-10
[SIZE=3]**SOLUTION:** [https://ubuntuforums.org/showthread.php?t=2468782&page=2&p=14068121#post14068121](https://ubuntuforums.org/showthread.php?t=2468782&page=2&p=14068121#post14068121)
[/SIZE]

I want to give a short intro in what is happening. We are deploying 18.04 desktop via a complex preseed using the netboot kernel/ramdisk. After a few month break we went into issues deploying new machines (i.e. Latitude 7420) with 18.04 which was working fine until this point. After a few days of headache I was able to fix the install it by using the most recent focal [grubnetx64.efi.signed]("http://archive.ubuntu.com/ubuntu/dists/focal/main/uefi/grub2-amd64/current/grubnetx64.efi.signed"). Now the **deployment of 18.04 and 20.04.3 is working on older machines. **18.04 is working on recent machines, too, **but 20.04 fails on i.e. a Latitude 7420.**


**Today**
- Windows Server DHCP configured to serve grubnetx64 to UEFI clients or pxelinux to legacy clients based on architecture codes
- Ubuntu server running tftp and apache to serve the files
- New (and old) machines with network connection via Thunderbolt (USB-C) DA300 / or Docking station


On our most recent machines the installation fails after loading the kernel and ramdisk (extracted vmlinuz and initrd from [ubuntu-20.04.3-live-server-amd64.iso]("https://releases.ubuntu.com/20.04/ubuntu-20.04.3-live-server-amd64.iso")). I changed nearly all bios settings I can think of but to no avail.


I am running into the following error after loading the kernel and ramdisk (which indicates the network connection was working properly until this point)
```

No broadcast interfaces found - exiting.
no search or nameservers found in /run/net-.conf /run/net-*.conf /run/net6-*.conf
Begin: Running /scripts/casper-premount ... done.
done.
Begin: Trying netboot from : ... Begin: Trying to download and mount http://11.11.11.11/preseed/focal/ubuntu-20.04.3-live-server-amd64.iso ... Connecting to 11.11.11.11 (11.11.11.11:80)
wget: can't connect to remote host (11.11.11.11): Network is unreachable
done.
Unable to find a live file system on the network

```


This is the grub config for 20.04 which works on "older" machines but results in the error above on a i.e. Latitude 7420
```

menuentry "Ubuntu 20.04.3 Server Live Installer" {
    echo "Loading Kernel..."
    linux /ubuntu20.04_liveserver/vmlinuz ip=dhcp url=http://11.11.11.11/preseed/focal/ubuntu-20.04.3-live-server-amd64.iso root=/dev/ram0 cloud-config-url=/dev/null
    echo "Loading Ram Disk..."
    initrd /ubuntu20.04_liveserver/initrd
}


menuentry "DEVDEVDEV Ubuntu 20.04.3 Server Live Installer - automated" {
    echo "Loading Kernel..."
    # make sure to escape the ';' or surround argument in quotes
    linux /ubuntu20.04_liveserver/vmlinuz ip=dhcp url=http://11.11.11.11/preseed/focal/ubuntu-20.04.3-live-server-amd64.iso autoinstall ds="nocloud-net;s=http://11.11.11.11/preseed/focal/" root=/dev/ram0 cloud-config-url=/dev/null
    echo "Loading Ram Disk..."
    initrd /ubuntu20.04_liveserver/initrd
}

```


Do you have any idea how to fix the networking issue for the ramdisk? Is it maybe a driver thing?

Best regards
Flausch


[SIZE=3]**SOLUTION:** [https://ubuntuforums.org/showthread.php?t=2468782&page=2&p=14068121#post14068121](https://ubuntuforums.org/showthread.php?t=2468782&page=2&p=14068121#post14068121)[/SIZE]

---

### Post by i-cat on 2021-11-10
The web address is unreachable. This means the website url is down.

---

### Post by Flauschie on 2021-11-10
> **i-cat said:**
> The web address is unreachable. This means the website url is down.

As I have written it is working on older machines... So no, the url is in fact not down.


Today I checked and it looks like it cannot get a network adapter since ipaddr show only brings up the loopback device. I guess it is a driver issue then?

---

### Post by i-cat on 2021-11-10
Let me Check the developer builds.
Just confirming
> The 18.04 Worked on the new mashine? [COLOR=#000000](i.e. Latitude 7420)
[/COLOR]> You are in stalling the 20.04 from [http://cdimage.ubuntu.com/ubuntu-server/focal](http://cdimage.ubuntu.com/ubuntu-server/focal) 

after changing grub did you run the command 
" sudo update-grub "
?

Thanks - I-Cat

---

### Post by Flauschie on 2021-11-10
> **i-cat said:**
> Let me Check the developer builds.
Just confirming
> The 18.04 Worked on the new mashine? [COLOR=#000000](i.e. Latitude 7420)
[/COLOR]> You are in stalling the 20.04 from [http://cdimage.ubuntu.com/ubuntu-server/focal](http://cdimage.ubuntu.com/ubuntu-server/focal) 

after changing grub did you run the command 
" sudo update-grub "
?

Thanks - I-Cat

I guess you registered fresh and just try to get points (looking through your answers so far). There is no real point in answering these questions. I need constructive feedback and help.
Do you even know how any of this works?

---

### Post by i-cat on 2021-11-10
I am a developer.

---

### Post by Flauschie on 2021-11-11
Ok, found out this could be a driver issue because it is loading the generic cdc_ether as it seems. Unfortunately initramfs is heavily limited in its abilities so I don't know how to properly check the devices in this state. But I went a step further started the live server installation via a usb stick and checked lsusb, lsmod, lshw. The results are below.

**EDIT: **Alright. The installer seems to load another extra modules due to it working properly there. I wanted to try rebuilding the initrd but the sources/guides are outdated and don't match files/folders in ubuntu 20 anymore. Does anyone know how to unpack, add the necessary modules and pack it again?

lsusb
```

Bus 006 Device 005: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter

```

lsmod (relevant entries for RTL8153)
```

r8153_ecm              16384  0
cdc_ether              20480  1 r8153_ecm
usbnet                 49152  2 r8153_ecm,cdc_ether
r8152                  81920  1 r8153_ecm

```

lshw -class network
```

  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       bus info: usb@6:2.4
       logical name: eth0
       serial: 
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=full firmware=rtl8153b-2 v1 10/23/19 link=no multicast=yes port=MII speed=1Gbit/s
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       bus info: usb@6:2.1.2
       logical name: enxa02919a989cd
       serial: 
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.11.11 duplex=half firmware=rtl8153b-2 v1 10/23/19 link=no multicast=yes port=MII speed=10Mbit/s

```

---

### Post by kramork on 2021-11-16
[https://ubuntuforums.org/showthread.php?t=2468967](https://ubuntuforums.org/showthread.php?t=2468967)
here is the same problem, we are looking for a solution

---

### Post by MAFoElffen on 2021-11-17
What are you using as the pxe boot vmlinuz and initrd files and where are they from? Do those same machines boot directly from those if it was on an ISO? Do these machines boot PXE without extra helpers? (because of their NIC's) Basically, is the pre-ample PXE handshake completed...

What does your PXE Boot Menu /netboot/tftp/pxelinux.cfg/default contain as entries?

From what it sounds like, is that the basic image does not support the hardware on what you are trying to boot right? This is why the vmlinuz and intrd files are usually from a LiveCD installation ISO, so that they are generic in the hardware they support...

Just thinking out loud...

---

### Post by kramork on 2021-11-21
in my case vmlinuz and initrd are taken from the installation discs. and they do not support usb network cards
everything is detailed here
[https://ubuntuforums.org/showthread.php?t=2468967](https://ubuntuforums.org/showthread.php?t=2468967)

---

### Post by Flauschie on 2021-11-22
I found a (for me) working solution. This is STC until kernel 5.13 arrives (hopefully as HWE) which [officially supports these chips]("https://www.phoronix.com/scan.php?page=news_item&px=Realtek-RTL8153-RTL8156-Linux")
You have to rebuild the initrd and include the drivers

[Source 1]("https://askubuntu.com/questions/1079240/ubuntu-18-04-pxe-booting-with-realtek-r8152-based-nic-no-interface-found")
[Source 2]("https://ubuntuforums.org/showthread.php?t=1843448")

The guide is pretty old. The resulting initrd differs in size and the binwalk differs greatly due to the way its packed. I don't get into my mind that it seems like nothing is being documented properly anywhere but stuff gets changed everywhere since subiquity... But it works and the network adapter is found.


[Repack initrd]("https://superuser.com/questions/1556241/initrd-file-cpio-archive-x-cpio-type-of-file-how-to-recompile")

My solution
```

mkdir /mnt/isofiles/
mount -o loop ubuntu-20.04.3-live-server-amd64.iso /mnt/isofiles


mkdir /tmp/newinitrd
cd /tmp/newinitrd


#Unpack initrd
unmkinitramfs /mnt/isofiles/casper/hwe-initrd .


#Extract drivers
cd /tmp/newinitrd/main/usr
dpkg-deb --fsys-tarfile /mnt/isofiles/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-27-generic_5.11.0-27.29\~20.04.1_amd64.deb | tar -x ./lib/modules/5.11.0-27-generic/kernel/drivers/net/usb/cdc_ether.ko
dpkg-deb --fsys-tarfile /mnt/isofiles/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-27-generic_5.11.0-27.29\~20.04.1_amd64.deb | tar -x ./lib/modules/5.11.0-27-generic/kernel/drivers/net/usb/usbnet.ko
dpkg-deb --fsys-tarfile /mnt/isofiles/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-27-generic_5.11.0-27.29\~20.04.1_amd64.deb | tar -x ./lib/modules/5.11.0-27-generic/kernel/drivers/net/usb/r8152.ko
dpkg-deb --fsys-tarfile /mnt/isofiles/pool/main/l/linux-hwe-5.11/linux-modules-extra-5.11.0-27-generic_5.11.0-27.29\~20.04.1_amd64.deb | tar -x ./lib/modules/5.11.0-27-generic/kernel/drivers/net/usb/r8153_ecm.ko


# Rebuild dependencies
cd /tmp/newinitrd/main/usr
depmod -b `pwd` 5.11.0-27-generic


cd /tmp/newinitrd


touch hwe-initrd-new


cd early
find . -print0 | cpio --null --create --format=newc > /tmp/newinitrd/hwe-initrd-new


cd ../early2
find kernel -print0 | cpio --null --create --format=newc >> /tmp/newinitrd/hwe-initrd-new


cd ../main
find . | cpio --create --format=newc | xz --format=lzma >> /tmp/newinitrd/hwe-initrd-new


```

---

### Post by MAFoElffen on 2021-11-22
But... You are using the 20.04.x Server Llve Installer ISO... Ubuntu 18.04 (Desktop and Server) ISO was the debain-installer and used preseed files. Ubuntu 20.04.x... Desktop is the debain-installer.   The 20.04.x Server is not debian-installer and was changed to the Live Installer, using yaml installer scripts.The 20.04.x Network boot is DHCP (ports 67 & 68) and TFTP (port 69)... But I am not going to get into those distractions...

Dell says there are only a few select USBA and USBC Network adapters that work with the Dell Latitude 7420 that will work with it to PXE Boot.

Here is Dell's support page on setting the BIOS options on it (once you have one of those USB Network adapters connected: 
[https://www.dell.com/support/kbdoc/en-ca/000131551/bios-settings-to-allow-pxe-boot-on-newer-model-dell-latitude-laptops](https://www.dell.com/support/kbdoc/en-ca/000131551/bios-settings-to-allow-pxe-boot-on-newer-model-dell-latitude-laptops)
[https://www.dell.com/support/kbdoc/en-us/000150882/how-to-implement-pxe-booting-from-usb-c-and-thunderbolt-ethernet-adapters](https://www.dell.com/support/kbdoc/en-us/000150882/how-to-implement-pxe-booting-from-usb-c-and-thunderbolt-ethernet-adapters)

Here is their recommended USB-A Network Adapter: [https://www.dell.com/en-us/shop/dell-adapter-usb-30-to-ethernet-pxe-boot/apd/443-bbbd/pc-accessories](https://www.dell.com/en-us/shop/dell-adapter-usb-30-to-ethernet-pxe-boot/apd/443-bbbd/pc-accessories)

Here is their recommended USB-C Network Adapter: [https://www.dell.com/en-us/shop/dell-adapter-usb-c-to-ethernet-pxe-boot/apd/470-abnd/pc-accessories](https://www.dell.com/en-us/shop/dell-adapter-usb-c-to-ethernet-pxe-boot/apd/470-abnd/pc-accessories)

---

### Post by Flauschie on 2021-11-22
> **MAFoElffen said:**
> But... You are using the 20.04.x Server Llve Installer ISO

The whole thread is about using the server installer with new (most recent) dell machines (as figured out using the driver mentioned in this thread). And yes, I want to deploy Ubuntu Desktop with it since there is no way to automate the Desktop 20 setup properly (props to the change which wasn't wanted by anyone... probably) since soon even the netboot/mini.iso is gone. Old (<1GB needed) vs New (>3GB ram needed).

> **MAFoElffen said:**
> 
[COLOR=#000000]Ubuntu 18.04 (Desktop and Server) ISO was the debain-installer and used preseed files.[/COLOR]


Correct. This setup wasn't affected by this change (which is weird but I guess this is due to a heavily trimmed down initrd)

> **MAFoElffen said:**
> 
[COLOR=#000000]Ubuntu 20.04.x... Desktop is the debain-installer.[/COLOR]


Is it? I cannot find any source hinting I can use my existing 18.04 desktop preseed setup properly with 20.x. I would prefer to do that because the way one has to do it now is imperfect, not wanted and resource heaviy (how to deploy a <4GB machine if I need to download a 3GB+ image for desktop?). Furthermore I have to manipulate the network adapter since it differs from the server one. Great.

> **MAFoElffen said:**
> 
[COLOR=#000000]The 20.04.x Server is not debian-installer and was changed to the Live Installer, using yaml installer scripts.The 20.04.x Network boot is DHCP (ports 67 & 68) and TFTP (port 69)... But I am not going to get into those distractions...[/COLOR]


Correct. 20.X server is yaml aka subiquity. Network boot wasn't working no matter DHCP settings (I dont even know why you mentioned it) because the correct driver was missing. Good that you didn't get into that.

> **MAFoElffen said:**
> 
[COLOR=#000000]Dell says there are only a few select USBA and USBC Network adapters that work with the Dell Latitude 7420 that will work with it to PXE Boot.[/COLOR]


Doesn't matter what Dell says as long as the correct drivers are missing and therefore not being loaded. That's why I had to modify the ramdisk to load the drivers (since there is only USB-C in the most recent machines). My guide sticks and I don't know how you answer is helpful in any way. Sorry.

---

