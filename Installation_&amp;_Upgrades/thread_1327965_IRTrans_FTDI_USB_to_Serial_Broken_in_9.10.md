---
title: "IRTrans FTDI USB to Serial Broken in 9.10"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Beezleblub on 2009-11-16
Hiya, 

I upgraded my Myth Server to 9.10 over the weekend.
All seems to work well, Except My IR Trans module. 

IRTrans is using a FTDI USB/ Serial conversion.
It correctly installs the device as TTYUSB0. 
But IRServer fails to connect.
 

This was working fine in my 9.04 installation.  
IR Trans moduel works ok on my windows pc, so harware is ok too.

Have found few complaints online, but no fix this far :( 
Anyone knows how to work-around to fix FTDI support in Karmic ? 

Thanks !

---

### Post by Beezleblub on 2009-11-16
Some more detail on this issue:
Running IR Server :
sudo /usr/local/irtrans/irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
[sudo] password for dirk: 
Init Server Socket done
Init Events done
Opening Device: /dev/ttyUSB0
IRTRans Send status: 0 - 0  SEQ:121  TO:250
IRTRans Send status: 0 - 0  SEQ:121  TO:250
IRTRans Send status: 0 - 0  SEQ:121  TO:250
IRTRans Send status: 0 - 0  SEQ:121  TO:250
IRTRans Send Done: 4
IRTRans Send status: 0 - 0  SEQ:122  TO:250
IRTRans Send status: 0 - 0  SEQ:122  TO:250
IRTRans Send status: 0 - 0  SEQ:122  TO:250
IRTRans Send status: 0 - 0  SEQ:122  TO:250
IRTRans Send Done: 4
Init communication ...
Error opening COM/USB Port / LAN Device


lsusb output :
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0403:fc60 Future Technology Devices International, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 046d:c714 Logitech, Inc. 
Bus 005 Device 003: ID 046d:c713 Logitech, Inc. 
Bus 005 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 051c:0003 Shuttle, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

... and dmesg |grep usb :
dmesg |grep usb
[    0.202377] usbcore: registered new interface driver usbfs
[    0.202377] usbcore: registered new interface driver hub
[    0.202377] usbcore: registered new device driver usb
[    0.908135] usb usb1: configuration #1 chosen from 1 choice
[    0.908509] usb usb2: configuration #1 chosen from 1 choice
[    0.908788] usb usb3: configuration #1 chosen from 1 choice
[    0.909086] usb usb4: configuration #1 chosen from 1 choice
[    0.909371] usb usb5: configuration #1 chosen from 1 choice
[    1.652068] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.841709] usb 2-1: configuration #1 chosen from 1 choice
[    2.088020] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    2.274334] usb 4-2: configuration #1 chosen from 1 choice
[    2.284159] usbcore: registered new interface driver hiddev
[    2.302495] input: Shuttle Inc VFD Module as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[    2.302584] generic-usb 0003:051C:0003.0001: input,hidraw0: USB HID v1.11 Keyboard [Shuttle Inc VFD Module] on usb-0000:00:1d.2-2/input0
[    2.302598] usbhid 4-2:1.1: couldn't find an input interrupt endpoint
[    2.321297] input: Shuttle Inc VFD Module as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/input/input4
[    2.321373] generic-usb 0003:051C:0003.0002: input,hidraw1: USB HID v1.11 Device [Shuttle Inc VFD Module] on usb-0000:00:1d.2-2/input2
[    2.321395] usbcore: registered new interface driver usbhid
[    2.321399] usbhid: v2.6:USB HID core driver
[    2.516025] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.697680] usb 5-2: configuration #1 chosen from 1 choice
[    2.981616] usb 5-2.2: new full speed USB device using uhci_hcd and address 3
[    3.153761] usb 5-2.2: configuration #1 chosen from 1 choice
[    3.165959] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.2/5-2.2:1.0/input/input5
[    3.166048] generic-usb 0003:046D:C713.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.3-2.2/input0
[    3.260012] usb 5-2.3: new full speed USB device using uhci_hcd and address 4
[    3.462795] usb 5-2.3: configuration #1 chosen from 1 choice
[    6.553090] usbcore: registered new interface driver usbserial
[    6.553161] usbcore: registered new interface driver usbserial_generic
[    6.553164] usbserial: USB Serial Driver core
[    6.591949] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.3/5-2.3:1.0/input/input6
[    6.592167] logitech 0003:046D:C714.0004: input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.3-2.3/input0
[    6.663645] usb 2-1: Detected FT232BM
[    6.663648] usb 2-1: Number of endpoints 2
[    6.663651] usb 2-1: Endpoint 1 MaxPacketSize 64
[    6.663654] usb 2-1: Endpoint 2 MaxPacketSize 64
[    6.663656] usb 2-1: Setting MaxPacketSize 64
[    6.667018] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB0
[    6.667086] usbcore: registered new interface driver ftdi_sio

