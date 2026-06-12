---
title: "couldnot install modem driver"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by sowhat12345 on 2008-06-17
I have just installed ubuntu 8 . It works great :) But I couldn't install modem driver (BIPAC BILLION USB 7000 MODEM) . I have downloaded drivers for linux from billions web site. It has a readme txt which writes :
-----------------------------------
This document describes the steps of installing the E2 or Hasbani (BIPAC-7000) on the Linux.
Driver Version 062802_REL1.7

First, uncompressing the packaged: USBNET_E2_LINUX_062802_REL1.7.tar.gz
	#tar zxvpf USBNET_E2_LINUX_062802_REL1.7.tar.gz
A directory named e2 will be created under current directory.

Second, Changing directory to the "e2" directory.
	#cd e2

Third, compiling the source code.
	#make

At last, copy the firmware file "CnxE2Fw.bin" to directory "/etc".
	#cp CnxE2Fw.bin /etc/CnxE2Fw.bin


Now, you can install the driver by the command below under current directory:
	#insmod e2.o

If you would like to installing driver anywhere else, Please copy the e2.o to 
the directory: /lib/modules/2.4.xx-xxx/kernel/drivers/usb first.

If the network doesn't up automatically, you must run the following commands to activate the net adapter.
	#ifconfig hsb0 up
	#dhcpcd -n hsb0



Upgrade the firmware:
	Replace the firmware file "/etc/CnxE2Fw.bin" with the new release. Note that the file
	name must be case sensitive.
-------------------------------------
But I couldn't understand anythink :( 
It has also a folder called "e2source" , and a USBNET_E2_LINUX_062802_REL1.7.tar which I can open it just on ubuntu. It is the first time I'm installing something to system.
Can you help to install my modem driver ? Thank you ...

---

### Post by dstew on 2008-06-17
In general, dial-up modems for PC's are "Winmodems", that are light on hardware, and use software to emulate the hardware. They need drivers to make them work, so you are right in trying to install a driver.

There is an Ubuntu way to install drivers for these modems. See the [Dialup Modem Howto]("https://help.ubuntu.com/community/DialupModemHowto").

If you want to go ahead an try to install the driver you downloaded, you can do it this way. First, identify where the downloaded tar.gz file is (often called a "tarball" in Linux). It should be on the desktop, or in your Home folder. Once you find it, double-click it. It should extract itself into a folder named e2.

