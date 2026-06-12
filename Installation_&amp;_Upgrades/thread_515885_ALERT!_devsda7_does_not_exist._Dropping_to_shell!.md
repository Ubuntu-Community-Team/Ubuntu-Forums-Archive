---
title: "ALERT! /dev/sda7 does not exist. Dropping to shell!"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Velvom on 2007-08-02
hello,

I have a Ubuntu machine and I am trying to install a new kernel (2.6.21.1) and it recompiles and does everything nicely as per [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2) which is an excellent website, btw. I tried booting to the new kernel but it after a long pause it always comes back with the error:

ALERT! /dev/sda7 does not exist. Dropping to a shell!

But my other kernels are (2.6.15-28, 2.6.15-26) able to recognize this drive and boot no problem so why is this new one giving such a message? Does anyone know? Is there something I am doing wrong concerning the make menuconfig options? I have already compiled 3 other kernels and they all give similar errors. Actually there is one prior message, displayed before the long pause that says:

PCI: Cannot allocate resource region 0 of device 0000:05:06.0.

I am not sure if that is related to the ALERT! error message but I thought I would let you guys know.

I have read the other posts but they do relate to my problem of upgrading the kernel.  

I already checked the menu.lst file and they all match i.e the root is pointing to /dev/hda7 but only in th newer version it is not finding that root device.  I am a frustrated noob so please bear with me if I ask obvious questions.  

Thanks in advance.

Velvom

---

### Post by Velvom on 2007-08-03
anyone with suggestions??

---

### Post by forestpixie on 2007-08-03
just a maybe but your title says /dev/sda7 doesn't exist - in your thread you say that menu.lst is pointing at /dev/hda7 

not been here long enough to really know but should they not be the same?

---

### Post by dabl on 2007-08-03
> **Velvom said:**
> anyone with suggestions??

There is a mis-match between what it says in your filesystem table (/etc/fstab) and where the boot menu thinks the root filesystem is located (/boot/grub/menu.lst).  Probably fstab has the "truth", and menu.lst needs to be edited to match it.

---

### Post by Velvom on 2007-08-03
Sorry for the mixup...menu.lst does point to sda7.  However I found out that in my working kernels the partions are named as sda0,1,2... but on the the new kernel which doesn't work it was named as hda0,1,2.....  I was able to find this out on the functionally limited sh shell by executing the command 'ls -l /dev | grep hda' on the new kernel.  'ls -l /dev | grep sda' returned nothing on the new kernel.  

So i changed menu.lst to point to hda7 only on the new kernel (2.6.21.1) but it still did not boot up. :(  I tried all the other hda numbers like hda6,8,9 etc (because I couldn't which partition was the root file system) and none of them worked.  

So it is very strange why the new kernel is not recognizing hda partitions.  I will try to see fstab and see if that is all good with menu.lst but thanks again.

---

### Post by Velvom on 2007-08-07
I tried changing /etc/fstab to hda0..7 and that still did not work.  And it also messes the root pointers for my other working kernels because the it has changed to hda instead of sda.  

On the other two work laptops, one is a toshiba, they seem to be working well and the partitions are recognized as sda, but only on mine is it giving this strange problem.  Please Help!!!! I dont want to get rid of ubuntu and start with another distro becuase I like ubuntu :(

---

### Post by merlinus on 2007-08-07
Should be (hd0,6), since numbering for this sort of thing begins at zero, not one.

And yes, the last kernel update changed things once again,  But as long as you point to the correct partition, it does not matter if the mountpoint is /media/sda7 and the device is /dev/hda7.

-merlin

---

