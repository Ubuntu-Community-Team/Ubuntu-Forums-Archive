---
title: "kernel .31-12"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by darco on 2009-10-06
Just updated to kernel .31-12 today. On reboot, Grub2 menu flashes when I pick an entry (is that new?). Chose the new kernel and it went bonkers, everything is flashing. Dropped me to text mode. Couldnt log in because the keyboard was acting up and not accepting my password....I figured the nvidia modules werent rebuilt which is why I got a text log in. 
Since I couldnt log in to Karmic, I went back to the previous kernel, installed the script by sdennie to automate nvidia module rebuilds after a kernel update, reinstalled the .31-12 kernel and I am back in.....

Also I did notice that Grub2 picked up my grub entries that are on a separate hdd. Now grub2 for karmic has about 12 or so entries. 
I dont mind but I actually wanted Grub2 on the other hdd to see karmic. I will have to work on that later.


darco

---

### Post by Regenweald on 2009-10-06
Smooth as silk here. Rebooted fine, just -12 and -11 in my grub list. Also found XP as it has been doing for all of the grub2 releases.

---

### Post by cor2y on 2009-10-06
I too am running into this problem.I dont know what the cause could be.
I had to use the previous kernel to be able to login since the blinking/jumping screen and slow response keyboard makes it impossible to login in .31-12

---

### Post by khughitt on 2009-10-07
Same problem here since 2.6.31-11. When attempting to load either 31-11 or 31-12, the following are displayed:

```

nvidia (185.18.36)...
...fail!
vboxdrv (...)
...fail!
etc

```

Then a login prompt is displayed, however, the screen is continually flashing, and input only seems to work sporadically (if you press "d" ten time quickly, it might show up three times).

So it looks like for some reason the modules aren't being rebuilt. Anyone know how to fix this? You mention a script to automatically build the nvidia modules, however, from the error messages I got, it looks like Virtualbox modules are affected as well.

I'm going to check on Launchpad for a bug report.

Any help would be greatly appreciated.

Thanks!

---

### Post by khughitt on 2009-10-07
Just found another similar thread:

[http://ubuntuforums.org/showthread.php?t=1271508](http://ubuntuforums.org/showthread.php?t=1271508)

Looks like a number of people are having the same problem.

---

### Post by khughitt on 2009-10-07
Fixed it :)

A helpful clue that popped up during a recent update tipped me off:

```

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-12-generic-pae                                                                                      
 *  nvidia (185.18.36)...                                                       nvidia (185.18.36): Installing module.
  Kernel headers for 2.6.31-12-generic-pae are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-12-generic-pae or equivalent.
                                                                         [fail]
 *  vboxdrv (3.0.6)...                                                          vboxdrv (3.0.6): Installing module.
  Kernel headers for 2.6.31-12-generic-pae are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-12-generic-pae or equivalent.
                                                                         [fail]
 *  vboxnetadp (3.0.6)...                                                       vboxnetadp (3.0.6): Installing module.
  Kernel headers for 2.6.31-12-generic-pae are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-12-generic-pae or equivalent.
                                                                         [fail]
 *  vboxnetflt (3.0.6)...                                                       vboxnetflt (3.0.6): Installing module.
  Kernel headers for 2.6.31-12-generic-pae are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-12-generic-pae or equivalent.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```

So I checked and sure enough the header files had not been installed. Installing the suggested package went smoothly:

```

sudo aptitude install linux-headers-2.6.31-12-generic-pae
[sudo] password for hughitt1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-headers-2.6.31-12-generic-pae 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 668kB of archives. After unpacking 8,778kB will be used.
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com karmic/main linux-headers-2.6.31-12-generic-pae 2.6.31-12.40 [668kB]
Fetched 668kB in 5s (122kB/s)                               
Selecting previously deselected package linux-headers-2.6.31-12-generic-pae.
(Reading database ... 206793 files and directories currently installed.)
Unpacking linux-headers-2.6.31-12-generic-pae (from .../linux-headers-2.6.31-12-generic-pae_2.6.31-12.40_i386.deb) ...
Setting up linux-headers-2.6.31-12-generic-pae (2.6.31-12.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-12-generic-pae                                                                     
 *  nvidia (185.18.36)...                                                                                                                      nvidia (185.18.36): Installing module.
............
......
                                                                                                                                        [ OK ]
 *  vboxdrv (3.0.6)...                                                                                                                         vboxdrv (3.0.6): Installing module.
............
......
                                                                                                                                        [ OK ]
 *  vboxnetadp (3.0.6)...                                                                                                                      vboxnetadp (3.0.6): Installing module.
...........
......
                                                                                                                                        [ OK ]
 *  vboxnetflt (3.0.6)...                                                                                                                     vboxnetflt (3.0.6): Installing module.
...........
......
                                                                                                                                        [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

After rebooting, I selected the previously unusable 2.6.31-12 kernel, and it worked perfectly :)

I searched through the launchpad bug reports some, but did not see any specifically related to the above.

Anyone know if one already exists? If not, should it be filed with dpkg, aptitude, or something else?

---

### Post by cor2y on 2009-10-07
Unfortunately i have no linux-headers-2.6.31-12-generic-pae
```
sudo aptitude install linux-headers-2.6.31-12-generic-pae
[sudo] password for cor2y: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for linux-headers-2.6.31-12-generic-pae
No candidate version found for linux-headers-2.6.31-12-generic-pae
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

Regular linux-headers-2.6.31-12-generic is already installed.

---

### Post by sports fan Matt on 2009-10-07
I'll see if this is an issue for me as well.  Im still loading the updates :)

---

### Post by sports fan Matt on 2009-10-07
no issues here

---

### Post by khughitt on 2009-10-07
> Regular linux-headers-2.6.31-12-generic is already installed.

What do kernel version are you currently using? (e.g. "uname -a") Are you using the NVIDIA drivers?

---

### Post by cor2y on 2009-10-08
Since i cant login to  31.12 kernet although it shows installed via synaptic.
at present i have to boot into 31.12
```
uname -a
Linux homeserver 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64 GNU/Linux
```
Nvidia driver installed is 190.36 beta x86_64bit version

---

### Post by tad1073 on 2009-10-09
> **cor2y said:**
> Since i cant login to  31.12 kernet although it shows installed via synaptic.
at present i have to boot into 31.12
```
uname -a
Linux homeserver 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64 GNU/Linux
```Nvidia driver installed is 190.36 beta x86_64bit version

You probably need to remover the 190.36 drive and revert back to 185.18.36

---

### Post by khughitt on 2009-10-13
Hmm. Same thing happened after .31-13 kernel was installed. For some reason the headers aren't being installed.

---

### Post by khughitt on 2009-10-13
Okay, I just did a search using aptitude, and found that there is the version-less package for my specific kernel headers is not installed:

```

$ aptitude search linux | grep pae
i   linux-generic-pae               - Complete Generic Linux kernel             
p   linux-headers-generic-pae       - Generic Linux kernel headers              
i   linux-image-generic-pae         - Generic Linux kernel image                

```

I'm wondering if perhaps that is why the headers are not being automatically installed each time the kernel is upgraded. I have installed the package, so I should find out when 2.6.31-14 comes out.

In the meantime, is anyone else still running into this problem? If so, it might be worth while to report the issue on Launchpad.

---

