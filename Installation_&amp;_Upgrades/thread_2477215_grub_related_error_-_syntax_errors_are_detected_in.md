---
title: "grub related error - syntax errors are detected in generated GRUB config file."
date: 2022-07-18
forum: Installation &amp; Upgrades
---

### Post by gatsbybom on 2022-07-18
hello guys, can you help me solving this issue since i can't install any packages using apt

when typing : **sudo apt upgrade**

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-image-unsigned-5.15.0-41-generic : Depends: linux-modules-5.15.0-41-generic but it is not going to be installed
E: Broken packages

```

----------------


when typing : **sudo apt -f install**

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-unsigned-5.15.0-41-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 11.4 MB disk space will be freed.
Do you want to continue? [Y/n] 
dpkg: warning: files list file for package 'linux-image-5.15.0-25-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-5.15.0-40-generic' missing; assuming package has no files currently installed
(Reading database ... 198014 files and directories currently installed.)
Removing linux-image-unsigned-5.15.0-41-generic (5.15.0-41.44) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-41-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-unsigned-5.15.0-41-generic (--remove):
 installed linux-image-unsigned-5.15.0-41-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-unsigned-5.15.0-41-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by grahammechanical on 2022-07-18
What version of Ubuntu are you using? I am using Ubuntu 20.04 and it recently updated to Linux 5.15.0-41-generic. It is the same kernel that you are having problems with. What kernel are you running?

```
uname -a
```

Please run

```
sudo update-grub
```

and post the output

Regards

---

### Post by Impavidus on 2022-07-18
Could you also show the output of```
cat /etc/default/grub
ls -l /etc/grub.d
```
Something's wrong with the way update-grub works.

---

### Post by gatsbybom on 2022-07-18
thanks for reply,

i am using ubuntu 22.04

**uname -a**

>> Linux Gatsby-HP 5.15.0-40-generic #43-Ubuntu SMP Wed Jun 15 12:54:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux




**sudo update-grub**

>> Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

---

### Post by gatsbybom on 2022-07-18
[B]cat /etc/default/grub


[/B]```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```[B]


ls -l /etc/grub.d[/B]

```

ls: cannot access '/etc/grub.d': No such file or directory