The e2 folder contains source code for the driver, not the final binary code. The source code needs to be compiled in order to create the binary driver file. In order to compile, you need to install a compiler program and related headers. Open the Synaptic package manager, (System --> Administration) and install the package **build-essential** and **linux-headers** for your particular kernel. To find out what your kernel is, open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
uname -r
```

Once you have the build-essential and linux-headers packages installed, you can do the rest of the installation as directed by the ReadMe. Use the terminal command line.

---

### Post by sowhat12345 on 2008-06-17
It says me write in terminal #make . but it doesn't work :(

---

### Post by dstew on 2008-06-17
What error do you get?

---

### Post by sowhat12345 on 2008-06-17
I mean I don't know how I can compiling the source code ... I open the terminal , I went to e2source folder (I wrote "cd e2source" in terminal) then I wrote "make" and terminal writes 
mekefile:50:***missing seperator. Stop.
I don't understand anythink :( It is the first time that I install something...

---

### Post by dstew on 2008-06-17
According to the instructions, you should be in the e2 directory, not the e2source directory.

---

### Post by sowhat12345 on 2008-06-17
dstew you are right . I tried as you say .. But now did something else ! It wrote me and didn't happened anything
-------------------------
gcc -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -DCPU=686 -march=i686  -DMODULE -D__KERNEL__ -DLINUX  -I/lib/modules/`uname -r`/build/include -c usbsndcm.c -o usbsndcm.o
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/preempt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/slab.h:14,
                 from hasbani.h:28,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:79: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:79: error: requested alignment is not a constant
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:200: error: requested alignment is not a constant
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:35,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/irq.h:24,
                 from /lib/modules/2.6.24-16-generic/build/include/asm/hardirq_64.h:5,
                 from /lib/modules/2.6.24-16-generic/build/include/asm/hardirq.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /lib/modules/2.6.24-16-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/preempt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/slab.h:14,
                 from hasbani.h:28,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/asm/processor_64.h:29:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/irq.h:24,
                 from /lib/modules/2.6.24-16-generic/build/include/asm/hardirq_64.h:5,
                 from /lib/modules/2.6.24-16-generic/build/include/asm/hardirq.h:4,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/interrupt.h:11,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h: In function ‘user_mode’:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: for each function it appears in.)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:50: error: ‘USER_RPL’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h: In function ‘user_mode_vm’:
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:54: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-16-generic/build/include/asm/ptrace.h:54: error: ‘USER_RPL’ undeclared (first use in this function)
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:54,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/interrupt.h:12,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.24-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.24-16-generic/build/include/linux/timer.h:5,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/sched.h:87,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/interrupt.h:12,
                 from /lib/modules/2.6.24-16-generic/build/include/linux/usb.h:15,
                 from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/linux/ktime.h: In function ‘ktime_set’:
/lib/modules/2.6.24-16-generic/build/include/linux/ktime.h:84: warning: comparison is always false due to limited range of data type
In file included from hasbani.h:29,
                 from usbsndcm.c:20:
/lib/modules/2.6.24-16-generic/build/include/linux/usb.h: In function ‘usb_register’:
/lib/modules/2.6.24-16-generic/build/include/linux/usb.h:1013: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
usbsndcm.c: In function ‘CmCommandRcv’:
usbsndcm.c:184: error: ‘CONFIG_HZ’ undeclared (first use in this function)
usbsndcm.c: In function ‘CmCommandSend’:
usbsndcm.c:259: error: ‘CONFIG_HZ’ undeclared (first use in this function)
usbsndcm.c: In function ‘CmPacketSend’:
usbsndcm.c:327: error: ‘CONFIG_HZ’ undeclared (first use in this function)
make: *** [usbsndcm.o] Error 1
------------------------

---

### Post by dstew on 2008-06-17
Did you install the build-essential and linux-headers packages? It looks like you probably did. If so, I think these errors are going to be hard to get around. It probably means whoever wrote the makefile for that driver made some mistakes that come out when you try to compile it in an Ubuntu system.

In that case, it might be better to try a new way to get the modem working. That is the way described in the Ubuntu [DialUpModem HowTo]("https://help.ubuntu.com/community/DialupModemHowto"). Download the [scanModem]("http://132.68.73.235/linmodems/packages/scanModem.gz") script first. Here are [instructions on using ScanModem]("https://help.ubuntu.com/community/DialupModemHowto/ScanModem"). When scanModem is run, it creates a bunch of folders with information in them that will help us figure out how to get the modem working. Usually, there will be a pre-compiled driver that will work.

---

### Post by sowhat12345 on 2008-06-17
dstew Thank you very much ! But I don't think that I'm able to do all of them :( If there is someone who have used the same modem help me! If not no problem :(

or explaing something easier :)

I haven't install build-essential and linux-headers . But it lloks like installed ... I think linux-headers are isnatlled . But I couldn't find build-essential ...

---

### Post by dstew on 2008-06-17
Look in the Synaptic package manager to see if build-essential and linux-headers for your kernel are installed. The check box will be green if they are installed.

---

### Post by sowhat12345 on 2008-06-17
linux-headers are green (installed)
But I couldn't find "build-essential" , there is not "build-essential" in the list.

---

### Post by sowhat12345 on 2008-06-18
How Can I install build-essential ?
I try it using the terminal : sudo apt-get install build-essential
and the results :
rediang package lists... done
building dependency tree
reading state information...done
E: Could'n find package build-essetials
:( There is another way to install build-essential??

---

### Post by dstew on 2008-06-18
Do you have an internet connection on that computer? Maybe build-essential is not on the CD, and you need to connect to the internet. But, since you are trying to get your modem working, of course you are not connected.

To install packages off-line, you can use the [nonetdebs service]("http://nonetdebs.unixpod.com/"). You upload a text file of the status of your off-line computer, and they provide you with links to Debian packages to install. You download the packages and copy them to your off-line computer, and install them with the dpkg program.

---

### Post by sowhat12345 on 2008-06-18
OK thank .I will do it . But first I want ask something ? What is build-essential ? and the other packages which I will setup them. Also In the new versions of Ubuntu 8.xx I will have them as default or I will have to install them again?
As an another solution can I install the drivers using wine?

---

### Post by sowhat12345 on 2008-06-18
I upload my status.txt , but I couldn't download any package.

---

### Post by dstew on 2008-06-18
I have not used nonetdebs myself, being blessed with a good internet connection, so it is hard for me to say what went wrong. In addition to the status.txt file, you also need to enter the release, locale, and architecture of your off-line system. See the [MiniHowTo]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11").

EDIT: The build-essential package contains (or rather refers to, and installs) the compiler, some standard libraries, and the make utility program. It is possible you already have these installed, but I could not verify that they are automatically installed in Hardy. Certainly it seems you have a compiler, and make. I just don't know about the libraries (standard header files).

---

### Post by sowhat12345 on 2008-06-19
linux-headers are installed . I have to install the build-essential. I did what I see in the pictures from the site dstew's gave me. But in the list page It didn't display any text box to write what package I want :(  (also I try it with IE but it doesn't work too) 
I googled the "build-essential package" I download it from the ubuntus page . I try to install but it gives error too :( :( :(
It's enough :( 
status error :  dependency is not satisfiable:libc6-dev|libc-dev
What should I do now ?:confused: :( :(

---

### Post by dstew on 2008-06-19
You can download and install the libc6-dev package...

---

### Post by sowhat12345 on 2008-06-19
dstew I try it also that . But it give me again an error :
Depency is not satisfiable : libc6 

:(

dstew thank you for help me by the way....

---

### Post by dstew on 2008-06-19
Now you have to install the libc6 package. I think the file name is libc6_2.7-10ubuntu3_i386.deb.

If you try to install a package this way, downloading the .deb file and installing with dpkg, you end up having to get more files to satisfy dependencies. That is why the nonetdebs service is valuable, because they give you all the dependencies at once (at least if it is working correctly). If you keep going like this, one file at a time, you will eventually get everything done, I think.

You might want to think again about trying the ScanModem way to get software for the modem.

---

### Post by sowhat12345 on 2008-06-19
If I give you my status.txt can you give me the download link for packed . Because I couldn't find something from nonetdebs service ?

---

### Post by sowhat12345 on 2008-06-23
I had to format the pc because of a problem my pc had like every time . While formatting something drew my attention. After the formatting process, I wanted to run the drivers of modem. Before I started to run, the third light on the modem wasn't turned on. Then I run the modem and when I am on the desktop, it is always turned on. And when I am on the desktop of Ubuntu, that light is always turned on and I have just noticed it. In my opinion, that means the modem read the drivers automatically. So, what can I do to connect the Internet ?

---

### Post by dstew on 2008-06-23
If the modem is working, there should be a connection to configure in System --> Administration --> Network.

---

### Post by sowhat12345 on 2008-06-23
I looked at System --> Administration --> Network . I unlocked with my password . But I couldn't fill all the blank text boxes .

---

### Post by dstew on 2008-06-25
That probably means the modem driver is not working. I suggest you try the Scanmodem method I outlined earlier.

---

### Post by sowhat12345 on 2008-06-26
I try the scanmodem method which you told me. It gave me a text file : modemdata.txt :
Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_06_21

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0572:cb06 Conexant Systems (Rockwell), Inc. 
 ID 0b38:0010  

USB modems not recognized

For candidate card in slot 02:05.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:05.0	14f1:2f00	14f1:2004	Communication controller: Conexant HSF 56k HSFi Modem 

 Modem interrupt assignment and sharing: 
  9:          1   IO-APIC-fasteoi   acpi
 --- Bootup diagnostics for card in PCI slot 02:05.0 ----

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 02:05.0:
	Modem chipset  detected on
NAME="Communication controller: Conexant HSF 56k HSFi Modem "
CLASS=0780
PCIDEV=14f1:2f00
SUBSYS=14f1:2004
IRQ=9
IDENT=hsfmodem

 For candidate modem in:  02:05.0
   0780 Communication controller: Conexant HSF 56k HSFi Modem 
      Primary device ID:  14f1:2f00
 Support type needed or chipset:	hsfmodem
 


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.07full_k2.6.24_16_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,
 linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 22:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
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


 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

what am I going to do now?

---

### Post by dstew on 2008-06-27
These are the instructions to install the driver for your modem:

> From [http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php)
download hsfmodem-7.68.00.07full_k2.6.24_16_generic_ubuntu_i386.deb. zip
Under Linux unpack with:
$ unzip hsfmodem*.zip
Then install with:
$ sudo dpkg -i hsfmodem*.deb
Subsequently, the modem should be found with
$ sudo wvdialconf /etc/wvdial.conf
Edit in your personal information with:
$ sudo gedit /etc/wvdial.conf
and try dialing out with:
$ sudo wvdial.
See DOCs/Testing.txt for details.
The link in the instructions does not work. To download the driver, use this link:
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)
Click on the link for Linux Distributions, Hardy 8.04 etc. That should get you to this page:
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
Pick the package that matches your kernel version, download it, and install it according to the instructions in the Scanmodem output (in the quote above).

---

### Post by sowhat12345 on 2008-06-29
I download the hsfmodemxxx.zip. But when I started the installation it gave me again an error :
dependency is not satisfiable: alsa-driver-linuxant 
:(

In a different forum which I ask the same question , the members told me to install some packages. But when I install them the installation gave me error. The members told me also the problems can be solved if I install the other packages which are necessary for the other installations. But the packages which are necessary are about 20-30 packages . Because almost all the packages are missing...:( 
The installation of Ubuntu was perfect,it didn't give me any error or something. so how can it be like this ?

---

### Post by dstew on 2008-06-29
It is like this because you are trying to get a Winmodem to work in Linux. These modems were designed for Windows, with proprietary software that was designed for Windows. The manufacturers give little support for Linux. Ubuntu is forbidden by license from distributing these drivers with the operating system, so you have to try to get them yourself, if they exist at all.

Again, you can try to download and install all the dependencies. That is hard work when you don't have an internet connection, but it can be done. I am not sure why nonetdebs didn't work for you, lots of people use it without problems. That is the easiest way.

Of course, the easiest way to solve your problem would be to get a real modem, one that plugs into the serial port. Then you wouldn't need any drivers.

---

### Post by sowhat12345 on 2008-06-30
If I go to my friend whoses modem is not USB , can Ubuntu install the drivers automatically ? If it installs I will be online and I can install built-essential :
sudo aptitude install build-essential
But I think that it can not work because it gives me again error...
I'm gonna try it in 1-2 days...

---

### Post by sowhat12345 on 2008-06-30
I went to my friend with my computer but could not connect to internet . My friends modem's cable was like that [http://img170.imageshack.us/img170/1872/rj601ij3.jpg](http://img170.imageshack.us/img170/1872/rj601ij3.jpg) . but my computers is smaller :(
I think I must have a ethernet card ?
Is it possible to install the drivers of my Mipac 7000 modem in Ubuntu without ethernet card?

---

### Post by dstew on 2008-06-30
The modem in your computer has a conexant chipset, and is a dial-up modem called a Winmodem. The manufacturer doesn't matter. You can install the drivers by downloading them off-line as we have been discussing, but it takes time and is difficult.

It would be easier if you could connect your computer to the internet by means of a DSL connection using Ethernet. To see if you have an ethernet card installed, look at the connections and see if you have a socket for one. Or, you can do```
lspci
```and see if an ethernet card is listed.

---

### Post by adilza on 2009-02-25
I have just installed ubuntu 8.10 . It works great  But I couldn't install modem driver. My installed modem was Conexant HSFi 56k PCi modem..Please hel me....

---

### Post by aguilla1 on 2009-05-14
I have a similar problem with my winmodem.
I got as far as issuing the hsfconfig command and received the following in the hsfconfig-buildlog.txt file.  What is the next step to do .. or which files seem to be missing?

(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
/bin/bash: /usr/src/linux-headers-2.6.28-11-generic/scripts/gcc-x86_64-has-stack-protector.sh: No such file or directory
/bin/bash: /usr/src/linux-headers-2.6.28-11-generic/scripts/gcc-x86_64-has-stack-protector.sh: No such file or directory
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[2]: scripts/Makefile.clean: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.clean'.  Stop.
make[1]: *** [_clean_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: [clean] Error 2 (ignored)
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS= -DFOUND_OPEN_SUBSTREAM_NOFILE       -DFOUND_NO_CTL_ELEM_RW" clean)
/bin/bash: /usr/src/linux-headers-2.6.28-11-generic/scripts/gcc-x86_64-has-stack-protector.sh: No such file or directory
/bin/bash: /usr/src/linux-headers-2.6.28-11-generic/scripts/gcc-x86_64-has-stack-protector.sh: No such file or directory
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[2]: scripts/Makefile.clean: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.clean'.  Stop.
make[1]: *** [_clean_/usr/lib/hsfmodem/modules/GPL/hda] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: [clean] Error 2 (ignored)
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
/bin/bash: /usr/src/linux-headers-2.6.28-11-generic/scripts/gcc-version.sh: No such file or directory
[: 1: -lt: unexpected operator
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:9:
/usr/lib/hsfmodem/modules/GPL/oscompat.h:75:25: error: linux/types.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:85:25: error: linux/sched.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:86:24: error: linux/slab.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:87:22: error: linux/mm.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:88:29: error: linux/interrupt.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:89:24: error: linux/wait.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:90:26: error: linux/module.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:91:24: error: linux/init.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:92:26: error: linux/kernel.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:93:26: error: linux/string.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:94:26: error: linux/kdev_t.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:95:34: error: linux/byteorder/swab.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:111:28: error: linux/spinlock.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:112:24: error: linux/list.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:113:24: error: asm/bitops.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h:114:24: error: asm/system.h: No such file or directory
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:9:
/usr/lib/hsfmodem/modules/GPL/oscompat.h:134: error: field 'list' has incomplete type
/usr/lib/hsfmodem/modules/GPL/oscompat.h:192: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tqueue_lock'
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'queue_task':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:202: error: implicit declaration of function 'test_and_set_bit'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:204: error: implicit declaration of function 'spin_lock_irqsave'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:204: error: 'tqueue_lock' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/GPL/oscompat.h:204: error: (Each undeclared identifier is reported only once
/usr/lib/hsfmodem/modules/GPL/oscompat.h:204: error: for each function it appears in.)
/usr/lib/hsfmodem/modules/GPL/oscompat.h:205: error: implicit declaration of function 'list_add_tail'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:206: error: implicit declaration of function 'spin_unlock_irqrestore'
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'run_task_queue':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:218: error: implicit declaration of function 'list_empty'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:218: error: dereferencing pointer to incomplete type
/usr/lib/hsfmodem/modules/GPL/oscompat.h:219: error: storage size of 'head' isn't known
/usr/lib/hsfmodem/modules/GPL/oscompat.h:222: error: 'tqueue_lock' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/GPL/oscompat.h:223: error: implicit declaration of function 'list_add'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:224: error: implicit declaration of function 'list_del_init'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:233: error: implicit declaration of function 'list_entry'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:233: error: expected expression before 'struct'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:233: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/GPL/oscompat.h:234: error: dereferencing pointer to incomplete type
/usr/lib/hsfmodem/modules/GPL/oscompat.h:237: error: implicit declaration of function 'wmb'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:219: warning: unused variable 'head'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:255:28: error: linux/circ_buf.h: No such file or directory
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'tasklet_kill':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:401: error: 'tqueue_lock' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/GPL/oscompat.h:404: warning: assignment from incompatible pointer type
/usr/lib/hsfmodem/modules/GPL/oscompat.h:404: error: 'struct tq_struct' has no member named 'next'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:406: error: 'struct tq_struct' has no member named 'next'
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'OsModuleUseCountInc':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:435: error: implicit declaration of function 'try_module_get'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:435: error: '__this_module' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'OsModuleUseCountDec':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:444: error: implicit declaration of function 'module_put'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:444: error: '__this_module' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/GPL/oscompat.h: In function 'OsContextAllowsSleeping':
/usr/lib/hsfmodem/modules/GPL/oscompat.h:530: error: implicit declaration of function 'in_irq'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:533: error: implicit declaration of function 'in_interrupt'
/usr/lib/hsfmodem/modules/GPL/oscompat.h:537: error: implicit declaration of function 'in_softirq'
/usr/lib/hsfmodem/modules/GPL/oscompat.h: At top level:
/usr/lib/hsfmodem/modules/GPL/oscompat.h:591: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'pm_message_t'
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
/usr/lib/hsfmodem/modules/mod_engine.c:14: error: expected declaration specifiers or '...' before string constant
/usr/lib/hsfmodem/modules/mod_engine.c:14: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:14: warning: type defaults to 'int' in declaration of 'MODULE_AUTHOR'
/usr/lib/hsfmodem/modules/mod_engine.c:14: warning: function declaration isn't a prototype
/usr/lib/hsfmodem/modules/mod_engine.c:15: error: expected declaration specifiers or '...' before string constant
/usr/lib/hsfmodem/modules/mod_engine.c:15: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:15: warning: type defaults to 'int' in declaration of 'MODULE_DESCRIPTION'
/usr/lib/hsfmodem/modules/mod_engine.c:15: warning: function declaration isn't a prototype
/usr/lib/hsfmodem/modules/mod_engine.c:19: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:19: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:19: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:20: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:20: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:20: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:21: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:21: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:21: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:22: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:22: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:22: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:23: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:23: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:23: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:24: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:24: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:24: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:25: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:25: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:25: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:26: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:26: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:26: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:27: warning: data definition has no type or storage class
/usr/lib/hsfmodem/modules/mod_engine.c:27: warning: type defaults to 'int' in declaration of 'EXPORT_SYMBOL'
/usr/lib/hsfmodem/modules/mod_engine.c:27: warning: parameter names (without types) in function declaration
/usr/lib/hsfmodem/modules/mod_engine.c:30: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'cnxtengine_init'
/usr/lib/hsfmodem/modules/mod_engine.c: In function 'init_module':
/usr/lib/hsfmodem/modules/mod_engine.c:51: error: implicit declaration of function 'cnxtengine_init'
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

---

