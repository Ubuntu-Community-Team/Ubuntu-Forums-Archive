---
title: "Problem in installing Kernel"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by pepofan on 2010-09-15
Hello. I'm a beginner with ubuntu. I tried to install Kernel in terminal with these instructions:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

First problem came when I entered these commands:
sudo cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
sudo cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/

It said something that I don't remember, but I could proceed until here:
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-mk kernel_image kernel_headers modules_image

Then it took like one day at 70% of installation and got stuck there.
After this, I tried using Lumen Kernel check to install the Kernel. It got stuck again at 70% and started showing errors. Now there probably are stuff from the previous installation attempts that prevent any new Kernel installation to get through(?). Is it possible to conveniently remove all the stuff from the failed installation attempts and try again? 

When I open Kernel check, it shows that Kernel to compile is 2.6.35.4. 

I'm sorry that I'm a little lost here. Thanks for your time!

---

### Post by dino99 on 2010-09-15
without special needs, you dont have to compile the kernel yourself: 

either use synaptic (system admin synaptic) to install the available kernel(s)

or pick one ready to use there:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

install first linux-headers....all.deb, then the header you want: i386 for 32 bits or amd64 for 64 bits, and finally the corresponding image (i386 or amd64 , depends on your previous header choice)

---

### Post by pepofan on 2010-09-15
Thanks Dino99 for your reply.
 
I tried with synaptic and got the following error:
linux-image-2.6.35.4-candela should be installed again, but its archive can not be found.

I don't even know, did it make any sense, but after getting the error in synaptic, I picked from your folder v2.6.35.4-maverick, cause I couldn't find "candela". Anyway, when tryin to open the first packet 	linux-headers-2.6.35-02063504-generic_2.6.35-02063504.201008271919_amd64.deb	
it gave me an error, that I don't either have the rights to open the packet, or the packet is damaged.

---

### Post by pepofan on 2010-10-06
Just to let you, Dino99, the problem I was having was failed installations. I installed a whole new Ubuntu and Kernel. Now everything works. Cheers!

---

