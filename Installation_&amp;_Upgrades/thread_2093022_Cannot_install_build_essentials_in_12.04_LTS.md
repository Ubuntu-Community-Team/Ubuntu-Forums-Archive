---
title: "Cannot install build essentials in 12.04 LTS"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by BrokenLines on 2012-12-09
Okay, so I'm not sure if I should post this here or what.. I'm not  terrible at the command line, basically everything I've done I've used  it for. But for some reason I keep getting an error when I try and  install Build Essentials, only reason I have a desire for it is because I  need it to *make install* one of the applications. Here's what shows  every attempt I've done.

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.5) but 1.99-21ubuntu3.6 is to be installed
           Depends: grub-pc-bin (= 1.99-21ubuntu3.5) but 1.99-21ubuntu3.6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then I try apt-get -f install and still here's what shows...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gimp-help-en libbabl-0.0-0 libgegl-0.0-0 linux-headers-3.2.0-26
  gimp-help-common linux-headers-3.2.0-26-generic-pae libgimp2.0
  redeclipse-data libenet1a gimp-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-pc
The following packages will be upgraded:
  grub-pc
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0 B/140 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-35-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.10 (12.10) on /dev/sda7
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda8
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 2: /etc/grub.d/40_custom: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-35-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.10 (12.10) on /dev/sda7
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda8
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 2: /etc/grub.d/40_custom: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Yeah it was a lot and I had my hopes up, but it failed and now I'm lost.. Because I tried to install build essentials again and got the same as before. I tried running 'sudo apt-get update' but it didn't help at all. Anyone have advise?

---

### Post by oldos2er on 2012-12-09
Have you edited your /etc/grub.d/40_custom file?

---

### Post by darkod on 2012-12-09
I don't know whether all this can be because of one simple syntax error, but did you notice it says you have syntax error in 40_custom?

> /etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 2: /etc/grub.d/40_custom: Syntax error: "(" unexpected

It seems you were trying to make manual entries in 40_custom but you have the syntax wrong. You can temporarily disable the file (so the syntax error won't count) to see if it continues. If it does, you can investigate the syntax error later. To temporarily disable 40_custom:
```
sudo chmod -x /etc/grub.d/40_custom
```

After that try the sudo apt-get install -f again.
See if the result is the same and whether the syntax error is reported again or not (I'm not sure if only disabling the file is enough or you actually have to fix the error first).

---

### Post by BrokenLines on 2012-12-09
I did edit the 40_custom but it still works fine.. I'll temp. disable it and see what that does and hope it's works.. Thanks in advance for answering.

---

### Post by BrokenLines on 2012-12-09
steven@LinuxLTS:~$ sudo chmod -x /etc/grub.d/40_custom
[sudo] password for steven: 
steven@LinuxLTS:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gimp-help-en libbabl-0.0-0 libgegl-0.0-0 linux-headers-3.2.0-26 gimp-help-common
  linux-headers-3.2.0-26-generic-pae libgimp2.0 redeclipse-data libenet1a gimp-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-pc
The following packages will be upgraded:
  grub-pc
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0 B/140 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-35-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.10 (12.10) on /dev/sda7
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda8
done
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-35-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic-pae...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-34-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-34-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.10 (12.10) on /dev/sda7
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda8
done
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub2-common (= 1.99-21ubuntu3.5); however:
  Version of grub2-common on system is 1.99-21ubuntu3.6.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.5); however:
  Version of grub-pc-bin on system is 1.99-21ubuntu3.6.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-generic-pae (3.2.0.34.37) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up linux-generic-pae (3.2.0.34.37) ...
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
steven@LinuxLTS:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.5) but 1.99-21ubuntu3.6 is to be installed
           Depends: grub-pc-bin (= 1.99-21ubuntu3.5) but 1.99-21ubuntu3.6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Didn't change anything, still failed to install build essentials... Though I have noticed this, again.

E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea what that is and if that has something to do with it?

---

### Post by darkod on 2012-12-09
There is no syntax error reported now, so your 40_custom is definitely wrong.

But it is still stuck at upgrading the package grub-pc, and until ti finishes that it will not be able to install other software. Unfortunately, I can't see why is it stuck at grub-pc.

---

### Post by BrokenLines on 2012-12-09
While looking through it I did notice something odd to me...

dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub2-common (= 1.99-21ubuntu3.5); however:
  Version of grub2-common on system is 1.99-21ubuntu3.6.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.5); however:
  Version of grub-pc-bin on system is 1.99-21ubuntu3.6.
dpkg: error processing grub-pc (--configure):

with that how it is, could I change the grub2common to 1.99-21ubuntu3.5?

---

### Post by darkod on 2012-12-09
If grub-pc is holding it back, it should be fairly safe to completely remove it (purge) and reinstall it. But I can't say for 100% that it will resolve this. You might wanna wait for second opinion.

To purge grub2 and reinstall it boot your ubuntu installation and do in terminal:
```
sudo apt-get remove --purge grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda (if you use grub on the MBR of /dev/sda)
```

Since apt-get seems stuck, I don't know whether it will be able to remove and reinstall grub at all.

---

### Post by BrokenLines on 2012-12-09
Okay.. Well worse case scenario I have a backup on another drive.. I'll give this a try. One quick question, how do I get the 40_custom back for later reference?

---

### Post by BrokenLines on 2012-12-09
Not even the first command worked... So I'm stuck without a clue to fix this

---

### Post by oldos2er on 2012-12-09
> **BrokenLines said:**
> Okay.. Well worse case scenario I have a backup on another drive.. I'll give this a try. One quick question, how do I get the 40_custom back for later reference?

Did you create a backup copy before editing it? Always a good idea when editing system files. The default file is ```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

---

### Post by BrokenLines on 2012-12-09
Yes, that is what it is. But so far nothing has worked... I really need to fix this problem.

---

### Post by oldos2er on 2012-12-09
> **BrokenLines said:**
> Not even the first command worked.

Can you please post the terminal output from the command(s)?

---

### Post by BrokenLines on 2012-12-12
> **oldos2er said:**
> Can you please post the terminal output from the command(s)?

Sure, here you go.

Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2) but it is not going to be installed
 grub-pc-bin : Depends: grub-common (= 1.99-21ubuntu3.6) but it is not going to be installed
 grub2-common : Depends: grub-common (= 1.99-21ubuntu3.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

