---
title: "[SOLVED] Howto compile+install Highpoint Rocketraid 1810A/1820A open source driver"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by upp3rd0g on 2007-09-05
As I have been struggling 2 days to get my Highpoint Rocketraid 1810A working in Ubuntu 7.04 I want to share my experiences.

I installed default Ubuntu 7.04. I have an Nforce4 mainboard, Highpoint Rocketraid 1810A + 2 * 320GB Samsung SATA in raid1 setup. (Note: my OS is not installed on the raid1 disks.) After default Ubuntu installation the card is recognized as a Marvell MV88SX5081 SATA card. The attached drives are visible through sata_mv driver as standalone drives, but not as a raid1 setup.

As there is no binary driver available for Ubuntu I had to use the open source driver which can be found here:

[http://www.highpoint-tech.com/BIOS_Driver/rr1820a/Linux/rr18xx-opensource-v1.17-0123.tgz](http://www.highpoint-tech.com/BIOS_Driver/rr1820a/Linux/rr18xx-opensource-v1.17-0123.tgz)

As I don't have too much experience with compiling/installing my own drivers I struggled quite a lot, but in the end I succeeded. Below I will describe the needed steps. I will not elaborate on the steps as I am not really sure what every steps exactly does... 

1) Download driver + extract to <directory>
2) # apt-get install build-essential
3) # cd <directory>
4) # make KERNELDIR=/usr/src/linux-headers-2.6.20-16-generic ARCH=x86_64
Note: change "linux-headers-2.6.xxxxxxx" into your kernelversion. Use "uname -r" to determine current kernelversion.
5) Now you have 2 compiled drivers (modules?) named hptmv.o (for 2.4 kernels) and hptmv.ko (for 2.6 kernels)
6) Manually install driver into kernel as follows:
   a] # cp <directory>/hptmv.ko  /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/
   b] # depmod -a
   c] add "hptmv" to /etc/modules
   d] add "blacklist sata_mv" to /etc/modprobe.d/blacklist
   e] add "hptmv" to /etc/initramfs-tools/modules
7) # update-initramfs -k "2.6.20-16-generic" -c
8 ) reboot

If the system boots succesfully you can check if the new hptmv module is loaded correctly by comparing the output below against the output of your system:

# lsmod | grep hpt
hptmv                 237836  0 
scsi_mod            166968  5 usb_storage,sg,sd_mod,libata,hptmv

These instructions are a combination of the driver included "README" and the instructions found here:

[http://stefan.freyr.org/?page_id=6](http://stefan.freyr.org/?page_id=6)

I am not sure if blacklisting driver "sata_mv" is really needed... I am not sure if there is anything in my hardware configuration which would result in a different default Ubuntu installation, causing my howto to fail...

---

### Post by sjpwong on 2008-03-10
Thank you for posting your notes here :-)

---

### Post by okeefferd on 2008-07-17
I followed your directions, lsmod shows it loaded.  I installed the web gui but only the card shows up there, none of the 7 drives I have show up. (They do in the BIOS)

---

### Post by okeefferd on 2008-07-17
Hmm, I shutdown the drives (esata TBs) then turned them back on... all is well. BTW Using a rr2220.

EDIT: Not really

The drives are acting up still.  Sometimes they are all recognized, other times not.  I am going to apply the update for eSata free agent drives and see if that helps.  Otherwise i am at a loss.

---

