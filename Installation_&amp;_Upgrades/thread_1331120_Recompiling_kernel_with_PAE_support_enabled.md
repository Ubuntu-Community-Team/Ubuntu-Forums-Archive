---
title: "Recompiling kernel with PAE support enabled"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by manavendra on 2009-11-19
Hi All,

I am using a Dell Studio 1555 laptop with 32-bit Kubuntu Karmic 9.10. Since, the kernel is not listing my all 4GB RAM but showing only 2.9GB, I am trying to recompile the kernel with PAE support enabled (High Memory Support - 64GB). 

When the recompile finally finishes,  cd to /usr/src and there will be two .debs for your kernel, install them as shown below:

root@manav-workstation:/usr/src# dpkg -i linux-headers-2.6.28.9-mykernel_2.6.28.9-mykernel-10.00.Custom_i386.deb
root@manav-workstation:/usr/src# dpkg -i linux-image-2.6.28.9-mykernel_2.6.28.9-mykernel-10.00.Custom_i386.debThe debug output of the last command is:

root@manav-workstation:/usr/src# dpkg -i linux-image-2.6.31.4-mykernel_2.6.31.4-mykernel-10.00.Custom_i386.deb 
 (Reading database … 176378 files and directories currently installed.)
Preparing to replace linux-image-2.6.31.4-mykernel 2.6.31.4-mykernel-10.00.Custom (using linux-image-2.6.31.4-mykernel_2.6.31.4-mykernel-10.00.Custom_i386.deb) …
Done.
Unpacking replacement linux-image-2.6.31.4-mykernel …
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory … found: /boot/grub
Searching for default file … found: /boot/grub/default
Testing for an existing GRUB menu.lst file … found: /boot/grub/menu.lst
Searching for splash image … none found, skipping …
Found kernel: /boot/vmlinuz-2.6.31.4-mykernel
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst … done
 Setting up linux-image-2.6.31.4-mykernel (2.6.31.4-mykernel-10.00.Custom) …
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.31.4-mykernel
) points to /boot/initrd.img-2.6.31.4-mykernel
 (/boot/initrd.img-2.6.31.4-mykernel) — doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.4-mykernel.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.31.4-mykernel
) points to /boot/vmlinuz-2.6.31.4-mykernel
 (/boot/vmlinuz-2.6.31.4-mykernel) — doing nothing at /var/lib/dpkg/info/linux-image-2.6.31.4-mykernel.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory … found: /boot/grub
Searching for default file … found: /boot/grub/default
Testing for an existing GRUB menu.lst file … found: /boot/grub/menu.lst
Searching for splash image … none found, skipping …
Found kernel: /boot/vmlinuz-2.6.31.4-mykernel
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst … done
 Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
