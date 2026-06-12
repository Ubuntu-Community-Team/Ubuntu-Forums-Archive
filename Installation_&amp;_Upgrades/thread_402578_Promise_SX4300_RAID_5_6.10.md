---
title: "Promise SX4300 RAID 5 6.10"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by z33k3r on 2007-04-05
Hey guys, was wondering if anybody has tried using one of the new Promise SX4300 PCIX SATA2 RAID5 cards...? I can not seem to get the installer to recognize the array... I tried using the SATAPROMISE driver on the installation menu with no luck. The driver's disc along with Promise's website show only support for Windows, RH, and SuSE... 

Time is something that I am loosing on this project. Anybody have any ideas?:confused:

---

### Post by z33k3r on 2007-04-05
Oh specs... those are helpful right... lol #-o 

Procs: 2 x AMD Opty 242's
Mobo: Tyan K8SE
MEM: 4gig Crucial ECC REG
RAID: Promise SX4300 SATA-2 PCI-X
HDD: 4 x WD 250gig RE's SATA-2


I was digging on Promises site and they say that they have a 'partial open linux driver'... anybody ever found this? I can't seem to find it on the Driver's Disc, nor their site... :mad:

---

### Post by z33k3r on 2007-04-06
Ok, so I found the partial open driver. Now, since I am a noob, I am assuming this would need to be compiled into an image that could then be burned to a disc, then installed to the server box with the RAID... but how do I go about that?

---

### Post by z33k3r on 2007-04-06
i hate doing this... bump

any ideas guys :confused:

---

### Post by z33k3r on 2007-04-09
bump

---

