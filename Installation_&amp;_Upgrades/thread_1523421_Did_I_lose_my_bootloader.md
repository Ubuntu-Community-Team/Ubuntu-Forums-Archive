---
title: "Did I lose my bootloader?"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by one5 on 2010-07-03
I have installed many linux distros including ubuntu before, so it frustrates me that I cant do this on my own but anyway here is my problem:

I have an old Fujitsu 3500 stylistic that I want to install xubuntu on. It had windows 98 on it. Since It is a tablet without a CD drive I used a 2.5 enclosure to connect it to my computer. 
I then formatted the hard drive and used  unetbootin to get the files on the disk. I thought I was done, and got it working but when I try to boot I get a message "remove disk and press any key to restart." Does anyone know how/why this happened, or how to fix it?

Any advice would be appreciated

---

### Post by oldfred on 2010-07-03
Welcome to the forums.

When you say you used unetbootin, did you just copy to the harddrive? Generally you use unetbootin to create a bootable fat based installer using syslinux as the boot loader. That is not normally a full install.

Can you run the external as a live disk? If so download and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by one5 on 2010-07-03
> **oldfred said:**
> Welcome to the forums.

When you say you used unetbootin, did you just copy to the harddrive? Generally you use unetbootin to create a bootable fat based installer using syslinux as the boot loader. That is not normally a full install.

Can you run the external as a live disk? If so download and run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

I wanted to boot the hard disk like a CD/live CD

My problem is that I cannot run it as a live disk, boot into it ect. All I get is a error message.
 At this point I do not have access to any OS on that tablet, it wont boot from the hard drive, it does not have a CD drive, and usb boot is not an option as it is an older system. I can use my 2.5 hard drive adapter to connect  to the hard drive but so far that has not worked.

---

### Post by darkod on 2010-07-03
Network or PXE install an option?

---

### Post by one5 on 2010-07-03
network might be. I have a lan connection, but I've never tried it. The only problem is that I cant seem to get anything to boot.

---

### Post by darkod on 2010-07-03
Well, that's the point, you don't need to have any bootable OS on the computer. As long as the BIOS allows you to boot from network, set it as first option before hdd.

This link with PXE instructions was recently mentioned in a thread:
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)

It's old but you can use it for lucid too.
The Lucid archive ftp with the files for 64bit and 32bit installer would be here, use the ones you want:
[ftp://archive.ubuntu.com/ubuntu/dists/lucid/main/](ftp://archive.ubuntu.com/ubuntu/dists/lucid/main/)

---

### Post by one5 on 2010-07-03
I have a PXE option in bios I'll try this and post the results.
It looks like it will be a perfect solution thanks.

---

### Post by one5 on 2010-07-03
Update: I have a telephone connector but no Ethernet/LAN is this still possible?

---

### Post by darkod on 2010-07-03
> **one5 said:**
> Update: I have a telephone connector but no Ethernet/LAN is this still possible?

Don't think so. A modem could give you internet, but you need local network, LAN.

You should probably consider borrowing a usb cd-rom from a friend. It sounds like a best option, if you can make it happen.

On another note, were you planning to have internet access only with the dial-up modem later? Or invest in one of those usb to network adapters, and give the PXE a shot through it. It would also allow you fast internet later.

But not sure if PXE recognizes it, whether drivers are needed, etc.

---

### Post by one5 on 2010-07-03
> **darkod said:**
> Don't think so. A modem could give you internet, but you need local network, LAN.

You should probably consider borrowing a usb cd-rom from a friend. It sounds like a best option, if you can make it happen.

On another note, were you planning to have internet access only with the dial-up modem later? Or invest in one of those usb to network adapters, and give the PXE a shot through it. It would also allow you fast internet later.

But not sure if PXE recognizes it, whether drivers are needed, etc.

I'll have to get a cd-rom usb thanks for all your help

---

