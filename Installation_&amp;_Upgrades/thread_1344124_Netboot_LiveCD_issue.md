---
title: "Netboot LiveCD issue"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Stormblazer on 2009-12-02
First, some background.
I recently bought an HP Mini 110 netbook. I'd like to resize the NTFS partition it came with so that I can dual-boot a linux partition (undecided on a particular distro yet).

Ordinarily, I'd just boot up a liveCD like Knoppix or UbuntuLive... unfortunately, netbooks don't really come with CD drives.

I've tried every USB stick in my house, with several methods including unetbootin and other liveUSB options - none of it worked, it would either outright fail to boot or it would error out and crash before it even managed to finish the bootloader.

So I've decided to try a network boot - which has been a nightmare. No two guides I have found are consistent on how to do this, it's mind-boggling. I have never seen such utter inconsistency on anything pertaining to linux before.

After several failed attempts at using an NFS root on my main PC to boot the live CD of ubuntu (failed because it couldn't mount any root drives after loading the initial ramdisk) along with several other failed attempts using different distros and guides, I'm at a loss here.

Does anyone know a simple clear-cut way to network boot the Ubuntu LiveCD from my PC (which has a CD drive) onto my netbook? If it helps any, my router (tomato) is capable of routing the network boot over to a TFTP server, it has a sort of built-in dnsmasq daemon, and I already have static DHCP routing based on MAC addresses.

---

### Post by darkod on 2009-12-02
I can't help with the rest except maybe with unetbootin. Was there any particular error or reason it didn't work? That's exactly how I installed on my netbook.

---

### Post by gravyflex on 2009-12-02
Are you using the tftp server on tomato? 

In my setup I am using DD-WRT and I point the tftp server to the ip address of my desktop which has tftpd-hpa running.

One thing to look out for with dnsmasq is that you are using the dns option: 

dhcp-boot=pxelinux.0,,10.0.0.1. 

I was using a dhcp option for about a month. No surprise it did not work. I have some notes here that might be useful [http://gravyflex.blogsopt.com](http://gravyflex.blogsopt.com).

---

### Post by Stormblazer on 2009-12-02
> **darkod said:**
> I can't help with the rest except maybe with unetbootin. Was there any particular error or reason it didn't work? That's exactly how I installed on my netbook.
I tried using a simple 1GB USB stick and a 4GB SD Card.
In the latter case, it flat out did not work - the system simply wouldn't boot from the SD card at all, no errors, just nothing.

In the case of the 1GB stick, I tried with both ubuntu 9.10 desktop ISO and the most recent core Arch Linux ISO, and I've also tried the liveUSB Arch Linux img file by raw-writing it to the 1GB usb stick.

None of these worked - unfortunately I can only remember the most recent error, which was with the img liveUSB file - it went to start grub, and simply stated it couldn't load the stage1 (or was it stage2?) file, and stalled.

---

### Post by Stormblazer on 2009-12-02
> **gravyflex said:**
> Are you using the tftp server on tomato? 

In my setup I am using DD-WRT and I point the tftp server to the ip address of my desktop which has tftpd-hpa running.

One thing to look out for with dnsmasq is that you are using the dns option: 

dhcp-boot=pxelinux.0,,10.0.0.1. 

I was using a dhcp option for about a month. No surprise it did not work. I have some notes here that might be useful [http://gravyflex.blogsopt.com](http://gravyflex.blogsopt.com).
The line in tomato simply reads:
dhcp-boot=pxelinux.0,,192.168.1.5

The tftp server was run via dnsmasq on my main PC (running a temporary install of arch linux on a spare partition). I tried using tftp-hda but couldn't get it to work (followed instructions to set it up through xinetd, but it simply wouldn't work, whereas dnsmasq did).

The trouble is that it seems to be able to load initial ramdisks, but can never mount the actual filesystem once booted.

I simply dropped everything (ISO files copied from a loopback mount, pxelinux.0, pxelinux.cfg + configuration file, etc) in a folder on the PC as /nfsroot, and set tftp to use that.

---

### Post by darkod on 2009-12-02
Try this.
You have your 9.10 ISO right? Format the stick as FAT32 if it's not that. Launch unetbootin and as usual select the ISO option and point to the ISO. Select the stick as target and click OK. At the end when it asks about reboot ignore it, just close unetbootin.

To get rid of the grub menu unetbootin makes, open the stick and do:
1. In the root folder of the stick rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will make the original Ubuntu menu show up during boot. Maybe it will make a difference. The Ubuntu menu is better anyway because it gives the options Try Ubuntu, Install Ubuntu, etc while unetbootin I think starts the installation straight away.

---

### Post by Stormblazer on 2009-12-02
Intersting... I reformatted the USB stick completely and tried live ubuntu through unetbootin again, and this time it worked. So hopefully I can resize the partition now.

This still leaves me with a problem though - I'd prefer to try something like gentoo on the netbook first, and net booting still seems like a very good idea in general.

---

### Post by gravyflex on 2009-12-02
> This still leaves me with a problem though - I'd prefer to try something like gentoo on the netbook first, and net booting still seems like a very good idea in general.

I know what you mean! This sure makes life much easier. By chance did you install the netboot package?

---

### Post by Stormblazer on 2009-12-02
> **gravyflex said:**
> I know what you mean! This sure makes life much easier. By chance did install the netboot package?

Netboot package?

---

### Post by gravyflex on 2009-12-02
The package for karmic is found here:

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz)

I had used netboot to install karmic from the alternate CD. I installed apache mounted the iso under /var/www. I then pointed the netboot installer to that computer.

---