### Post by Ptero-4 on 2007-04-09
Check the size of the "driver". If it`s 100MB+ it`s likely an iso image (might be compressed), and you need to copy it to a non-RAID HD and then decompress (if required) and burn. If OTOH it`s a small file, like 10MB or less, then you need to add a non-RAID HD to your PC, install ubuntu there and compile the driver, then download the desktop CD and use reconstructor to insert the compiled driver in the install image and also install the driver in the "Live" environment, and finally burn to disc. In that way your customized LiveCD will have support for your RAID controller.

---

### Post by z33k3r on 2007-04-09
Yay, somebody's is helping! Woot. Looking up this process now. The drivers are all .c files I think. Will update soon! Thanks Ptero!

---

### Post by Ptero-4 on 2007-04-10
Well, it seems that it`s not an iso, but source code you`ll need to compile.

---

### Post by jdawiz on 2007-04-12
if someone could please point to a how-to on what the heck is being discussed that would be helpful.  Also, since you found the open driver could you post where you found it.  Thanks.

Jeremy

---

### Post by z33k3r on 2007-04-12
The partial driver is found half way down the page here [here...]("http://www.promise.com/support/download/download2_eng.asp?productId=147&category=driver&os=100&go=GO")

I have yet to have time to try this whole process. I am thinking that I might have to go with a system drive and then storage RAID. I just hate having to buy more drives...

---

### Post by z33k3r on 2007-04-12
The partial driver file includes a bunch of .c and .h files. It also includes two txt files with some instructions :

[quote=How-To-Build-Driver-From-Partial-Source-Code.txt]
**************** How to build driver from partial source code *****************

This reamde file will help you build driver binary file from partial source code. You can easily build driver according to the following steps:

Step 1. Set proper symbol link

	ln -s Makefiel.partial Makefile

Step 2. Set proper ftlib binary 

	make clean

Step 3. Build driver binary file.

	For kernel 2.4, just type:

		make	

	For kernel 2.6, type:
		
		make DRIVER_SRC_DIR=`pwd`

PS: Makefile script can receive parameters from command line, so if you want to build drive according to specific settings, such as build driver automaticly. Please refer to Makefile script itself or contact to the author.

********************************************************************************	
[/quote]

[quote=How-To-Build-Driver-Into-Kernel.txt]
***************** How to build driver into kernel from partial source *****************

This how-to document is used to help user build Promise FastTrak/NAPA/Shasta Seriel 
driver into kernel step by step, I will take FT4100 as a example.

Note: KENNEL_SRC_DIR is the root directory of your kernel source tree location.

Step 1. unpack ft4100_partialb32.tgz and cp ft4100_partial directory to proper location, 
then make proper symbol links.
	
		tar -zxvf ft4100_partialb32.tgz
		cp -rf ft4100_partial KENNEL_SRC_DIR/drivers/scsi
		cd KERNEL_SRC_DIR/drivers/scsi/ft4100_partial
For Kernel 2.6
		ln -s Makefiel_buidin2.6 Makefile

	For 32bit Kernel	
		ln -s ftlib.o.32 ftlib.o
	For 64bit kernel
		ln -s ftlib.o.64 ftlib.o	
For Kernel 2.4	
		ln -s Makefile_buidin2.4 Makefile	

	For 32bit Kernel	
		ln -s ftlib.obj.32 ftlib.obj
	For 64bit kernel
		ln -s ftlib.obj.64 ftlib.obj	

Step 2. set some related macros to header files

	File napa_cfg.h (if you build driver in 2.4 kernel, you need not
modify this file )
		Add  #define _LINUXDRIVER
	
        File cfg_linux.h: 

	Take AMD64 platform as a example:

		you need unmark following two lines to the head of file:

			#define _AMD64B
			#define _64BPLATFORM   	


Step 3. Modified Kconfig/Config.in file in KERNEL_SRC_DIR/drivers/scsi 
	
	Add below section under "SCSI low-level drivers" menu
	
	For kernel 2.6, modify Kconfig file


		config SCSI_PROMISE_FT4100
		tristate "Promise FT4100 Seriel SATA-RAID support"
		depends on PCI && SCSI
		help
	  	This driver supports the Promise FT4100 series SATA-RAID cards.

	  	<http://www.promise.com>

	For kernel 2.4, modify Config.In file
		
		if [ "$CONFIG_PCI" = "y" ]; then
   			dep_tristate 'Promise SX4100 SATA-RAID support' CONFIG_SCSI_PROMISE_FT4100 $CONFIG_SCSI
		fi

Step 4. Modified Makefile in the same location as Kconfig/Config.In

	Add one line to Makefile:

	For kernel 2.6, add following line:

		obj-$(CONFIG_SCSI_PROMISE_FT4100)	+= ft4100_partial/

	For kernel 2.4, add following lines:
	
		subdir-$(CONFIG_SCSI_PROMISE_FT4100)	+= ft4100_partial
		ifeq ($(CONFIG_SCSI_PROMISE_FT4100),y)
  			obj-$(CONFIG_SCSI_PROMISE_FT4100)	+= ft4100_partial/FastTrak.o
		endif

Step 5. Enter KERNEL_SRC_DIR, build kernel with FastTrak driver build in.

		cd KERNEL_SRC_DIR
		make menuconfig  (you need config scsi/scsi disk/FT4100 support as build-in 
				  state (*) in config menu, then save your configuration)

		make / make bzImage

************************************************************************************************* 
[/quote]

---

### Post by z33k3r on 2007-04-19
I have downloaded 7.04 and  tried the pre-mentioned steps but no luck. Will try again with 6.10...

---

### Post by z33k3r on 2007-04-19
Does anybody have a tutorial link to which would show how to use Reconstructor for building an ISO based off the current system (once I have the drivers figured out, that is...), or will it just do that right off the bat?:confused:

---

### Post by z33k3r on 2007-04-19
So this is what I have done. I have installed both 6.10 and 7.04 onto a single drive utilizing the integrated SATA controller on the motherboard then setup the three remaining drives into a 2+1 RAID5 on the Promise controller so that I have something to test with before I burn the custom image and rebuild my 3+1 RAID5. 

I have gone through all the steps but it keeps giving me errors. I will have to try again after work so I can c&p the errors, but when I go to run the Makefile commands, it dies. So I am sure that their instructions are lacking and I am missing some steps?

---

### Post by urielskie on 2007-09-06
Hi, I also have same problem. did you happen to solve d issue of installing Promise SX4300 on your Ubuntu?

---

### Post by z33k3r on 2007-09-07
No, we ended up going with another raid card... :(

---

