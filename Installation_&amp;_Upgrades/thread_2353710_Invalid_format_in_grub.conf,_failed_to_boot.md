---
title: "Invalid format in grub.conf, failed to boot"
date: 2017-02-24
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2017-02-24
Hi,

I installed 14.4 in a multiple os machine where the default boot starts from CentOS boot. I added following to CentOS grub.conf, but I failed to boot ubuntu, the error was invalid format. Appreciate helps to fix the boot. Thank you. 

title Ubuntu 14.4 (4.4.0-31-generic)
    root (hd1,7)
    kernel /boot/initrd.img-4.4.0-31-generic ro root=UUID=91584f92-af5e-487c-9f2c-09bc778f959b rd_NO_LUKS rd_NO_LVM LANG=en_US.UTF-8 rd_NO_MD SYSFONT=latarcyrheb-sun16 crashkernel=auto  KEYBOARDTYPE=pc KEYTABLE=us rd_NO_DM rhgb quiet single rdblacklist=nouveau nouveau.modeset=0 nvidia.modeset=0
    initrd /boot/initrd.img-4.4.0-31-generic

---

### Post by yancek on 2017-02-24
> kernel /boot/initrd.img-4.4.0-31-generic

That's wrong because it does not point to the kernel (vmlinuz file) in the boot directory of the Ubuntu partition.  Mount sdb8 (your Ubuntu partition) and go to the /boot/grub/grub.cfg file and copy the 'linux' line for the Ubuntu menuentry to the 'kernel' line in the CentOS grub.conf file.  You should also be able to point to the core.img file or chainload with entries such as the ones below.

> title Ubuntu-14.04
root (hd1,7)
kernel /boot/grub/i386-pc/core.img

> title Ubuntu
root (hd1,7)
chianloader +1


Or you could install Grub from Ubuntu to the MBR (if you are using an MBR system) and then run:  sudo update-grub from Ubuntu.

---

### Post by oldfred on 2017-02-24
Debian based installs put a link to most recent kernel in /, so  you can use that to boot without having to update your grub entries with every kernel update. Also easier to manually boot.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

      sudo nano /etc/grub.d/40_custom
```

menuentry "Ubuntu on sdb7" {
  set root=(hd1,7) 
  linux /vmlinuz root=/dev/sdb7 ro quiet splash
  initrd /initrd.img 
} 
```
sudo update-grub

Commands are for Ubuntu, you probably so not need sudo, and may need different command for an editor, and to update grub.

Are you booting from sda as hd0? 
I have had issues where boot drive is always hd0. And booting from sdc became hd0, sda was hd1 and sdb was hd2. But when booting from sda that would be hd0 and sdb was hd1.
Drive order, sda, sdb etc was same as installed in SATA ports as that was how BIOS/UEFI finds drives. But I have also skipped a SATA port and sdf flash drive on reboot may be sdb changing all the other drives.

---

### Post by jimhce on 2017-02-24
> **yancek said:**
> That's wrong because it does not point to the kernel (vmlinuz file) in the boot directory of the Ubuntu partition.  Mount sdb8 (your Ubuntu partition) and go to the /boot/grub/grub.cfg file and copy the 'linux' line for the Ubuntu menuentry to the 'kernel' line in the CentOS grub.conf file.  You should also be able to point to the core.img file or chainload with entries such as the ones below.

I changed to "kernel /boot/grub/i386-pc/core.img", then it gave me another error "Linux kernel must be loaded before initrd" What I am missing here?

Also, my machine is x86_64 not the i386, did I download the wrong Ubuntu image? 

Thank you.

---

### Post by oldfred on 2017-02-24
You want the 64 bit version.
The 16.04 64 bit version for Intel or AMD:
ubuntu-16.04-desktop-amd64.iso

More info:
[https://en.wikipedia.org/wiki/X86-64](https://en.wikipedia.org/wiki/X86-64)

 The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).

---

### Post by yancek on 2017-02-24
Are you using an older (pre 7.0) version of CentOS?  It switched to Grub2 with 7.0.  If so, did you try changing the kernel line to:  kernel /boot/vmlinuz-4.4.0-31-generic

Also, where did you get all the parameters you are using on that line?
I have Ubuntu 14.04 64bit installed and it boots without problem with the core.img entry I posted.  Also boots with the chainloader entry.  
Did you install Grub2 to the Ubuntu partition?  If you did not, then neither of the above entries I posted will work.  Try a 'kernel' line with less parameters:

> kernel  /boot/vmlinuz-4.4.0-31-generic  root=/dev/sdb8


In the entry you posted above, do you have the correct UUID?  You can check for sdb8 with:  sudo blkid

---

### Post by jimhce on 2017-02-24
> **yancek said:**
> Are you using an older (pre 7.0) version of CentOS?  It switched to Grub2 with 7.0.  If so, did you try changing the kernel line to:  kernel /boot/vmlinuz-4.4.0-31-generic

Also, where did you get all the parameters you are using on that line?
I have Ubuntu 14.04 64bit installed and it boots without problem with the core.img entry I posted.  Also boots with the chainloader entry.  
Did you install Grub2 to the Ubuntu partition?  If you did not, then neither of the above entries I posted will work.  Try a 'kernel' line with less parameters:



In the entry you posted above, do you have the correct UUID?  You can check for sdb8 with:  sudo blkid

On my machine the grub version is "grub-install (GNU GRUB 0.97)" on CentOS 6.8. Yes, the UUID is correct. I double checked the image which is Ubuntu 14.04.5 LTS "Trusty Tahr" - Release amd64, but why the boot grub image is i386-pc not amd64?

It failed on both kernel /boot/vmlinuz-4.4.0-31-generic and kernel /boot/grub/i386-pc/core.img. The parameters were copied from the CentOS kernel line, let me change kess parameters.

---

### Post by yancek on 2017-02-24
> The parameters were copied from the CentOS kernel line

I owuld not expect that to work.

> but why the boot grub image is i386-pc not amd64

That's something you would have to ask the Ubuntu developers, I don't know.  I do have that directory on my system which is a 64bit OS but if you did not install Grub with Ubuntu, it will obviously not boot nor will a chainloader entry. You could try the basic entry below.  An you have verified your Ubuntu is on sdb8, correct?

> title Ubuntu-14.04
           root (hd1,7)
           linux    /boot/vmlinuz-4.4.0-31-generic root=UUID=91584f92-af5e-487c-9f2c-09bc778f959b ro  quiet splash $vt_handoff
           initrd    /boot/initrd.img-4.4.0-31-generic

---

### Post by jimhce on 2017-02-24
I changed to use /dev/sdb8, it can now boot, but crashed in kernel. The machine is Dell Inspiron 15 7000 with Core i7 and GPU GeForce GTX 960M, I suspect that the GPU might cause Ubutu 14.4 crash :-(?

kernel /boot/vmlinuz-4.4.0-31-generic root=/dev/sdb8 
initrd /boot/initrd.img-4.4.0-31-generic

---

### Post by oldfred on 2017-02-25
Try nomodeset until you get the proprietary driver installed from Ubuntu repository or ppa.
In your case you can just add to boot stanza until not needed.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 


       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)       
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices

---

