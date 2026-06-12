---
title: "Virtual Box"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by qbox on 2008-06-09
Ok I read a lot texts how to fix this bug but nothing worked for me.


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Everything worked fine until I make some update. After that I see this bug. I read a lot topics how to fix this bug, but nothing worked for me. Can someone give me one step by step how to make this to work?
Thank you.

---

### Post by qbox on 2008-06-12
I try this
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/237278/comments/12](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/237278/comments/12)

I follow all the steps.
sudo module-assistant a-i virtualbox-ose
in the log file show me alot warnings and errors.
I choose to continue.
After that I run this
qbox@qbox:~$ sudo /etc/init.d/vboxdrv restart
* Stopping VirtualBox kernel module vboxdrv [ OK ]
* Starting VirtualBox kernel module vboxdrv
* No suitable module for running kernel found.
qbox@qbox:~$

Please any one to give me a some solution.
Thanks

---

### Post by qbox on 2008-06-12
qbox@qbox:~/Desktop$ sudo dpkg -i virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb
(Reading database ... 170625 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb) ...
dpkg: error processing virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb (--install):
 trying to overwrite `/lib/modules/2.6.24-16-rt/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-16-rt
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 virtualbox_1.6.2-31466_Ubuntu_hardy_amd64.deb
qbox@qbox:~/Desktop$

---

### Post by wolfen69 on 2008-06-12
why not remove what you have and reinstall from [HERE]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") 1 click install.

---

### Post by qbox on 2008-06-12
I look for files to remove but files not exist.
That link didn't work for me. I receive upper error.

---

### Post by Vadi on 2008-06-12
Try installing this ([click]("apt:virtualbox-ose-modules-2.6.24-18-generic")). Reboot, and see if virtualbox works now.

---

### Post by qbox on 2008-06-12
sqbox@qbox:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-18-generic
[sudo] password for qbox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose-modules-2.6.24-18-generic
qbox@qbox:~$

---

### Post by Vadi on 2008-06-12
That's strange, I have that package here.

Maybe you aren't on 8.04 or didn't enable universe or something like that? Search in synaptic for something related to a virtualbox module.

---

### Post by qbox on 2008-06-14
Im on 8.04

qbox@qbox:~$ uname -a
Linux qbox 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
qbox@qbox:~$ 

In synaptic I enable all packages after that disable one by one, nothing help. Can someone give me a solution which will work?
Thx.

---

### Post by Vadi on 2008-06-14
Just uninstall this virtualbox and install the one from their website would work.

---

### Post by qbox on 2008-06-14
in System -> Administration -> Software Sources I choose MainServer.
I make update and I receive message that there is new updates.
In the list was 128 packets, and between was virtuelbox-ose-modules-generic (i didnt spell corectly). I was wondering why until now I didnt receive updates for virtuel box from prevision server, I receive this updates until I switch to MainServer. I said ok I will make update. After update I restart the computer. First thing I notice was that I dont have SOUND. I put the user for virtualbox in UserManager, I logout and login again. The virtual box worked great. I reboot the computer to see if everything is alright, and maybe the sound will be fixed by himself.
So I make reboot. The computer didnt turn on again. I try couple times, but after bios check computer reboot recently. After 5-6 times, I see command line for terminal login. I didnt be able to switch to graphic mode. I was on the end of madnes. I take Ubuntu 8.04 CD and reinstall the system.Now I have new installation, and I cant run again VirtualBox.
I choose mainserver again, but I cant update virtualbox-ose-modules.
Can someone tell me what to do???

---

### Post by qbox on 2008-06-14
FINALY I Make it to work...
:guitar:

---

### Post by rarsa on 2008-11-18
How did you make it work?

I have the same sound issue. The only way for me to fix the sound is to restore the kernel as it was before installing the vbox modules.

---

