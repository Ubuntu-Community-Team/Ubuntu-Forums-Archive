---
title: "I'm getting SQUASHFS and print_req errors when restarting after installation"
date: 2019-03-24
forum: Installation &amp; Upgrades
---

### Post by alpbintug on 2019-03-24
I'm trying to install Ubuntu 16.04 on my computer (dualboot with Win10), but when I see "installation is complete, restart your device" message, I click on restart and I get SQUASHFS and print_req errors and ubuntu won't start up.

What I did when trying to install Ubuntu;
-Burned ISO file to 2 different USBs, incase if problem was causing by one of them (got same result)
-Closed Fast boot and secure boot
-Opened CSM thingy
-Booted from non-UEFI usb boot option
-Couldn't close USB legacy mode because my computer resisted booting from USB when it's closed
-Deselected every other boot option but non-UEFI USB option from BIOS menu
-Ubuntu won't showup in BIOS Boot options menu, but when I try to install it again, installer says "Ubuntu 16.04 detected on your computer" and suggests me to install Ubuntu 16.04 alongside with ubuntu 16.04

Errors;
SQUASHFS error: unable to read 
->fragment cache entry
-> page, block *some hexadecimal numbers*
print_req_error: I/O error, devloop0, sector *some decimal numbers*

I need to install ubuntu 16.04 so there is no point to try any other version but any suggestion is appreciated.

---

### Post by ubfan1 on 2019-03-24
squashfs is the filesystem used on the ISO.  Did you hashcheck the ISO?  Did you remove the install media before rebooting?  A normal install, without the install media present should not have a squashfs file system present.
To md5sum check the downloaded iso:
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

