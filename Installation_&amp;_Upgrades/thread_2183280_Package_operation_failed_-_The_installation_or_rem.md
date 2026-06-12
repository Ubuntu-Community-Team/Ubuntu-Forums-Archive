---
title: "Package operation failed - The installation or removal of a software package failed."
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Peter_Rudo on 2013-10-24
I autoupdated ubuntu, but am getting this error:


installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 467153 files and directories currently installed.)
Unpacking linux-headers-3.2.0-55 (from .../linux-headers-3.2.0-55_3.2.0-55.85_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-55_3.2.0-55.85_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-55/arch/m68k/include/asm/nettel.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-55/arch/m68k/include/asm/nettel.h'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-55-generic-pae (from .../linux-headers-3.2.0-55-generic-pae_3.2.0-55.85_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-55-generic-pae_3.2.0-55.85_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-55-generic-pae/include/config/pnp/debug/messages.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-55-generic-pae/include/config/pnp/debug/messages.h'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-generic-pae.
Unpacking linux-headers-generic-pae (from .../linux-headers-generic-pae_3.2.0.55.65_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-55_3.2.0-55.85_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-55-generic-pae_3.2.0-55.85_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-55-generic-pae; however:
  Package linux-headers-3.2.0-55-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.55.65); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae

---

### Post by ian-weisser on 2013-10-24
> **Peter_Rudo said:**
> 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-55_3.2.0-55.85_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-55/arch/m68k/include/asm/nettel.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-55/arch/m68k/include/asm/nettel.h'): [COLOR=#ff0000]**No space left on device**[/COLOR]


Your disk (or /boot partition) is full.
Do you need help freeing up space?

---

### Post by Peter_Rudo on 2013-10-24
yes please... i am really noob in ubuntu

---

### Post by Peter_Rudo on 2013-10-24
just to make it clear - i use ubuntu in VirtuaBox. I googled how to get free space so i put this in terminal:
df -h
[U]
[B]result is:
[/B][/U]
marek@UbuntuVBOX:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.4G  5.7G  1.5G  80% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  760K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M  124K  501M   1% /run/shm
/dev/sr0         57M   57M     0 100% /media/VBOXADDITIONS_4.2.18_88780
marek@UbuntuVBOX:~$

Doesnt it mean I have enough space?

---

### Post by ian-weisser on 2013-10-24
If you really had enough free space, you wouldn't get a "no free space left" error.
Open a terminal, and try the following command. Post the results here, and please use  tags to make the output readable.
```
dpkg -l | grep '^ii' | grep linux-image
```
It will tell us how many kernels you have installed, and their names. The easy way to free up space is to delete old, unused kernels. Keep at least one old working kernel (in case an upgrade fails) until the upgrade is successful and thoroughly tested.

---

### Post by Peter_Rudo on 2013-10-24
OK, so here is the result.. btw did i put tags correctly?

> marek@UbuntuVBOX:~$ dpkg -l | grep '^ii' | grep linux-image
ii  linux-image-3.2.0-23-generic-pae       3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic-pae       3.2.0-27.43                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae       3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic-pae       3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae       3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae       3.2.0-40.64                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic-pae       3.2.0-41.66                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae       3.2.0-43.68                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae       3.2.0-48.74                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae       3.2.0-49.75                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae       3.2.0-51.77                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae       3.2.0-53.81                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae       3.2.0-54.82                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae       3.2.0-55.85                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.55.65                             Generic Linux kernel image
marek@UbuntuVBOX:~$ 


---

### Post by ian-weisser on 2013-10-24
Looks like you can get rid of 12 (or so) of those older kernels.
*Do NOT* delete the kernel you are currently using.

Great instructions on how to do so are at [http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)
Pick the method that you are most comfortable with.

After deleting a few older kernels, your new kernel should install without problem.

---

### Post by Peter_Rudo on 2013-10-25
and how do i know which kernel i am using?

---

### Post by Peter_Rudo on 2013-10-25
Well I tried 3 ways described in your link and Im getting an error before finishing each of them correctly.

[U]**Synaptic**
[/U]> marek@UbuntuVBOX:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-55-generic-pae but it is not going to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marek@UbuntuVBOX:~$ 


[U]**Ubuntu-tweak**
[/U]> marek@UbuntuVBOX:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-55-generic-pae but it is not going to be installed
 ubuntu-tweak : Depends: python-lxml but it is not going to be installed
                Depends: python-compizconfig but it is not going to be installed
                Depends: gir1.2-gconf-2.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marek@UbuntuVBOX:~$ 


[U]**user penreturn**
[/U]> marek@UbuntuVBOX:~$ sudo apt-get purge linux-image-3.2.0-23-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-55-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marek@UbuntuVBOX:~$ 


---

### Post by varunendra on 2013-10-25
Hope ian won't mind while I fill in for him.

> **Peter_Rudo said:**
> and how do i know which kernel i am using?
By following command in terminal (apart from many other ways)-
```
uname -r
```

For example, if you are using kernel linux-image-3.2.0-54-generic-pae, then the output of the above will be -
```
linux-image-3.2.0-54-generic-pae
```

..then, to remove the older kernels that you have, you may use this command -
```
sudo apt-get purge linux-image-3.2.0-{23,27,37,38,39,40,41,43,48,49,51}-generic-pae
```
Which will remove the kernels 3.2.0-23 to 3.2.0-53 in one go. Needless to say - **Be Careful** not to remove the current kernel ! It is recommended to keep at least one previous kernel, that's why I didn't include "54" in above example. :)

