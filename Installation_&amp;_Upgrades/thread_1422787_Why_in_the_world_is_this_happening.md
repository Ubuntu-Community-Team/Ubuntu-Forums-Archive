---
title: "Why in the world is this happening?"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Anthony523 on 2010-03-05
Okay well I had ubuntu netbook remix on my netbook and I decided to switch to normal Ubuntu (Karmic) so I made a LiveCD and made my flash drive into a startup disc and tried to boot from it and it worked... but now it won't let me install it at all I can run the live CD fine! but it won't allow me to install it fully
On top of all of that it won't let me boot into my Windows partition so now I basically have a useless netbook until this get solved
I turn on the computer and it says
GRUB loading.
error: no such partition
grub rescue> _      <-------- command line
Can anyone help? at the very least help me become able to get onto my Windows partition

---

### Post by themusicalduck on 2010-03-05
Did you delete the partition that Ubuntu was installed on?

Also, why can't you install it? Is there some kind of error? Does the installer not run?

As to getting into Windows, you could try to reinstall the windows bootloader to the MBR, but that is a little difficult without a CD drive. You would have make a pen drive with the XP installer on it, which is possible to do with some software, but I think you'd need access to a Windows PC.

But if you can get Ubuntu to install anyway, you will be able to get back into XP.

---

### Post by Anthony523 on 2010-03-05
When I try to open the installer it just doesn't open.

---

### Post by themusicalduck on 2010-03-05
First thing to try is to check the md5sum of the .iso that you used to make your live usb stick with. It's possible something is up with the file, so checking the md5sum will tell you. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) If the md5sum does not match the corresponding code on this page [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) then re-download it and try it again.

If the .iso does appear to be fine, then you could try installing with the alternate CD instead. [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

However it isn't as clear as using the installer with a GUI, so be careful with partitioning. If you know what you're doing then it's clear enough.

Lastly. If you preferred to, you might be able to re-install the UNR version, then there may be a way of uninstalling and installing certain packages to make it like the desktop version. This would probably be the less easy option though and you'd have to do some research to find out how to do it.

How did you make the USB bootable drive? With unetbootin? Or something else?

---

### Post by hyperAura on 2010-03-05
it is possible that there is a dead sector on the hard drive but the probabilities are not so high..

---

### Post by pastalavista on 2010-03-05
Don't try to open the installer, but open Applications >Accessories >Terminal and enter```
sudo fdisk -l
```
Notice the drive maked with [*] under the 'boot' column. That has the boot sector. Then run```
sudo grub-setup /dev/sd**
``` replace the ** with the dev# with the boot *.

Then try and boot again.

---

### Post by Anthony523 on 2010-03-05
I tried what you said pasta but it says "error: cannot open '/boot/grub/device.map'"
Soooo well now I'm gonna try using UNetbootin to remake my flash drive into a bootable disk and see if that works.. if not then I'll be at a loss...

---

### Post by Anthony523 on 2010-03-05
Okay well I Pretty much now have a useless netbook and I'm really pissed about it.... I have no idea what to do... ugh..

---

