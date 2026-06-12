---
title: "Kernel will not upgrade"
date: 2017-04-25
forum: Installation &amp; Upgrades
---

### Post by sappho+ on 2017-04-25
It seems that /boot partition is full. 

ls /boot/ gives me this:
 ```
abi-4.4.0-70-generic         initrd.img-4.4.0-72-generic
 abi-4.4.0-72-generic         lost+found
 config-4.4.0-70-generic      memtest86+.bin
 config-4.4.0-72-generic      memtest86+.elf
 grub                         memtest86+_multiboot.bin
 initrd.img-4.4.0-47-generic  System.map-4.4.0-70-generic
 initrd.img-4.4.0-63-generic  System.map-4.4.0-72-generic
 initrd.img-4.4.0-64-generic  vmlinuz-4.4.0-70-generic
 initrd.img-4.4.0-70-generic  vmlinuz-4.4.0-72-generic
```

When I sudo apt-get purge linux-image-4.4.0-47 or 63, I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-4.4.0-47-lowlatency' for regex 'linux-image-4.4.0-47'
Note, selecting 'linux-image-4.4.0-47-generic' for regex 'linux-image-4.4.0-47'
Package 'linux-image-4.4.0-47-generic' is not installed, so not removed
Package 'linux-image-4.4.0-47-lowlatency' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 16 not to upgrade.
```

Same for 63. 

dpkg --list | grep linux-image gives me this:
 ```
rc  linux-image-3.19.0-64-generic                        3.19.0-64.72                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP

 rc  linux-image-4.4.0-59-generic                         4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 rc  linux-image-4.4.0-66-generic                         4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 ii  linux-image-4.4.0-70-generic                         4.4.0-70.91                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 ii  linux-image-4.4.0-72-generic                         4.4.0-72.93                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 rc  linux-image-extra-3.19.0-64-generic                  3.19.0-64.72                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP

 rc  linux-image-extra-4.4.0-59-generic                   4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 rc  linux-image-extra-4.4.0-63-generic                   4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 rc  linux-image-extra-4.4.0-64-generic                   4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 rc  linux-image-extra-4.4.0-66-generic                   4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 ii  linux-image-extra-4.4.0-70-generic                   4.4.0-70.91                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 ii  linux-image-extra-4.4.0-72-generic                   4.4.0-72.93                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

 ii  linux-image-generic                                  4.4.0.72.78                                   amd64        Generic Linux kernel image
```

Is there anything else I should list to help solve this?

---

### Post by Xian on 2017-04-26
Is there output of "No space left on device" message if you do:

$ sudo apt-get -f install

If so then try:

$ sudo apt-get autoremove

---

### Post by Bashing-om on 2017-04-26
sappho+; Hello;

Current is :
> 
sysop@x1604:~$ uname -r
4.4.0-75-generic
sysop@x1604:~$

All that is (i)nstalled is the -70 and -72 kernels - as should be IF you have not updated the system !
the field 'rc'
> 
rc  linux-image-4.4.0-59-generic 

means (R)emoved but (c)onfig files remain . this is a normal state and will not effect the overall performance of your system.
so, to learn and see what the "state" is; in terminal :
```

dpkg -l linux-image-generic

```
the legend here indicates what each of the 4 positions in the field represent.

So, ya want it to be squeaky clean - removIng those obsolete config files ?
 Is your system stable and consistent in all respects ? then ->

 While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

Is this the resolution to your state of affairs ? OR
do we need to focus on getting the -75 kernel installed ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sappho+ on 2017-04-30
No, I get this message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ian-weisser on 2017-04-30
You have already done due diligence to determine if the 4.4.0-57, -63, and -64 kernels are installed - they are clearly not.

Apt cannot do any more.
Go ahead and use rm to remove initrd.img-4.4.0-47-generic, initrd.img-4.4.0-63-generic, and initrd.img-4.4.0-64-generic

---

