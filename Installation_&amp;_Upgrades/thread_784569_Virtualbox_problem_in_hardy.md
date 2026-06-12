---
title: "Virtualbox problem in hardy"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Dalstal on 2008-05-06
Since I updated to Hardy i can't make VirtualBox anymore, all I get is "run 'sudo /etc/init.d/vboxdrv setup'" and it does not seem to help. What should I do?

---

### Post by Rocket2DMn on 2008-05-06
Sounds like you may need to reinstall virtualbox, but you should be able to recover the virtual machines you have already setup.  Here is the guide I followed to setting up VB in Hardy, you can probably do without most of the post-install stuff, but it walks you through the install, too - [http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)
You may want to backup your VMs first, they should be in ~/.VirtualBox/Machines
It may be prudent to remove the existing VB install from Synaptic before reinstalling VB.

---

### Post by Dalstal on 2008-05-12
I've tried removing and reinstalling virtualbox but it still doesnt work properly, while trying to start my virtual machine I get the message 
"VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}"

What should I do?

---

### Post by andrewoftheelves on 2008-05-12
yeah, i get the same thing. I even installed the virtualbox-ose-modules-generic package. when I do :
```
 dpkg -l | grep virtualbox-ose
ii  virtualbox-ose                             1.5.6-dfsg-6ubuntu1                 x86 virtualization solution - binaries
ii  virtualbox-ose-modules-2.6.24-16-generic   24                                  virtualbox-ose module for linux-image-2.6.24
ii  virtualbox-ose-modules-generic             24  
```
which proves that I have it installed, so if anyone understands this problem I would greatly appreciate help as well.

---

### Post by Rocket2DMn on 2008-05-12
Are you running a custom kernel or the generic kernel?  Did you follow the directions on that link I gave and make sure to include virtualbox-ose-modules-generic in the install command?
You can try manually adding the kernel module, I'm not sure exactly how it goes, but it should be something like
```
sudo modprobe vboxdrv
sudo depmod -a
```
I'm not in Ubuntu right now to check my configuration, but I will get back to you later today after I check.

---

### Post by RichardG891 on 2008-05-12
Had the same problem with the OSE packages in Mandriva and couldn't really resolve it - needed to have the kernel source and headers present... but still couldn't make it work. In Gutsy and Hardy, I just installed the Binary Deb package from the VirtualBox website... and works perfectly.

---

### Post by Dalstal on 2008-05-12
> **Rocket2DMn said:**
> Are you running a custom kernel or the generic kernel?  Did you follow the directions on that link I gave and make sure to include virtualbox-ose-modules-generic in the install command?
You can try manually adding the kernel module, I'm not sure exactly how it goes, but it should be something like
```
sudo modprobe vboxdrv
sudo depmod -a
```
I'm not in Ubuntu right now to check my configuration, but I will get back to you later today after I check.

no stupid as I am I missed that pert and did a regular apt-get install. I'll retry it immediately

---

### Post by Dalstal on 2008-05-12
I think it did the trick:) thanks a lot for the help

---

### Post by andrewoftheelves on 2008-05-16
hey, I know that I installed the virtualbox-ose-modules-generic package, but I think that the problem I'm having is that my computer's archetecture is x86-64, I have tried completely uninstalling, and reinstalling virtualbox. when I use the code  Rocket2DMn described in the hyperlink I get this:

```
sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-generic is already the newest version.
Suggested packages:
  bridge-utils virtualbox-ose-source
The following NEW packages will be installed:
  virtualbox-ose
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/6632kB of archives.
After this operation, 21.9MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package virtualbox-ose.
(Reading database ... 136479 files and directories currently installed.)
Unpacking virtualbox-ose [COLOR="Lime"](from .../virtualbox-ose_1.5.6-dfsg-6ubuntu1_amd64.deb) ..[/COLOR].
Setting up virtualbox-ose (1.5.6-dfsg-6ubuntu1) ...
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module [COLOR="black"][COLOR="Lime"]vboxdrv                                    
 * No suitable module for running kernel found.[/COLOR]


```
the green text is where the problem is I think, if anyone knows a solution for this I would greatly appreciate it, thanks.

---

### Post by Rocket2DMn on 2008-05-16
I had a problem like that when I reinstalled with the 386 version actually, and I think somewhere along the line a ended up with a new kernel (-386 instead of -generic).  You should remove that kernel and use the generic kernel.  Then run
```
sudo modprobe vboxdrv
sudo depmod -a
```
and you should be able to use virtualbox.

If it turns out you have a different kernel now than the generic kernel (like something-amd64 or something-i386), open Synaptic and search for "linux-image".  You can then find the one to remove, completely remove it (make sure the generic kernel still exists!), then reboot into the generic kernel.

---

### Post by andrewoftheelves on 2008-05-24
ha im trying to delete this post but its not working.

---

### Post by andrewoftheelves on 2008-05-24
hey, I tried changing kernels but to no avail. So i googled my problem and found this workaround that worked for me:```
sudo insmod /lib/modules/2.6.24-16-generic/misc/vboxdrv.ko
```
I have no idea what this code does(If anyone wants to explain I would greatly appreciate it) but thanks to everyone for their help.

---

### Post by albeano2004 on 2008-06-07
Hi,
According to this page [http://linux.about.com/od/commands/l/blcmdl8_insmod.htm]("http://linux.about.com/od/commands/l/blcmdl8_insmod.htm"), lsmod does the following
> insmod installs a loadable module in the running kernel.

insmod tries to link a module into the running kernel by resolving all symbols from the kernel's exported symbol table.

So, from that, I gather that this command loads the Virtualbox kernel module into the kernel. I would say that this problem is occurring because of a difference in the version of kernel that the module is designed for, and the latest kernel???

---

### Post by andrewoftheelves on 2008-06-07
yeah I agree with you, after the ubuntu kernel 17 came out virtualbox worked perfectally fine, and when I did that ismod code i was using the kernel 16 so that is why it was working.

---

