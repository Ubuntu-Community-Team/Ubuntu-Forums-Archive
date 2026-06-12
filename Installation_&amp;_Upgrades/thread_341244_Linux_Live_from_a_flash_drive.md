---
title: "Linux Live from a flash drive"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by jonlemur on 2007-01-18
I recently got a 1G flash drive, and I'm wanting to be able to boot Linux from it.  I tried following the guide, 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28drive%29%7C%28pen%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28drive%29%7C%28pen%29)

but I had a few questions about it.  First when dealing with creating the necessary partions using fdisk, it says 

> Set the file system of partition 1 to FAT: 't', then '1', then '6'

What FAT version does it mean?  When I type "l" it displays the possible versions.  1 is FAT12, and 16 is FAT16 (hidden), or something like that.  Is it supposed to be FAT16?

Second, I don't understand what the following is supposed to accomplish, or where it is supposed to be done (i.e. in my home directory, on the flash drive itself, etc).  This is done after downloading an image.

> Download the dapper or edgy image (ubuntu-6.06-desktop-i386.iso or ubuntu-6.10-desktop-i386.iso) or put in the install CD if you have it. If you use the downloaded image you can access it as follows (supposing that the image is in the path you are working in; use 6.06 for dapper or 6.10 for edgy):

[QUOTE]mkdir ubuntuCD
sudo mount ubuntu-6.06-desktop-i386.iso ubuntuCD -o loop[/QUOTE]



Third, it shows what files to copy from a live cd to the flash drive.  However, the live cd that I have (which I just made by downloading an image from [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download) ) doesn't have the same files and folders listed.  The following are the files and folders he says to copy, and the bold ones are the ones I don't have:

> Folders : **'casper',** **'disctree',** 'dists', 'install', 'pics', 'pool', 'preseed', '.disk'

Files : all files from the folder 'isolinux', 'md5sum.txt', 'README.diskdefines', **'ubuntu.ico'** 

I have, in addition to the non-bold folders above, dists and doc.  Have casper and disctree been replaced by these two?

Once I get these issues ironed out, I should be able to work more with the rest of the guide.  Or if you know of a better way, I'd love to look at it.  Thanks for your help.

---

### Post by Rippey on 2007-01-18
[_this_]("http://ubuntuforums.org/showthread.php?t=80811") howto is made for use with a usb external drive, however it works verry nice on a stick, quit easy to do aswell. :)

---

