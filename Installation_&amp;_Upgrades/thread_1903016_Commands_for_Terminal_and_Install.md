---
title: "Commands for Terminal and Install"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by UltimateCat on 2012-01-01
I have this driver in a folder on my Ubuntu-Gnome desktop unpacked.  I also have this driver in a zip folder still packed.  I was not able to get past this first command.
 I am manually attempting to follow the instructions for this driver because I have not been able to get my Ubuntu: Ultimate Ed 2.7 online.  Only my Windows Xp is online when the NIC isn't kicking me off the internet.   
 Should I put this folder somewhere else in my Ubuntu for the commands to work in the terminal?
 

 What does this result from the terminal mean?
 

 cat@username:~$ sudo tar vjxf r8168-8.aaa.bb.tar.bz2  
 [sudo] password for cat:  
 tar: r8168-8.aaa.bb.tar.bz2: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
 tar: Child returned status 2  
 tar: Exiting with failure status due to previous errors  
 

 These are the instructions I am following and I have 2.6.32 – 25 Version of the kernel
 

 	This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.
 

 <Requirements>
 

 	- Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
 	- For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
 	- Compiler/binutils for kernel compilation
 

 <Quick install with proper kernel settings>
 	Unpack the tarball :
 		# tar vjxf r8168-8.aaa.bb.tar.bz2
 

 	Change to the directory:
 		# cd r8168-8.aaa.bb
 

 	If you are running the target kernel, then you should be able to do :
 

 		# ./autorun.sh	(as root or with sudo)
 

 	You can check whether the driver is loaded by using following commands.
 

 		# lsmod | grep r8168
 		# ifconfig -a
 

 	If there is a device name, ethX, shown on the monitor, the linux  
 	driver is loaded. Then, you can use the following command to activate  
 	the ethX.
 

 		# ifconfig ethX up
 

 		,where X=0,1,2,...


Any help is appreciated my head is spinning and I've been trying my hand at this for a long time now.  Thanks in advance;)

---

### Post by 73ckn797 on 2012-01-01
> **UltimateCat said:**
> I have this driver in a folder on my Ubuntu-Gnome desktop unpacked.  I also have this driver in a zip folder still packed.  I was not able to get past this first command.
 

 cat@username:~$ sudo tar vjxf r8168-8.aaa.bb.tar.bz2  
 [sudo] password for cat:  
 tar: r8168-8.aaa.bb.tar.bz2: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
 tar: Child returned status 2  
 tar: Exiting with failure status due to previous errors  

It appears you need to ```
cd /home/username/Desktop/foldername
``` first. You have not told terminal where it is.

---

### Post by oldos2er on 2012-01-01
> **UltimateCat said:**
>  What does this result from the terminal mean?
 

 cat@username:~$ sudo tar vjxf r8168-8.aaa.bb.tar.bz2  
 [sudo] password for cat:  
 tar: r8168-8.aaa.bb.tar.bz2: Cannot open: No such file or directory  
 tar: Error is not recoverable: exiting now  
 tar: Child returned status 2  
 tar: Exiting with failure status due to previous errors  
 

Don't use 'sudo' to untar the archive.

You need to run the tar command from within the same folder where the tar file is, for example if r8168-8.aaa.bb.tar.bz2 is in your Downloads folder, you'd run ```
cd Downloads

tar vjxf r8168-8.aaa.bb.tar.bz2
```

---

### Post by UltimateCat on 2012-01-01
> **oldos2er said:**
> Don't use 'sudo' to untar the archive.

You need to run the tar command from within the same folder where the tar file is, for example if r8168-8.aaa.bb.tar.bz2 is in your Downloads folder, you'd run ```
cd Downloads

