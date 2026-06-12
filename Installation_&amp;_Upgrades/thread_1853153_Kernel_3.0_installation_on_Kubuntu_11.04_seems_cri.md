---
title: "Kernel 3.0 installation on Kubuntu 11.04 seems crippled"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by lhuser on 2011-10-01
So today, I decided to finally get myself in for some kernel upgrade, but unfortunately, it seems to install, ut once I try to boot with it, my PC just seems to remain inactive to a blank screen.

In the details, here is what I get:

Preparing to replace linux-image-3.0.0-0300-generic 3.0.0-0300.201107220917 (using .../linux-image-3.0.0-0300-generic_3.0.0-0300.201107220917_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.0.0-0300-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
Setting up linux-image-3.0.0-0300-generic (3.0.0-0300.201107220917) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-3.0.0-0300-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168e-1.fw for module r8169
cryptsetup: WARNING: failed to detect canonical device of /dev/sdc1
cryptsetup: WARNING: could not determine root device from /etc/fstab
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-0300.201107220917 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-0300.201107220917 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
 * dkms: running auto installation service for kernel 3.0.0-0300-generic

 *       virtualbox-ose (4.0.4)...
   ...done.
 *       nvidia-current (270.41.06)...
   ...fail!
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-0300-generic /boot/vmlinuz-3.0.0-0300-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-0300-generic
Found initrd image: /boot/initrd.img-3.0.0-0300-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done



Note that when it is performing the installation service to nvidia-current, the module crashes as well as soon as it says failed.


Any ideas? Something I'm missing?
I did follow the linux-headers_all, then the linux-headers-amd64, then the kernel, but still, doesn't seem to do it.

---

### Post by lhuser on 2011-10-02
I got it fixed. It turns out that the Nvidia drivers were outdated, and won't work with the new 3.0 kernel, unless you do some modding. I took the easy way. I should of known that Nvidia was at version 280 of their driver package.

Anyways, what I did is that I uninstalled the nvidia-current and nvidia-common then I  grabbed the beta 285 drivers from the Nvidia's website, then followed the steps to grab the 3.0.0-10.16 generic kernel over here:
[http://www.ultimateeditionoz.com/forum/viewtopic.php?t=2992](http://www.ultimateeditionoz.com/forum/viewtopic.php?t=2992)

I booted into the terminal, then installed the drivers. I ignored the warning about the gcc4.5 issue (since I was compiling it with gcc 4.6).

Then, I started X, and here I am typing all this in the new kernel, and the Nvidia 285.03 drivers.

Hope this helps out a few people here!

---

