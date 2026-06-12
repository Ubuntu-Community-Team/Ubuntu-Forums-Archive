---
title: "image upgrades not working"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by RogerM on 2012-07-24
The linux images are no longer upgrading.

This is the summary at the end of a long output:

 linux-image-3.2.0-26-generic
 linux-image-3.2.0-27-generic
 linux-image-generic
 linux-image
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried the usual recommendations:

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get install -f

to no avail.

Any more suggestions?

---

### Post by Zorael on 2012-07-24
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
No other specifics?

Also see if there's anything of interest at the end of **/var/log/apt/term.log**.

---

### Post by RogerM on 2012-07-24
Sorry, there is quite a bit more:


Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
E: /usr/share/initramfs-tools/hooks/watershed failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.2.0-26-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
E: /usr/share/initramfs-tools/hooks/watershed failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.2.0-27-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                          Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-3.2.0-27-generic
 linux-image-generic
 linux-image
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dino99 on 2012-07-24
looks like you does not got the kernel headers, or these downloads are corrupted

is it a genuine ubuntu kernel ?

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by RogerM on 2012-07-24
Yes, somehow I had unintentionally installed 12.10 so I recently downloaded Kubuntu 12.04 do CDROM which was a pain to install but after about many tries and about 6 hours it got installed except for this problem.

I am hoping to fix this without another install.  This problem or something similar appears to be experienced by others but as I said the usual:

sudo apt-get install -f 
sudo dpkg --configure -a

does nothing to help.

Somehow the linux-image stuff is corrupted but still running okay except for these updating issues.

---

### Post by dino99 on 2012-07-24
you need to clean the system as much as you can: clean/autoclean/autoremove/bleachit (as root) and also /lib/modules/theBorkedKernelFolders

---

### Post by RogerM on 2012-07-24
Thanks, I can do all the apt-get & bleachit but I don't know what I need to do for:

/lib/modules/theBorkedKernelFolders

What files can I safely delete and which ones are needed?

---

### Post by Zorael on 2012-07-24
```
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
**[COLOR="Red"]E: /usr/share/initramfs-tools/hooks/watershed failed with return 1.[/COLOR]**
update-initramfs: failed for /boot/initrd.img-3.2.0-26-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
```
That there is your issue.

```
Package: **watershed**
Priority: extra
Section: admin
***[...]***
Description-en: reduce superfluous executions of idempotent command
 watershed may be run around a command such that any further attempts to
 run the command while another copy is running will only result in one
 initial further attempt.
```

Is this [watershed](apt://watershed) something you're actually using? It looks to be LVM-related.

Regardless, for whatever reason its update-initramfs hook exits with errors. Looking at said script, the only way I can see that happening is if the **/lib/udev/watershed** file is missing or otherwise cannot be read.

[list][*]To manually run update-initramfs with (hopefully interesting) verbose output of what's happening;
```
$ sudo update-initramfs -vuk 3.2.0-26-generic
```
[*]To (reversibly) disable watershed being copied into initramfs;
```
$ sudo chmod -x /usr/share/initramfs-tools/hooks/watershed
```[/list]

---

### Post by RogerM on 2012-07-24
Thanks Zorael, I used:

$ sudo chmod -x /usr/share/initramfs-tools/hooks/watershed

then 

$ sudo apt-get install -f 

and now everything appears to be okay.

I have no idea why watershed was there it was not indicated as 'installed' by Synaptic.

Thanks again,
   Roger

P.S. I would mark it SOLVED but I don't see where that is done?

---

### Post by Zorael on 2012-07-24
Cheers. :3

Thread Tools (up top) -> Mark this thread as solved

---