```

---

### Post by ubfan1 on 2022-07-18
/etc/grub.d is from the grub-common package, and is a part of a normal system install.   You can try a sudo dpkg --reconfigure grub-common or reinstall the package with sudo apt install grub-common.   But who knows what else is missing...  Was the system install interrupted?

---

### Post by deadflowr on 2022-07-18
[s]/etc/grub.d is folder so try
```
ls -l /etc/grub.d/*
```[/s]

Might also post the contents of the /boot/grub/grub.cfg.new file.
I'd recommend posting that at a pastebin site such as paste.ubuntu.com.

(I recommend a paste site because the file may be too big for the forums to handle.)

EDIT: nevermind, I realized after re-reading i just posted the same command you tried already; more or less.

But the second part might be helpful.

---

### Post by gatsbybom on 2022-07-18
TL;DR, after installing ubuntu 22.04, i had an issue when the device was start booting , it wasn't able to identify any bootable device and continue reloading and i had to select the boot loader file path manually. then the issue solved after playing in UEFI and legacy options in BIOS xD. and it worked fine for almost a month, and then i am facing this grub related error and i have tried many solutions but none worked tho :"(


**sudo dpkg --configure grub-common**

```

dpkg: error processing package grub-common (--configure):
 package grub-common is already installed and configured
Errors were encountered while processing:
 grub-common


```


**sudo apt install grub-commmon**

```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package grub-commmon

```

---

### Post by gatsbybom on 2022-07-18
content for /boot/grub/grub.cfg.new :

```


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


```


content for /boot/grub/grub.cfg :

[https://pastebin.ubuntu.com/p/ZNk5j9TBs8/](https://pastebin.ubuntu.com/p/ZNk5j9TBs8/)

---

### Post by ubfan1 on 2022-07-18
Sorry for my typo, that should be grub-common   only two m s  .

---

### Post by gatsbybom on 2022-07-18
sorry it was my fault mistyping it, i updated the answer tho, no much difference

---

### Post by gatsbybom on 2022-07-18
is there any fix possibility ? or must i install it again !

---

### Post by Impavidus on 2022-07-19
Try reinstalling grub-common:```
sudo apt install --reinstall grub-common
```

---

### Post by gatsbybom on 2022-07-20
**sudo apt install --reinstall grub-common**

```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 2,214 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://eg.archive.ubuntu.com/ubuntu jammy/main amd64 grub-common amd64 2.06-2ubuntu7 [2,214 kB]
Fetched 2,214 kB in 4s (540 kB/s)        
Preconfiguring packages ...
dpkg: warning: files list file for package 'linux-image-5.15.0-25-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-5.15.0-40-generic' missing; assuming package has no files currently installed
(Reading database ... 199324 files and directories currently installed.)
Preparing to unpack .../grub-common_2.06-2ubuntu7_amd64.deb ...
Unpacking grub-common (2.06-2ubuntu7) over (2.06-2ubuntu7) ...
Setting up linux-image-unsigned-5.15.0-41-generic (5.15.0-41.44) ...
Setting up grub-common (2.06-2ubuntu7) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for linux-image-unsigned-5.15.0-41-generic (5.15.0-41.44) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-41-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-unsigned-5.15.0-41-generic (--configure):
 installed linux-image-unsigned-5.15.0-41-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-unsigned-5.15.0-41-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Impavidus on 2022-07-20
So it unpacks grub-common, but still fails to run the scripts in /etc/grub.d.

What is now in that directory?```
ls -l /etc/grub.d
```
And what is now in your  /boot/grub/grub.cfg.new?```
cat  /boot/grub/grub.cfg.new
```

zz-update-grub (which is correctly called in the postinstall script) is supposed to call update-grub, from the grub2-common package, which in turn calls grub-mkconfig, from the grub-common package. The comments in your original /boot/grub/grub.cfg.new indicate that this works: grub-mkconfig knows the right file and directory to get the grub configuration, but fails to create a proper grub.cfg.

Could there be anything wrong with your grub-mkconfig? Version number of grub-common appears to be fine, but check anyway:```
sha256sum /usr/sbin/grub-mkconfig 
31009dbc888549fc54dd721c18e6498cbe0cb3dee582487c91a2e64455a6f238  grub-mkconfig
```
As you run the same version of Ubuntu as I do, that long sequence of hexadecimal digits should be the same.

Have you done anything that could interfere with the configuration of grub? Playing with alternative bootladers, grub customizer etc.?

---

### Post by gatsbybom on 2022-07-20
- the content of **/etc/grub**.d is empty


- [B]cat  /boot/grub/grub.cfg.new

[/B]```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


```


- **sha256sum /usr/sbin/grub-mkconfig **

```

31009dbc888549fc54dd721c18e6498cbe0cb3dee582487c91a2e64455a6f238  /usr/sbin/grub-mkconfig

```

- and yes, after installing ubuntu, the system wasn't able to identify the boot loader file path by itself and i had to choose it manually while booting , then after some playing in UEFI and legacy options in the BIOS, the system starts fine and it lasts for almost a month with no issues at all. then  this issue arise with no reason which make me unable to specify the responsible action that leads to it.

---

### Post by Impavidus on 2022-07-21
So apt tells you it unpacked grub-common, for the files from grub-common belonging in /etc/grub.d aren't there yet. Maybe it has to be configured first:```
sudo dpkg --configure grub-common
```Then look for the contents of /etc/grub.d again.

Playing with UEFI and legacy options opens another can of worms. Chances are you got your system to work in such a way that it would break at the first kernel upgrade. Can you provide any more details on this?

---