tar vjxf r8168-8.aaa.bb.tar.bz2
```

Thank you ! I get it now:D

---

### Post by UltimateCat on 2012-01-01
> **73ckn797 said:**
> It appears you need to ```
cd /home/username/Desktop/foldername
``` first. You have not told terminal where it is.
I thought I understood.....boy was I wrong.  The results from my terminal are:
 

 cat@username:~$ cd/home/cat/Desktop/r8168-8.027.00  
 bash: cd/home/cat/Desktop/r8168-8.027.00: No such file or directory  
 cat@username:~$ cd/home/cat@ztcat/Desktop/r8168-8.027.00  
 bash: cd/home/cat@ztcat/Desktop/r8168-8.027.00: No such file or directory  
 cat@username:~$ apt-get cd/home/cat@ztcat/Desktop/r8168-8.027.00  
 E: Invalid operation cd/home/cat@ztcat/Desktop/r8168-8.027.00  
 cat@username:~$ home/cat@ztcat/Desktop/r8168-8.027.00  
 bash: home/cat@ztcat/Desktop/r8168-8.027.00: No such file or directory  
 cat@username:~$ apt-get home/cat@ztcat/Desktop/r8168-8.027.00 tar vjxf r8168-8.aaa.bb.tar.bz2 
 E: Invalid operation home/cat@ztcat/Desktop/r8168-8.027.00  
 cat@username:~$  
 
I'm trying so hard but it doesn't seem to be going so well:confused:and ready to cry-

---

### Post by oldos2er on 2012-01-01
You need to leave a space between "cd" and "/home/cat/Desktop/r8168-8.027.00": ```
cd /home/cat/Desktop/r8168-8.027.00
```

Not sure why you're putting "apt-get" in there; it's not going to function.

Edit: Also, your home folder is "cat", not "cat@ztcat".

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by UltimateCat on 2012-01-04
> **oldos2er said:**
> You need to leave a space between "cd" and "/home/cat/Desktop/r8168-8.027.00": ```
cd /home/cat/Desktop/r8168-8.027.00
```Not sure why you're putting "apt-get" in there; it's not going to function.

Edit: Also, your home folder is "cat", not "cat@ztcat".

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
I used the commands that a member specifically advised me to and hit enter after each command. T am not sure if the driver is installed or not.  I'm still learning.
I used these commands:

 cd /home/cat/Desktop tar -xvjf r8168-8.027.00.tar.bz2
 cd r8168-8.027.00 sudo ./autorun.sh
cat@ztcat:~$ cd /home/cat/Desktop 
 cat@ztcat:~/Desktop$ tar -xvjf r8168-8.027.00.tar.bz2  tar: 
Record size = 8 blocks  r8168-8.027.00/  r8168-8.027.00/Makefile  r8168-8.027.00/src/
 r8168-8.027.00/src/rtl_eeprom.h
 r8168-8.027.00/src/r8168_asf.h  r8168-8.027.00/src/rtltool.h  r8168-8.027.00/src/r8168_asf.c  r8168-8.027.00/src/r8168_n.c  r8168-8.027.00/src/rtl_eeprom.c  r8168-8.027.00/src/rtltool.c  r8168-8.027.00/src/Makefile  r8168-8.027.00/src/r8168.h  r8168-8.027.00/src/Makefile_linux24x  r8168-8.027.00/README  r8168-8.027.00/autorun.sh
 cat@ztcat:~/Desktop$ cd r8168-8.027.00  cat@ztcat:~/Desktop/r8168-8.027.00$ sudo ./autorun.sh  [sudo] password for cat:   Check old driver and unload it.  rmmod r8169  Build the module and install  Backup r8169.ko  rename r8169.ko to r8169.bak  DEPMOD 2.6.32-25-generic  load module r8168  Updating initramfs. Please wait.  update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic  Completed.
 cat@ztcat:~/Desktop/r8168-8.027.00$   cat@ztcat:~/Desktop/r8168-8.027.00$ lsmod | grep r8168  r8168                 190975  0
 cat@ztcat:~/Desktop/r8168-8.027.00$ ifconfig -a  eth0      Link encap:Ethernet  HWaddr 00:21:85:66:7a:d1             UP BROADCAST MULTICAST  MTU:1500  Metric:1            RX packets:0 errors:0 dropped:0 overruns:0 frame:0            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)            Interrupt:26
 lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0            inet6 addr: ::1/128 Scope:Host            UP LOOPBACK RUNNING  MTU:16436  Metric:1            RX packets:1384 errors:0 dropped:0 overruns:0 frame:0            TX packets:1384 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:0            RX bytes:109888 (109.8 KB)  TX bytes:109888 (109.8 KB) 
  wlan0     Link encap:Ethernet  HWaddr 00:23:69:d7:3f:0f             UP BROADCAST MULTICAST  MTU:1500  Metric:1            RX packets:0 errors:0 dropped:0 overruns:0 frame:0            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000
Not sure why Open Office made such a mess of these results. You?

---

### Post by oldos2er on 2012-01-04
> **UltimateCat said:**
> Not sure why Open Office made such a mess of these results. You?

You can copy and paste directly from the terminal to a post here, no need for OpenOffice.

It looks like your connection is working now, judging by the output from 'ifconfig', but networking is not my specialty.

---

### Post by UltimateCat on 2012-01-06
> **oldos2er said:**
> You can copy and paste directly from the terminal to a post here, no need for OpenOffice.

It looks like your connection is working now, judging by the output from 'ifconfig', but networking is not my specialty.
The Driver is installed....I am so happy!:D
And I found the inf file to install in the morning:D
So happy that the 6 weeks of hardship is over.
Best wishes for a new year
Thank You

---

### Post by oldos2er on 2012-01-07
Glad you got it working!

---