---

### Post by metalac on 2009-11-16
I have an identical issue.  Everything worked prior to upgrade to 9.10. Any assistance would be greatly appreciated.  

I've tried everything, but nothing seems to work.  A simple ```
cat /dev/ttyUSB0
``` doesn't produce anything when I push buttons.  I've tried unloading/loading related modules and so forth.  I'm thinking now of opening up the box and removing all of the cards I can just to verify it's not some sort of IRQ conflict issue, but I doubt it since the device seems to be created correctly.

---

### Post by Alexxf on 2009-11-16
Confirm
same problem in 9.04 working fine but on 9.10 don't work.

---

### Post by Beezleblub on 2009-11-16
It's related to :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857)

"either patch the proposed kernel with the
2.6.31.5 code for ftdi_sio, or maybe start over with a new kernel based
on 2.6.31.5."

How to patch the current Kernel to use the updated ftdi_sio ?
Or is is possible to upgrade the Kernel to 2.6.31.5 ?

Thanks.

---

### Post by carl.fischer on 2009-11-18
Arg! I was about to post some comments on how I'd failed to solve this problem and then X suddenly quit. Maybe that's best...

Essentially I managed to recompile the current ftdi_sio and usbserial modules by following the instructions at the top of [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild). You need to install the linux-source package, then unpack the contents of the tar.bz2 archive into /usr/src and run the commands in the drivers/usb/serial folder.

This doesn't help because I don't have the patches to fix the problem. The patches mentioned at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857) don't seem to apply directly to that source tree.

I tried downloading the latest source from kernel.org and copying the whole drivers/usb/serial folder into the ubuntu sources but this won't compile, probably because there have been changed elsewhere in the kernel that affect these modules.

For information I'm having this problem with an XSens MTx inertial sensor. The issue occurred when I upgraded to Karmic a few days ago.

---

### Post by lawrni on 2009-11-19
Hi 
 
I've got the same issue with the ftdi driver in 9.10.  Interestingly, I can use minicom to open the serial port and then my application can then speak to the ftdi usb serial device no problem.  This is only a short term fix - I'd really like to know how to install the ftdi driver from downloading the 2.6.31.6 kernel source from kernel.org.  
 
I've tried going to drivers/usb/serial and keying 'make' - but I get all sorts of compile errors (showing my in-experience here).
 
I think I could install the 2.6.31.6 kernel from kernel.org in ubuntu, but do I risk having other parts of my system not working if I do this ?
 
If anyone out there could give a quick tutorial (or show me a few links on how to do this) on how to compile and insert the new driver in the current kernel it would help me (and others) a lot I think.

---

### Post by carl.fischer on 2009-11-19
Ubuntu keeps previous kernels. You can just hit escape at the start of the boot process to get the GRUB menu, and then choose your previous kernel. That gets my USB device working again but breaks the MacBook Pro's touchpad. (The external mouse is OK so I can keep working until an update is available.)

-- Carl

---

### Post by lawrni on 2009-11-19
Hi Carl,
 
Maybe I'll give this a go then - just install the kernel from kernel.org and reboot.  If things start to go pear-shaped, use grub to switch back to the original kernel.
 
I'd still be interested if there is a relatively easy way to compile the updated ftdi driver against the current kernel.
 
Many thanks
 
Nick

---

### Post by xblx on 2009-11-20
I got the irtrans to work under Karmic by compiling the 2.6.31.6 kernel from kernel.org and by replacing the ftdi_sio module. Result is a nicely working HTPC. Aside from this unfortunate issue with the ftdi_sio kernel module supplied in Karmic which hopefully will be resolved in some kernel update later on there is now out-of-the box support in lcdproc for the irtrans module.

Short summary on how I got it to work is above, the long "overkill" version is below where I recompiled the complete kernel only to get a working ftdi_sio module. I am sure that there is a faster way to do it, however I did not manage to get a module that would load by only compiling a single module. Suggestions are welcome :).

Create two new directories within your home:

```
# cd
# mkdir kernel-tmp
# mkdir kernel
# cd kernel-tmp
```

Download the kernel source for 2.6.31.6 and unpack the kernel:

```
# wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.6.tar.bz2
# tar xjvf linux-2.6.31.6.tar.bz2
```

Download the kernel source for the current kernel using apt and satisfy the build dependencies:

```
# cd
# cd
# cd kernel
# sudo apt-get build-dep linux-image-$(uname -r) fakeroot
# sudo apt-get install kernel-package
# apt-get source linux-image-$(uname -r)
# cd linux-$(uname -r)
```

Prepare the kernel for rebuilding to the currently installed kernel:

```
# cp /boot/config-$(uname -r) .config
# make oldconfig
```

Answer any questions with the default answer if applicable
Remove the debugging option to avoid large file sizes:

```
# nano .config
```

Search for the string "CONFIG_DEBUG_INFO" (CTRL-W) and replace the value to "CONFIG_DEBUG_INFO=n"
Save the change using CTRL-O and exit the file with CTRL-W

Now we are changing the makefile to make sure the kernel has the same identifier as the running kernel:

```
# nano Makefile
```

Change the EXTRAVERSION value to EXTRAVERSION = -14
Save in nano with CTRL-O and exit with CTRL-X

Now copy (replace) the new source for the FTDI driver from the downloaded kernel to the source retrieved using apt

```
# cd
# cp kernel-tmp/linux-2.6.31.6/drivers/usb/serial/ftdi* kernel/linux-image-$(uname -r)/drivers/usb/serial/
```

Build the kernel using the following command:

```
# sudo make-kpkg --rootcmd fakeroot --initrd --append-to-version=-generic kernel-image
```

Test your new ftdi module:

```
# sudo rmmod ftdi_sio
# sudo insmod drivers/usb/serial/ftdi_sio.ko

