---
title: "Need Help!! Internet wont work on 9.10 (64bit)!"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by cardozo on 2010-02-16
I have just dual booted my pc to run windows 7(64 bit) and ubuntu 9.10 (64 bit). This is my FIRST time using ubunutu and i have spent the whole day trying to get my internet working but with no success. I have come so close to giving up on ubuntu but for some reason i just cant let go!!
 
When i type in ifconfig in the terminal i can see that i have an ip address assigned and i can ping my router.

My motherboard came with linux drivers and i tried installing the LAN drivers with the included instructions i have got no where. I did find out that the file name in the instructions was wrong and the actual name is r8168-8.012.00.

Here are the instructions-
Step 1: sudo tar vjxf r8168-8.005.02.tar.bz2

Step 2: sudo cd r8168-8.005.02

Step 3: sudo make clean modules

Step 4: sudo make install

Step 5: sudo depmod -a

Step 6: sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/
This will move the r8169 kernel module into your home directory.

Step 7: sudo depmod -a
Rebuild the kernel module dependencies.

Step 8: sudo mv /boot/initrd.img-`uname-r` /boot/initrd.img-`uname -r`.ubuntu
make a backup of the original initrd.

Step 9: sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
Create a new initrd WITHOUT the r8169 module

Step 10: sudo vim /etc/modules
	=>and add "r8168" (without the quotes) at the end of the file.

Step 11: init 6
reboot the system

---------------------------------
This is what happens when i execute step 3
make -C src/ clean
make[1]: Entering directory `/home/hometheatre/Desktop/r8168-8.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/hometheatre/Desktop/r8168-8.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/hometheatre/Desktop/r8168-8.012.00/src'
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/hometheatre/Desktop/r8168-8.012.00/src'
make: *** [modules] Error 2

Can anyone make sense of this? Is there an easier way to connect to the internet? 

Thanks in advance.

---

