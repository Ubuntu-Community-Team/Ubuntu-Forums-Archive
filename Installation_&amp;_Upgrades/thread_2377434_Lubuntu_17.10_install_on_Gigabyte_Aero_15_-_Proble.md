---
title: "Lubuntu 17.10 install on Gigabyte Aero 15 - Problems..."
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by tilllt on 2017-11-13
Hello People,

i have one of these "fairly" new Gigabyte Aero 15 Laptops and i bought a second NVMe SSD to install Ubuntu on it. The install fails, i tried 17.04, 17.10, UEFI Bios with Secure Boot on & off, TPM on & off... Installation medium was the amd64 desktop ISO shoved to USB using Rufus in DD mode.

What happens is that the installer seems to run fine, but then cannot install the Grub2 Bootloader correctly. The Installer crashes and leaves an unbootable installation. I used the "Custom" Setup option and setup a 500MB efi Partition and and a 50Gb Root...

i THINK this might be connected to a very old and suprisingly stupid Grub2 Bug as described here: 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561572](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1561572)
or here
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1507505](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1507505)
and in approximately hundreds of other places over the interweb.

Since this Bug is VERY old, has to do with the enumeration of NVMe drives, i assumed that i would be safe with 17.10 - am i not?

Any way how to EASILY solve this? (Boot Repair does NOT work to fix the missing Grub)

Thanks,
E.

---

### Post by tilllt on 2017-11-13
Ok. That was easier than i thought: The 4hrs or so that i tried yesterday installing from the USB install unsuccesfully (in a place without internet access) were solved by a 5 min install with internet enabled. No Grub install errors. Great.

First boot: Black Screen. Booting into recovery, running software update solved this as well.

Next problem: Reboot, Shutdown etc. crashes the system. Any Hints?

---

### Post by oldfred on 2017-11-13
You said you resolved black screen?
Was that from installing nVidia driver?
You may need newer ppa to get latest driver.
Or in UEFI do you turn on/off nVidia or Internal Intel video?

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 


 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

If you are only using the Intel video.

 With current kernel versions, i915.fastboot=1 needs to be set for enabling the Fastboot mode as it's been disabled by default.
Intel's "i915" DRM driver fastboot mode is intended for eliminating unnecessary mode-set operations during the system's boot process. 
This patch is too late for DRM-Next for Linux 4.15, but perhaps we'll finally see it flipped on for Linux 4.16. 
   [https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)
Now new Intel chips need this boot parameter:
 i915.alpha_support=1

---

### Post by tilllt on 2017-11-13
@oldfred:
i _assume_ that the nvidia or intel drivers got installed / updated once i booted into recovery mode. So, to recap: 
- Installation failed without Internet because of NVMe enumeration with Grub2 Install.
- Installation succeeds with Internet enabled (and downloading updates during install).
- Installation boots into black screen when regularly booting.
- Booting recovery mode loads Desktop with totall wrong resolution, but at least loads. Offers software update. Installs something.
- Regular boot succeeds with proper resolution. I then continued to install Bumblebee, which in return replaces free nouveau drivers with proprietary nvidia drivers
- Another boot results in perfectly working (so far) lubuntu.  Havent used Bumblebee yet or apps which make use of the Nvidia.

---

### Post by oldfred on 2017-11-13
I thought bumblebee was obsolete with the newest nVidia drivers which you should be using.
Have you tried just installing nVidia driver from ppa?

If you have installed bumblebee you need to purge it & nVidia & reinstall nVidia as posted above.

---