**run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20**
 Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.4-mykernel.postinst line 1186.
 dpkg: error processing linux-image-2.6.31.4-mykernel (–install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.4-mykernel
 root@manav-workstation:/usr/src#


 I guess that the error might be due to nvidia drivers as I don’t have any nvidia graphics card but ATI Raidon card. However, i cannot understand why it is compiling nvidia drivers. I am planning to remove the support for nvidia drivers from “make menuconfig” and give a try again. What do you suggest ??

---

### Post by manavendra on 2009-11-19
I disabled nvidia from
menuconfig -> grphics driver -> AGP -> nvidia

I also tried disabling the NVIDIA drivers by commenting out all the lines containing NVIDIA in the file ".config".

Still i am getting the same error:
root@manav-workstation:/usr/src# dpkg -i linux-image-2.6.31.4-mykernel_2.6.31.4-mykernel-10.00.Custom_i386.deb 
.
..
...
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
**run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20**
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.4-mykernel.postinst line 1186.
dpkg: error processing linux-image-2.6.31.4-mykernel (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31.4-mykernel

All solutions are welcome !!! I desperatly need to use all my 4GB. Also, I have allocated 1GB swap space. So, will enabling PAE with high memory support affect hybernation of the system.

---

### Post by manavendra on 2009-11-19
Hope this helps !!!

# sudo chmod -x /etc/kernel/postinst.d/nvidia-common

# sudo apt-get purge nvidia-common

---

### Post by manavendra on 2009-11-19
After removing nvidia-common when i am trying to install the new kernel image the following errors are coming:

root@manav-workstation:/usr/src/linux# **make-kpkg --initrd --append-to-version=-mykernel kernel_image kernel_headers**
exec debian/rules  DEBIAN_REVISION=2.6.31.4-mykernel-10.00.Custom  APPEND_TO_VERSION=-mykernel  INITRD=YES  kernel_image kernel_headers 
/usr/bin/make -f ./debian/rules         debian/stamp/binary/pre-linux-image-2.6.31.4                                                    
make[1]: Entering directory `/usr/src/linux-source-2.6.31'                                                                              
====== making target debian/stamp/binary/pre-linux-image-2.6.31.4 [new prereqs: linux-image-2.6.31.4]======                             

This is kernel package version 11.015.
/usr/bin/make -f ./debian/rules debian/stamp/binary/linux-image-2.6.31.4
make[2]: Entering directory `/usr/src/linux-source-2.6.31'              
====== making target debian/stamp/binary/linux-image-2.6.31.4 [new prereqs: ]======

This is kernel package version 11.015.
install -p -d -o root -g root  -m  755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN
sed -e 's/=V/2.6.31.4/g'    -e 's/=IB//g' \                                             
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                          
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                          
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                          
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                              \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \                                                 
            -e 's@=M@@g'    -e 's/=OF//g'    \                                                                                
            -e 's/=S//g' -e 's@=B@i386@g'     \                                                                               
          ./debian/pkg/image/postinst > /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/postinst                            
chmod 755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/postinst                                                          
sed -e 's/=V/2.6.31.4/g'           -e 's/=IB//g' \                                                                            
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                                                                
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                                                                
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                                                                
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                              \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \                                                 
            -e 's@=M@@g'    -e 's/=OF//g'    \                                                                                
            -e 's/=S//g'  -e 's@=B@i386@g'    \                                                                               
         ./debian/pkg/image/config > /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/config                                 
chmod 755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/config                                                            
sed -e 's/=V/2.6.31.4/g'           -e 's/=IB//g' \                                                                            
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                                                                
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                                                                
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                                                                
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                              \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \                                                 
            -e 's@=M@@g'    -e 's/=OF//g'    \                                                                                
            -e 's/=S//g' -e 's@=B@i386@g'     \                                                                               
         ./debian/pkg/image/postrm > /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/postrm                                 
chmod 755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/postrm                                                            
sed -e 's/=V/2.6.31.4/g'           -e 's/=IB//g'           \                                                                  
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                                                                
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                                                                
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                                                                
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                              \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \                                                 
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/preinst > /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/preinst
chmod 755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/preinst
sed -e 's/=V/2.6.31.4/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                              \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/prerm > /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/prerm
chmod 755 /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/prerm
echo using old template
using old template
sed -e 's/=V/2.6.31.4-mykernel/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master /usr/src/linux/debian/linux-image-2.6.31.4/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp             \
                        -plinux-image-2.6.31.4 -P/usr/src/linux/debian/linux-image-2.6.31.4/
**dpkg-gencontrol: error: package linux-image-2.6.31.4 not in control info**
make[2]: *** [debian/stamp/binary/linux-image-2.6.31.4] Error 255
make[2]: Leaving directory `/usr/src/linux-source-2.6.31'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.31.4] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.31'
make: *** [kernel_image] Error 2

What might have possibly went wrong? Any clues??

---

### Post by manavendra on 2009-11-19
**"dpkg-gencontrol: error: package linux-image-2.6.31.4 not in control info"**

What does the above error means and how to remove it? Should it come for custom kernels?

---

### Post by manavendra on 2009-11-19
When i run the above command again with "***--stem***" option I get a different error:

root@manav-workstation:/usr/src/linux# **make-kpkg *--stem* --initrd --append-to-version=-manav-kernel kernel_image kernel_headers**
exec debian/rules  DEBIAN_REVISION=2.6.31.4-mykernel-10.00.Custom  APPEND_TO_VERSION=-manav-kernel  KPKG_STEM=--initrd  kernel_image kernel_headers 
/usr/bin/make -f ./debian/rules         debian/stamp/binary/pre---initrd-image-2.6.31.4                                                             
make[1]: Entering directory `/usr/src/linux-source-2.6.31'                                                                                          
====== making target debian/stamp/install/--initrd-image-2.6.31.4 [new prereqs: ]======                                                             
This is kernel package version 11.015.                                                                                                              
rm -f -r .//usr/src/linux/debian/--initrd-image-2.6.31.4 .//usr/src/linux/debian/--initrd-image-2.6.31.4.deb                                        
install -p -d -o root -g root  -m  755 /usr/src/linux/debian/--initrd-image-2.6.31.4//boot                                                          
install -p -d -o root -g root  -m  755 /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/examples                 
install -p    -o root -g root  -m  644 debian/changelog /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/changelog.Debian
install -p    -o root -g root  -m  644 Documentation/Changes /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/           
install -p    -o root -g root  -m  644 ./debian/docs/ImageLoaders/LiloDefault /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/LiloDefault                                                                                                                                                                   
install -p    -o root -g root  -m  755 ./debian/examples/sample.force-build-link.sh          \                                                                          
                                                      /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/examples/                     
install -p    -o root -g root  -m  644 ./debian/pkg/image/README    /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/debian.README
install -p    -o root -g root  -m  644 .config   /usr/src/linux/debian/--initrd-image-2.6.31.4//boot/config-2.6.31.4
install -p    -o root -g root  -m  644 conf.vars         /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/conf.vars
echo "This was produced by kernel-package version 11.015." > \
                   /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/Buildinfo
chmod 0644 /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/Buildinfo
install -p    -o root -g root  -m  644 debian/buildinfo /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/buildinfo
if test -f debian/official && test -f debian/README.Debian ; then \
           install -p    -o root -g root  -m  644 debian/README.Debian   /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/README.Debian ; \
        fi
if test -f README.Debian ; then \
           install -p    -o root -g root  -m  644 README.Debian /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/README.Debian.1st;\
        fi
if test -f Debian.src.changelog; then               \
          install -p    -o root -g root  -m  644 Debian.src.changelog   /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/; \
        fi
gzip -9qfr                        /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4
install -p    -o root -g root  -m  644 ./debian/pkg/image/copyright /usr/src/linux/debian/--initrd-image-2.6.31.4/usr/share/doc/--initrd-image-2.6.31.4/copyright
test ! -f scripts/package/builddeb.kpkg-dist || mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist || mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
/usr/bin/make EXTRAVERSION=.4-manav-kernel INSTALL_MOD_PATH=/usr/src/linux/debian/--initrd-image-2.6.31.4            \
                INSTALL_FW_PATH=/usr/src/linux/debian/--initrd-image-2.6.31.4/lib/firmware/2.6.31.4  \
                 ARCH=i386 modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.31'
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-source-2.6.31'
make[2]: Entering directory `/usr/src/linux-source-2.6.31'
**cp: cannot stat `/usr/src/linux-source-2.6.31/modules.order': No such file or directory**
make[2]: *** [_modinst_] Error 1
make[2]: Leaving directory `/usr/src/linux-source-2.6.31'
make[1]: *** [debian/stamp/install/--initrd-image-2.6.31.4] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.31'
make: *** [kernel_image] Error 2
root@manav-workstation:/usr/src/linux#

What is the solution for the above bug(s) ???

---

### Post by manavendra on 2009-11-19
Finally, when "make clean" also didn't worked then, I did

# rm -rf linux-source-2.6.31

Then, untar the linux source again and followed the above steps, keeping in mind to include,

# apt-get purge nvidia-common

After this, i got the new kernel image and upgraded the grub menu. PAE was working fine, and i got the following output:

root@manav-workstation:/home/manav# dmidecode | grep Size | grep MB
        Size: 2048 MB
        Size: 2048 MB

root@manav-workstation:/home/manav# free -m
             total       used       free     shared    buffers     cached
Mem:          3859        938       2921          0         42        475
-/+ buffers/cache:        420       3439
Swap:          980          0        980

For users, who want nvidia drivers can now do "sudo apt-get install nvidia-common" and get it running again. It would be excellent if you build your drivers from the source instead of using apt-get, specially, nvidia drivers. ;)

However, "free -m" still shows 3859 instead of 4096 which remains the last thing to figure out. :smile:

Happy Ubuntuing !!!

---

