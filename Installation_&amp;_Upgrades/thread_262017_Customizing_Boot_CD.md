---
title: "Customizing Boot CD"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by codenamewilley on 2006-09-21
Hi everybody,
    Im trying to create a Botable CD which is customized. I'm trying Xubuntu 6.06 for this. This version has Install & Live CD together. I'm using this link for the same.
  [https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo](https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo)

I did everything excpet for the preseed file. I am using the original preseed file ported with the CD. (Can this be the problem?) Now, after I burn the new customized image on the CD & try it, I get errors. The screen shows all the options but it does not boot fromth same disk. Errors I get are as follows :-

hdc: ide_intr:huh? Expected NULL handler on exit
Buffer I/O error on deivce hdc, logical block 339454
VFS: brelse: trying to free free buffer
SQUASHFS error: sb_bread failed reading block 0x7617b
SQUASHFS error:  Unable to read fragment cache bolck[1d8597ac]
SQUASHFS error: Unable to read page, block 1d8597ac, size 55b7

Also, I've created a menu in /cdrom/isolinux/isolinux.cfg which should 
install with the addedd packages in the repository. But if this is selected it says :- 
           Could not find image /install/vmlinuz

Can anyone please tell me how can I resolve these issues?

Praktan.

---

