---
title: "kernel 2.6.13.4 problem"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by oxiw on 2005-10-21
HI, I am first time reinstalling kernel, everything seems good, but after reinstall, there is written mesage about 

kernel:
LinuxbzImage, setup=0x1e00, size 0x16480e
and initrd:
Linux-initrd@0x1d4cd000, 0x2b22000 bytes
and a blinking cursor only,

so I dont know where is the problem, because it didn't write anything else. Could someone help, if this is problem, or where should i start to look for it.

thnx a lot.

---

### Post by Kyral on 2005-10-21
Can I see your /boot/grub/menu.lst?

Also what compile method did you use? You must have done it yourself because the 2.6.13.4 sources aren't in any Ubuntu repo right now (Only on Kernel.org)

---

### Post by oxiw on 2005-10-21
Hi,  i dont know much about differencies between methodes, if you could explain shortly, what is the difference between make and make bzImage, if there is.. 

My relevant Grub lines:
title		  Ubuntu, kernel 2.6.13.4-13.4
root		(hd0,1)
kernel	       /boot/bzImage-2.6.13.4-13.4 root=/dev/hda2 ro quiet splash
initrd		 /boot/initrd-2.6.13.4-13.4.img

method: **untar, config, make bzImage, make initrd, make modulles, make install_modules, cp maps, and setup grub**. 
as mentioned in
[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html]("http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html")

Just installing 2.6.11, but ... if I rewrite modules with older version will it works? How works support for ubuntu, if there is two version release difference ?
but if possible i will rewrite it again, and another little q. about dependencies between steps of creating image and making modules, q. is i**f modules are built from image, or from sources.** 
thnx a lot..

---

### Post by Kyral on 2005-10-21
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

This may help

[https://wiki.ubuntu.com/KernelByHandHowto](https://wiki.ubuntu.com/KernelByHandHowto)

This is what I used when I compiled the 2.6.13.4 that I'm using now (granted I don't use an Initrd anymore..)

---

### Post by oxiw on 2005-10-22
[FONT="System"]
hi thnx for advice,
 finally working, but inspite of all ubuntu docs, here is one step by step kernel instalation which works found on [http://www.linuxquestions.org/questions/history/361735]("http://www.linuxquestions.org/questions/history/361735")
with some necessary adds.

[B]
1. $ tar -zxf linux-2.6.13.4.tar.gz
2. $ cd linux-2.6.13.4
3. $ make menuconfig
4. $ make
5. # cp .config /boot/config-2.6.13.4
# cp System.map /boot/System.map-2.6.13.4
# cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.13.4
# ln -sf config-2.6.13.4 /boot/config
# ln -sf System.map-2.6.13.4 /boot/System.map
# ln -sf vmlinuz-2.6.13.4 /boot/vmlinuz
6. # make modules
7. # make modules_install
8.#  mkinitrd -o /boot/initrd.img-2.6.13.4 2.6.13.4
9. #gedit /boot/grub/menu.lst

#grub
title		Ubuntu, kernel 2.6.13.4
root		(hdX,X)
kernel 		/boot/vmlinuz-2.6.13.4 root=/dev/hdaX ro quiet splash
initrd		  /boot/initrd.img-2.6.13.4
savedefault
boot[/B]
 [/FONT] :rolleyes:

---

### Post by mlomker on 2005-10-22
That isn't the standard way to build a debian kernel.  It's a lot easier to [use make-kpkg]("http://newbiedoc.sourceforge.net/system/kernel-pkg.html#KPKG-KERNEL-PKG") and then install the resulting .deb files.

---

### Post by oxiw on 2005-10-22
yes, like from coans not? next time shorter

---

