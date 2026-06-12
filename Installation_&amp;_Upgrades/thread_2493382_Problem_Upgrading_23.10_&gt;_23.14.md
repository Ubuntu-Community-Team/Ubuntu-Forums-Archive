---
title: "Problem Upgrading 23.10 &gt; 23.14"
date: 2023-12-13
forum: Installation &amp; Upgrades
---

### Post by mhojonz on 2023-12-13
Apologies for newbie ignorance. I am trying to update 23.10 to 23.14 and get the following error...

$  sudo dpkg --configure -a
Setting up linux-image-6.5.0-14-generic (6.5.0-14.14) ...
Processing triggers for linux-image-6.5.0-14-generic (6.5.0-14.14) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.5.0-14-generic
 * dkms: autoinstall for kernel 6.5.0-14-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-6.5.0-14-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Found linux image: /boot/vmlinuz-6.5.0-10-generic
Found initrd image: /boot/initrd.img-6.5.0-10-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
Adding boot menu entry for UEFI Firmware Settings ...
/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.5.0-14-generic (--configure):
 installed linux-image-6.5.0-14-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-6.5.0-14-generic

---

### Post by deadflowr on 2023-12-13
?
No such release.
There's  24.04 in development.
Nothing called 23.14.

Are you trying to upgrade to the development release?

---

### Post by MAFoElffen on 2023-12-13
@deadflowr --

No. He is confused. Not a release upgrade. Rather an 23.10 "upgrade error" on failing to install Linux kernel 6.5.0-14 successfully...
> **mhojonz said:**
> 
/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.5.0-14-generic (--configure):
[COLOR=#ff0000]installed linux-image-6.5.0-14-generic package post-installation script subprocess returned error exit status 1[/COLOR]
Errors were encountered while processing:
linux-image-6.5.0-14-generic 


@mhojonz --

Welcome to Ubuntu  Forums. Could you please post the output from this, within CODE Tags? (Press "Advanced Reply" > Select the "#" Icon from the extended tool menu, and paste the output between those inserted CODE Tags.)
```

grep . /etc/default/grub

```
Most of the time that error thrown (error 127) when it is updating the grub menu, is when there is some kind of syntax error or extraneous character inside that file...

---

### Post by ian-weisser on 2023-12-13
The output clearly shows a plain, ordinary self-inflicted error.

```

/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127

```

Looks like you have been mucking about with Grub. Try telling us all about that.
A link to whatever instructions you were following would be very helpful.

---

### Post by MAFoElffen on 2023-12-13
> **ian-weisser said:**
> The output clearly shows a plain, ordinary self-inflicted error.

```

/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127

```

Looks like you have been mucking about with Grub. Try telling us all about that.
A link to whatever instructions you were following would be very helpful.
Yup...

Like I suspected: Another victim of Grub Customizer(?)

---

### Post by oldfred on 2023-12-13
I saved these, just in case.

Purge Grub-Customizer
[https://ubuntuforums.org/showthread.php?t=2492988&page=4](https://ubuntuforums.org/showthread.php?t=2492988&page=4)
[https://askubuntu.com/questions/1491892/i-messed-up-my-grub-config](https://askubuntu.com/questions/1491892/i-messed-up-my-grub-config)

---

### Post by mhojonz on 2023-12-15
```
[Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-14-generic
Found initrd image: /boot/initrd.img-6.5.0-14-generic
Found linux image: /boot/vmlinuz-6.5.0-10-generic
Found initrd image: /boot/initrd.img-6.5.0-10-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot 
entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
Adding boot menu entry for UEFI Firmware Settings ...
/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.5.0-14-generic (--configure):
 installed linux-image-6.5.0-14-generic package post-installation script subproc
ess returned error exit status 1
Errors were encountered while processing:
 linux-image-6.5.0-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
marshall@marshall-XPS-17-9700:~$ sudo apt clean
marshall@marshall-XPS-17-9700:~$ grep . /etc/default/grub
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
# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
#GRUB_DISABLE_OS_PROBER=false
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# Uncomment to disable graphical terminal
#GRUB_TERMINAL=console
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024x24 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by mhojonz on 2023-12-15
I was using grub customizer but something broke and I removed it.

---

### Post by MAFoElffen on 2023-12-15
> **mhojonz said:**
> I was using grub customizer but something broke and I removed it.
Thought so...

Try this
```

sudo chmod -R 644 /etc/grub.d/proxifiedScripts
sudo dpkg --configure -a

```
Tell me how that goes...

---

### Post by mhojonz on 2023-12-16
I have attempted to reinstall grub but am getting the following error with sudo update-grub

```
[sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

```

---

### Post by #&amp;thj^% on 2023-12-16
> **mhojonz said:**
> I have attempted to reinstall grub but am getting the following error with sudo update-grub

```
[sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

```

Please include the command you used to install grub.
The update grub offers those trying to help nothing relevant.

---

### Post by ian-weisser on 2023-12-16
One problem seems with a file /etc/grub.d/proxifiedScripts/linux

Have you looked at that file?
Do you use it? (Hint: No you don't)

---

### Post by oldfred on 2023-12-16
This says there is a problem somewhere.
> /boot/grub/grub.cfg.new file attached.
It could be in /etc/default/grub or in 40_custom.
Or if you installed Grub Customizer and one of its scripts is not compatible.


I add my own boot stanzas to 40 custom and got the .new file. Turned out I had a mis-match on  {}. Sometimes those types of errors are hard to find and it can be easier for a new user to just totally uninstall grub and install it without any changes.

---

### Post by mhojonz on 2023-12-17
After executing

sudo chmod -R 644 /etc/grub.d/proxifiedScripts and
sudo dpkg --configure -a 

I get a  permissions denied  error 

\sudo  update-grub
Sourcing file  `/etc/default/grub'
Generating grub configuration file  ...
Adding boot menu entry for UEFI Firmware Settings  ...
/etc/grub.d/LS_linux: 2:  /etc/grub.d/proxifiedScripts/linux: Permission  denied

Permission for proxifiedScripts as follows:

drw-r--r-- 2 root root  4096 Oct  8 09:54 proxifiedScripts

---

### Post by tea for one on 2023-12-17
I'm not 100% sure, but you will have to remove all traces of proxified scripts from /etc/grub.d.
Then, purge and re-install grub from a live session.
It may work, it may not..........?

From post no. 1, I also noted that you have a Windows Boot Manager.
Before you do anything else, please confirm that you have backups of your Windows and Ubuntu data.

More info here [https://forums.linuxmint.com/viewtopic.php?t=319789](https://forums.linuxmint.com/viewtopic.php?t=319789)

---

### Post by mhojonz on 2023-12-17
Happy to report problem is fixed using boot repair. Thanks to all for the help

---

