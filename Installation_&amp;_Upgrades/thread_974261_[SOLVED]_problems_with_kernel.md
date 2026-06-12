---
title: "[SOLVED] problems with kernel"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by johnapeterson on 2008-11-07
Hey gang,

I have a problem with the kernel after upgrading to Ubuntustudio 8.10.  Whenever I install new apps I get the following message:

Whenever I add/update something in Synaptic, I get the following messages:

E: linux-image-2.6.27-3-rt: subprocess post installation script returned error exit status 2
E: linux-restricted-image-26.27-3-tr: dependency problems-leaving unconfigured
E: linux-image-rt: dependency problems-leaving unconfigured
E: linux-restricted-modules-rt: dependency problems-leaving unconfigured
E: linux-rt: dependency problems-leaving unconfigured

I tried reinstalling the kernel but keep getting the same message.  Maybe I am trying to reinstall the kernel the wrong way.  Can anyone help me reinstall it, or tell me how to back grade to an older kernel.

Thanks,
John

---

### Post by kulus1969 on 2008-11-07
I'm having a similar problem with a Hardy update:

E: linux-image-2.6.24-21-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-21-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

Let me know if you find a solution...

Kulus

---

### Post by cdtech on 2008-11-07
Have you tried the command:
```
sudo dpkg --configure --pending
```

---

### Post by johnapeterson on 2008-11-07
I will try this when I get home tonight.  Is it something that I can do from the terminal on the desktop and then do a reboot, or do I need to do  need to boot to a command prompt and then enter it?

Thanks,
John

---

### Post by cdtech on 2008-11-07
Just "ctrl+alt+f1 from your desktop.

---

### Post by lordbjorn on 2008-11-07
I've been seeing this error too. The underlying problem seems to be update-grub crashing:

Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2

I tried looking through /usr/sbin/update-grub, but couldn't figure out which instance of the expr command is failing.

---

### Post by johnapeterson on 2008-11-07
I ran sudo dpkg --configure --pending, but get the following back:

john@john:~$ sudo dpkg --configure --pending
Setting up linux-image-2.6.27-3-rt (2.6.27-3.8) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-3-rt
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.27-3-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-3-rt:
 linux-restricted-modules-2.6.27-3-rt depends on linux-image-2.6.27-3-rt; however:
  Package linux-image-2.6.27-3-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-3-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.27-3-rt; however:
  Package linux-image-2.6.27-3-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.27-3-rt; however:
  Package linux-restricted-modules-2.6.27-3-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-3-rt
 linux-restricted-modules-2.6.27-3-rt
 linux-image-rt
 linux-restricted-modules-rt


What next?

THanks,
John

---

### Post by lordbjorn on 2008-11-07
> **johnapeterson said:**
> I ran sudo dpkg --configure --pending, but get the following back:

john@john:~$ sudo dpkg --configure --pending
Setting up linux-image-2.6.27-3-rt (2.6.27-3.8) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-3-rt
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'


I would try reinstalling grub ("sudo apt-get reinstall grub"), and see if that fixes it. it should give you the script that it wants.

---

### Post by johnapeterson on 2008-11-07
I get the follow:

john@john:~$ sudo apt-get reinstall grub
E: Invalid operation reinstall
john@john:~$ 

Am I missing something?

Thanks

---

### Post by cdtech on 2008-11-07
Try:
sudo apt-get install --reinstall packagename

---

### Post by johnapeterson on 2008-11-07
No luck.  This is what I am getting after I type the command:

john@john:~$ sudo apt-get install --reinstall linux-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-177-kernel-source dkms cpp-4.2 libscrollkeeper0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.27-3-rt (2.6.27-3.8) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-3-rt
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.27-3-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-3-rt:
 linux-restricted-modules-2.6.27-3-rt depends on linux-image-2.6.27-3-rt; however:
  Package linux-image-2.6.27-3-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-3-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.27-3-rt; however:
  Package linux-image-2.6.27-3-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.27-3-rt; however:
  Package linux-restricted-modules-2.6.27-3-rt is not configured yet.
dpkg: error prNo apport report written because the error message indicates its a followup error from a previous failure.
                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                ocessing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.27.3.4); however:
  Package linux-image-rt is not configured yet.
 linux-rt depends on linux-restricted-modules-rt (= 2.6.27.3.4); however:
  Package linux-restricted-modules-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.27-3-rt
 linux-restricted-modules-2.6.27-3-rt
 linux-image-rt
 linux-restricted-modules-rt
 linux-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john:~$ 


Thanks for any help
John

---

### Post by johnapeterson on 2008-11-08
Here are some new things I tried:
Removing Linux-rt kernel- No Luck

Install the 2.6.27-8.17 generic kernel  - I get back the message from Synaptic "linux-image-2.6.27-8-generic 2.6.27-8.17 " failed to install or upgrade.

I noticed that when I go to the grub boot screen when booting up, Ithe only kernels listed are 8.04 nothing newer.  The top kernel is "ubuntu 8.04 kernel 2.6.24.21-rt".  If I select the recovery version below it, I get to a screen with a different wallpaper then I set, the banner at the top that you can select apps, and nothing else.  The cursor does not move.

Any of the remaining kernel is the boot list opon select just give back the message "error 15" and I can get back to tthe list to select a different kernel.

Appreciate any help,
John

---

### Post by johnapeterson on 2008-11-10
I did a fresh install, and everything is working ok now.

Thanks,
John

---

### Post by kulus1969 on 2008-12-09
I also had to reinstall to fix this problem...

Kulus

---

