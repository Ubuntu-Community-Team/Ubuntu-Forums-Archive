---
title: "help me to install intel 537 modem"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Farooq3k on 2007-03-10
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_Feb_21


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0c.0	e159:0001	8086:0003	Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:0c.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

===================================
 The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!! 
 The CPU cannot control the modem until this situation is corrected!!
 Possible corrections are:
   1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
   Instructions for accessing BIOS are at:
      [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
   2a) Add an option "pci=routeirq" to the kernel boot up line.
      Here is an example paragraph from  /boot/grub/menu.lst :
	title           Ubuntu, kernel 2.6.15-26-686
	root            (hd0,6)
	kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
	initrd          /boot/initrd.img-2.6.15-26-686
	savedefault
   2b) Same as above, but use "pollirq" instead of "pci=routeirq". 
   3) Within some BIOS setups, IRQ assignments can be changed.
   4) On non-laptop systems, moving the modem card to another slot has helped.
   5) Sometimes upgrading the kernel changes IRQ assignment.
=====================================

 For candidate modem in PCI bus:  00:0c.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
 


 Vendor e159 is Tiger Jet , [http://www.tjnet.com/](http://www.tjnet.com/)
  Controller e159:0001  translates PCI commands to the serial link used by
     the silabs DAA from the si3034, si3044 and si3056 family.
  The e159:0001  with SubSystem 8086:0003 is TJ320 v2.0 
  is the first and still most common of the Intel537 modem family.
  However primary controller chip can have broader uses:  [http://www.tjnet.com/chips/tiger320.htm](http://www.tjnet.com/chips/tiger320.htm)
  Though having its own driver package under 2.4.n. kernels,
  support (if any) from Intel is now included within the Intel-537EP package.

 ====== end Tigerjet section =======
 In 2006, Intel appears to have ceased updates for Linux.
 For the INTEL537 and INTEL536 chipset modems, the most current support is provided at:
       [http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/](http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/)
 But regular support is not available, see:  [http://archives.linmodems.org/24939](http://archives.linmodems.org/24939)
:
 The outdated official Intel support packages can be accessed through:
       [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)
 Read Intel.txt and Modem/YourSystem.txt for follow through guidance.


Writing Intel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 15:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by teaker1s on 2007-03-11
[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

THERE IS A 537EP IS THIS THE SAME MODEL?

---

### Post by chuck_h1987 on 2007-08-03
Actually i think all the 537's can be controlled by the same driver if you use the EXPORT_MODEM=537EP, EG ect ect.

---

### Post by Sepero on 2007-09-17
If you have an Intel 537ep modem, you can download the compiled driver here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

