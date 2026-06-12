---
title: "Kernel build issues with Gutsy"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by bitmonkey on 2008-01-10
I am trying to rebuild my Gutsy kernel. I downloaded the sources using apt-get, did a make xconfig and have built the kernel and modules using:

make-kpkg --initrd --append-to-version=ironballs kernel-image kernel-headers

Then used dpkg -i to install the .deb files produced by this. All looked fine with the correct files in /boot and the right entries in grub menu.list, however my kernel would not boot. It just stopped partway through the boot process and inspecting /var/log/messages shows the following during the attempted boot:

Jan 10 18:04:05 ironballs kernel: [  293.416000] bcm43xx: TODO: Incomplete code 
in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wirele
ss/bcm43xx/bcm43xx_main.c:1112

I am presuming this means that the restricted drivers package has not been built for the new kernel, so I am trying to use the instructions under the "Rebuilding "linux-restricted-modules"" heading on the page [https://help.ubuntu.com/community/Kernel/Compile#head-4591a640f1ecb03492f49521d7c055cba2845ca1](https://help.ubuntu.com/community/Kernel/Compile#head-4591a640f1ecb03492f49521d7c055cba2845ca1)

However, this page talks about adjusting the values of the abi_version and flavours variable assignments to ensure the build process has the correct name for your new kernel - mine is not in the form suggested. The page suggests kernel filenames should be of the form 2.6.19-7-ref-generic and this is what abi_version does - append the "7-ref" in the above example, however my kernel is called vmlinuz-2.6.22.9ironballs without the dashes that the linux-restricted-modules build script is expecting.

In addition the original ubuntu kernel is called vmlinuz-2.6.22-14-generic, in the correct form of name, so perhaps I have done something wrong during the build process to end up with my oddly named file. 

Any ideas and suggestions gratefully accepted.

---