```
The irserver should work now, test this by typing:

```
# sudo /usr/local/irtrans/irserver /dev/ttyUSB0
```

Make the change permanent by the following command (replace the old module):

```
# sudo cp drivers/usb/serial/ftdi_sio.ko /lib/modules/$(uname -r)/kernel/drivers/usb/serial/
```

I hope this works for you as well. Let me know if the instructions work for you or if you have a faster solution.

---

### Post by buthus on 2009-11-21
Thank you for your detailed instructions, xblx. The tutorial works fine for me. It took me four days to find this page and to solve my problem - so - BIG THANKS!

I detected that a small detail is different on my system than in your tutorial:
I could not find any package named *linux-source-2.6.31-14-generic*. I used the package *linux-source* instead (which uses V2.6.31.14-27). Therefore my folders have slightly different names.

Some minor improvements:
It might be faster to run *make modules* instead of compiling everything. To change the Makefile might be the fastest solution, but you should know what you are doing ... 

There is already a bug notice available for the Ubuntu crew:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857)

Greetings,
buthus

---

### Post by lawrni on 2009-11-22
Hi xblx,
 
Many thanks for your detailed explanation of how to compile the 2.6.31.6 ftdi module against original kernel source. I followed your instructions and managed to get my ftdi serial working without minicom.  Like buthus I've been trying to do this for days.
 
I also noticed the same problem buthus had - in that there was no linux-source-2.6.31-14.  I used the following instead:
 
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)
 
This gave me the correct source code, only it was then called linux-2.6.31.6 not linux-2.6.31.6-generic - so I just tweaked the paths and it worked.
 
Thank you for taking the time to write out this detailed explanation - this has helped me a great deal.
 
Lawrni :D:D:D

---

### Post by xblx on 2009-11-22
I updated the instructions to refer automatically to the running kernel is this obviously is not the same for everybody. Thanks for the comments. I hope that a new Ubuntu kernel update will pull in the latest 2.6.31 kernel otherwise we will need to go through this procedure again.

Regards, xblx

---

### Post by CraigVanD on 2009-11-25
Thanks xblx!  In a couple of places I needed to use linux-2.6.31 instead of $(uname -r), but now my DLP-2232-PB-G works again with the Ubuntu 2.6.31-15 kernel.

---

### Post by wamarler on 2009-12-04
My thanks to you too xblx! If there's a better way to just build the ftdi_sio.ko module by itself it'd be great to post it... this builds EVERYTHING.

---

### Post by tz1 on 2009-12-06
Makefile (remember that indents **MUST BE TABS** and not spaces)

Create a new directory with this file in it, copy the working ftdi_sio.* into the same directory and type "Make".  In a few seconds you will have ftdi_sio.ko for the current kernel you can do insmod, or copy it to /lib/modules/`uname -r`/kernel/drivers/usb/serial to replace the existing broken one.

```

KDIR:=/lib/modules/$(shell uname -r)/build

EXTRA_CFLAGS += -I$(KDIR)/drivers/usb/serial -I/usr/src/linux-headers-$(shell uname -r)/include

obj-m:=ftdi_sio.o

default:
	$(MAKE) -C $(KDIR) $(EXTRA_CFLAGS) SUBDIRS=$(PWD) modules

clean:
	$(RM) *.mod.c *.o *.ko .*.cmd Module.symvers Module.markers modules.order

```

---

### Post by hipogrito on 2009-12-07
Hi,

I tried the last easy way and it works perfect for me.

Thank you very much for the help!!!

Kind regards,
Hipo

---

### Post by Bloemetjesgordijn on 2009-12-18
Hi

Just my 2 cents:

The solution of Kendrick Shaw ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460857)) worked for me.

Cheerz

---

