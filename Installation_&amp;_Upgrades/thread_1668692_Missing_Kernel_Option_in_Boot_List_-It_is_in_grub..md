---
title: "Missing Kernel Option in Boot List -It is in grub.cfg grub2"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by Highlander01 on 2011-01-16
I went thru the exercise of installing a new kernel.....
 
I have Grub2 
I have the following files in my boot folder:
 
config-2.6.32.28
initrd.imp-2.6.32.28
vmlinuz-2.6.32.28
 
I also did update-grub
grub.cfg has 2.6.32.28 above as a menuentry
 
when I boot up though it does not appear in the list of boot options.
 
just noticed: maybe I need an abi-2.6.32.28 file or vmcoreinfo-2.6.32.28 file

---

### Post by texla on 2011-03-26
I have a multi-boot setup and this kept happening to me.  For some reason I had to go to another ubuntu partition and run a sudo update-grub there and now I have the updated kernels in my grub.  Might be because of which one was installed first or something but it worked.  Hope this helps.

---

### Post by Hedgehog1 on 2011-03-27
If you wish to correct the install location of grub; please to this:

Please boot off your LiveCD/LiveUSB, select TRY

Determine what partition holds your Ubuntu root.  In the examples below, the assume that /dev/sd**a5** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

### Post by texla on 2011-03-27
Did it - looks good so far - we'll see on the next update.  Thanks, Hedge!

---

### Post by oldfred on 2011-03-27
If you want to reset which install is in the MBR you can boot that install and just install grub2's bootloader to the MBR from there.


#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub


If you are alternatively booting multiple installs you can add a boot stanza that always boot the most current kernel. ubuntu always puts a link to the most current kernel in /. So boot the link in root.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

You can even turn off osprober and just have the above style entries in 40_custom.

---