**PS:**
ian meant to use the '**Code**' tags, not the 'Quote' tags you are using. It makes a lot of difference. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by Peter_Rudo on 2013-10-25
So i tried this:
```
marek@UbuntuVBOX:~$ sudo apt-get purge linux-image-3.2.0-{23,27,37,38,39,40,41,43,48,49,51}-generic-pae

```

and the result is:
```
[sudo] password for marek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-55-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
marek@UbuntuVBOX:~$ 

```

---

### Post by varunendra on 2013-10-25
> **Peter_Rudo said:**
> ```
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-55-generic-pae but it is not going to be installed

```

Hmm.. it is the same package that was interrupted during installation. The "apt-get -f install" or "dpkg configure -a" options should fix it, but they won't succeed until you have enough space on the partition.

So, do you have other partitions in the virtual machines where we can temporary move some files to get sufficient space? Since it is just a virtual machine, you can add a virtual hard disk anytime you wish. That should be much easy and probably most straight forward solution (apart from some 'dirty' ones, which would be more straight forward :P).

---

### Post by ian-weisser on 2013-10-25
I was about to write about how linux-headers-generic-pae is a metapackage that refers to the current kernel, and can be safely removed and reinstalled without compromising the system.  I was also about to write about how since apt-get is stuck by device-is-full, a dpkg method is on the AskUbuntu page, and to use that initially to free up space to get apt-get working.

But I like varunendra's method better for users who don't want do a lot of mucking about with dpkg.

---

### Post by Peter_Rudo on 2013-10-25
doesn't this mean I have enough space?
[IMG]http://imageshack.us/photo/my-images/834/acka.png/[/IMG]

---

### Post by ian-weisser on 2013-10-25
Do I think that 20% (according to df) should be enough space? Yes, on many systems it seems to be plenty of space. 
In this case, apt disagrees. 

Do you want to investigate why? 
Or do you just want to get it working again?

---

### Post by Peter_Rudo on 2013-10-25
i want to get it working, just wanted to let you know... btw did you see the picture? because I inserted the link, but now i cant see

---

### Post by ian-weisser on 2013-10-25
No link, no picture.

---

### Post by Peter_Rudo on 2013-10-25
OK, anyway, I managed to solve it thanks to you guys.
To increase the size of the drive I used this how-to:

[http://logicmason.com/2012/growing-a-hard-drive-partition-in-a-virtualbox-ubuntu-guest/](http://logicmason.com/2012/growing-a-hard-drive-partition-in-a-virtualbox-ubuntu-guest/)

to make it short - 
1. download Gparted
2. insert is as cd in VirtualBox
3. boot from Gparted
4. resize partition
5. reboot

---

