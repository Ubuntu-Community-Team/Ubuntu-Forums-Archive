---
title: "Errors were encountered while processing:  linux-image-2.6.35-22-generic"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by kingv on 2010-10-20
I executed apt-get update/upgrade commands and I get this error constantly and I cant make it go away :( Any ideas? Thanks in advance! 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kingv on 2010-10-20
I executed apt-get update/upgrade commands and I get this error constantly and I cant make it go away :( Any ideas? Thanks in advance! 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rubi1200 on 2010-10-20
Try these commands in the terminal and report any errors:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Hope this helps.

---

### Post by kingv on 2010-10-20
> **Rubi1200 said:**
> Try these commands in the terminal and report any errors:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Hope this helps.

Thanks for your reply! However, it didnt work. Here's the output:


```
w1ck3d@w1ck3d:~$ sudo apt-get install -f
[sudo] password for w1ck3d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
w1ck3d@w1ck3d:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
```

---

### Post by drs305 on 2010-10-20
When running the post-installation scripts it didn't like something in /etc/default/grub. It got to line 23 (probably the end) and registered a complaint.

You can open and inspect the file:
```
gksu gedit /etc/default/grub
```
See if you find anything odd. You might make sure there is an empty line last, with no spaces on it. If you find something wrong, save the file and run "sudo update-grub".

---

### Post by kingv on 2010-10-20
> **drs305 said:**
> When running the post-installation scripts it didn't like something in /etc/default/grub. It got to line 23 (probably the end) and registered a complaint.

You can open and inspect the file:
```
gksu gedit /etc/default/grub
```
See if you find anything odd. You might make sure there is an empty line last, with no spaces on it. If you find something wrong, save the file and run "sudo update-grub".


hmm yeah I also think it has something to do with grub, but I have no clue what to look for...
here's my grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=>>1024x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by drs305 on 2010-10-20
Try changing this:
> 
[QUOTE]GRUB_GFXMODE=>>1024x768-24<<
[/QUOTE]
To:
> GRUB_GFXMODE=1024x768x24
Save the file and update grub.

---

### Post by kingv on 2010-10-20
> **drs305 said:**
> Try changing this:

To:

Save the file and update grub.
THAT WORKED! YOU'RE THE MAN! Kernel update installed correctly from what I can tell. You're help is much appreciated my friend. 


Also when i do the update I get these errors...I did some googling and it seems like it's a language bug or something....

```
Err http://archive.canonical.com maverick Release.gpg                                                                                                                         
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err http://archive.canonical.com/ maverick/partner Translation-en
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com/ maverick/partner Translation-en_US
  Unable to connect to archive.canonical.com:http:
Ign http://archive.canonical.com maverick Release
Ign http://archive.canonical.com maverick/partner amd64 Packages/DiffIndex
Ign http://archive.canonical.com maverick/partner amd64 Packages
Ign http://archive.canonical.com maverick/partner amd64 Packages
Err http://archive.canonical.com maverick/partner amd64 Packages
  Unable to connect to archive.canonical.com:http:
Fetched 4,634B in 21s (220B/s)
W: Failed to fetch http://archive.canonical.com/dists/maverick/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz  Unable to connect to archive.canonical.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sikander3786 on 2010-10-20
Please try

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by cariboo on 2010-10-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by kingv on 2010-10-20
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

My apologies, it wasn't on purpose. My browser pooped out and posted duplicates. Thanks for your help!

---

### Post by C.C.C.P. on 2011-03-08
I also got this problem here is my grub
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force irqpoll"
GRUB_CMDLINE_LINUX=”acpi=force irqpoll”

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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by automart on 2012-11-26
If grub config seems ok, but nothing works, try rebuilding the device map.
```
sudo grub-mkdevicemap
```
It will automatically update /boot/grub/device.map
Useful after adding a new raid array or a new hard drive.

---

### Post by oldos2er on 2012-11-26
Closed. Please don't bump old threads.

---

