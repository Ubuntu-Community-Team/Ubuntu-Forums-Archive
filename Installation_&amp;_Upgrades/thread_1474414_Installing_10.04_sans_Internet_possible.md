---
title: "Installing 10.04 sans Internet possible?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by MianoSM on 2010-05-06
I am working with a new Dell SC1425.

It does not have any optical drives, and I do not have a readily available network connection to the Internet.

I am attempting to install using a unetbootin created bootable flash drive with the x86 server.

While going through the install I choose to configure my network later (as no DHCP available), and can not seem to get past the "choose your archive mirror".

When I choose <go back> I go back to the list of archives to choose from. When I choose <continue> it has the same effect.

I shot some video of it so you can review it - and maybe see where I have gone wrong.

[http://mianosm.devio.us/ffuu.m4v](http://mianosm.devio.us/ffuu.m4v)

Sorry if the upload/download speed is slow...

---

### Post by alh on 2010-05-06
> **MianoSM said:**
> I am working with a new Dell SC1425.
 
It does not have any optical drives, and I do not have a readily available network connection to the Internet.
 
I am attempting to install using a unetbootin created bootable flash drive with the x86 server.
 
While going through the install I choose to configure my network later (as no DHCP available), and can not seem to get past the "choose your archive mirror".
 
When I choose <go back> I go back to the list of archives to choose from. When I choose <continue> it has the same effect.
 
I shot some video of it so you can review it - and maybe see where I have gone wrong.
 
[http://mianosm.devio.us/ffuu.m4v](http://mianosm.devio.us/ffuu.m4v)
 
Sorry if the upload/download speed is slow...
 
 I think you need the full DVD version with all the software on it. I think the playable CD needs to access the package repositiories via the net.

---

### Post by MianoSM on 2010-05-06
> **alh said:**
> I think you need the full DVD version with all the software on it. I think the playable CD needs to access the package repositiories via the net.

I need the full DVD to install a server OS?

That seems like a bit overkill for what I want to do.

---

### Post by MianoSM on 2010-05-06
So this is what I did.

Step 1: Created my bootable USB drive with [Pen Drive Linux's Universal USB Installer]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/").

Step 2: Copied the ~[700 MB iso]("http://releases.ubuntu.com/releases/10.04/") to the same USB stick.

Step 3: Booted from the USB stick, and started the installer. It complained saying it couldn't find the /dev/cdrom, so I mounted the USB stick to /mnt/ which had the ubuntu-10.04-server-i386.iso on it, and pointed it to: /mnt/ubuntu-10.04-server-i386.iso. It worked.

I think if I had an optical drive it would have been fine. Unetbootin sets the install up as a network install to the best of my knowledge (from looking at its starting options/configuration). PenDrive Linux is missing some of the packages/files when it sets up the USB stick from the iso. 

Conclusion: It may not actually be so much of an issue with Ubuntu, but more so an issue with the utilities that are currently available to setup USB drives for installing operating systems to hard drives.

---

