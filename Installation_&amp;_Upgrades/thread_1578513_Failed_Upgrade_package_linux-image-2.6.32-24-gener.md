---
title: "Failed Upgrade package linux-image-2.6.32-24-generic-pae"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by CyberBob on 2010-09-20
My normal update/upgrade of packages on a LAMP server (Ubuntu 10.04) for my business has resulted in the following error:

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic-pae /boot/vmlinuz-2.6.32-24-generic-pae
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic-pae.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried several things without resolving the error:

```
sudo dpkg --configure -a  

sudo apt-get -f install

sudo apt-get upgrade

sudo apt-get purge
```

when I invoke the following command I get :

```
~$ uname -r
2.6.32-24-generic-pae
```

and when I attempt to upgrade the package again:

```
~$ sudo apt-get upgrade
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
```

... and at the end of the process (using any of the commands posted above) I get the initial snippet I posted as the result.  Seems like a vicious little circle.

Anyone have a similar problem or know how to clean things up here?

Thanks ...

---

### Post by CyberBob on 2010-09-27
Update:  After receiving a notice from Landscape that my server was still in need of upgrading the new kernel packages I attempted the upgrade once again, and it seems to get a bit further ... an error still persists:

```
solimeno@Gabbriellini:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 8,250B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-generic-pae 2.6.32.25.27 [4,122B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-generic-pae 2.6.32.25.27 [4,128B]
Fetched 8,250B in 0s (15.7kB/s)             
(Reading database ... 164009 files and directories currently installed.)
Preparing to replace linux-generic-pae 2.6.32.24.25 (using .../linux-generic-pae_2.6.32.25.27_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 2.6.32.24.25 (using .../linux-image-generic-pae_2.6.32.25.27_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.42 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-24-generic-pae
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.15-27-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic-pae /boot/vmlinuz-2.6.32-24-generic-pae
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic-pae.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-24-generic-pae
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.15-27-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-25-generic-pae /boot/vmlinuz-2.6.32-25-generic-pae
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-25-generic-pae.postinst line 1003.
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
           Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
solimeno@Gabbriellini:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-24-generic-pae
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/vmlinuz-2.6.15-27-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-25-generic-pae /boot/vmlinuz-2.6.32-25-generic-pae
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-25-generic-pae.postinst line 1003.
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae

```

---

### Post by CyberBob on 2010-09-29
NOT SOLVED! ... here is how I THOUGHT that I succeeded in resolving this issue on my own:


[LIST=1]
[*]using aptitude (instead of apt-get)
[*]purged all of the kernel packages that were not able to be configured without errors
[*]purged any dependencies that were not needed
[*]checked for errors after running aptitude by re-running sudo dpkg --configure -a  and also apt-get -f install
[*]dpkg and apt-get commands returned nothing ... so I interpret this as an up-to-date system
[/LIST]

In fact, after doing this the system required a restart, and I had purged ALL of the kernel images on the system - duh!

Using the server edition install CD for lucid 10.04 I was able to use rescue mode to re-install the current kernel image (linux-image-2.6.32-25-generic) and successfully rebooted the system - and my web server is back in operation.  HOWEVER, I still have the same problem - after logging in via SSH from my laptop:

```


solimeno@Gabbriellini:~$ sudo apt-get upgrade
[sudo] password for solimeno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.32-25-generic (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-25-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-25-generic-pae /boot/vmlinuz-2.6.32-25-generic-pae
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-25-generic-pae.postinst line 1003.
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-25-generic; however:
  Package linux-image-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.25.27); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.32-25-generic
 linux-image-2.6.32-25-generic-pae
 linux-image-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)
solimeno@Gabbriellini:~$ 

```

Does anyone know how to FIX this???

---

### Post by owenspa on 2010-09-30
I have the same problem with 2.6.32-25-generic, attempting to

```
apt-get install linux-image-generic linux-headers-generic
```

I've  found a sledge hammer solution.  Probably not recommended, I've undone
the change after successfully installing the latest kernel.

The fix is to nobble the post install scripts so they are forced
to return the success code.  Given that I don't have "nvidia-common"
installed that should be fine.

The post install scripts causing the problems for these two packages are

```
/etc/kernel/postinst.d/nvidia-common
/etc/kernel/header_postinst.d/nvidia-common
```

Simply edit these files and add a line

```
exit 0
```

**after the very 1st line**.

An "apt-get install" then worked for me, I rebooted with the
new kernel OK.  And I've since undone the edits to the files
above in the hope that it wont be required next time.

---

### Post by owenspa on 2010-09-30
I wouldn't mind betting that those two scripts are left over
when I removed "nvidia-common" et al in favour of "nvidia-current".
That is the "nvidia-common" removal scripts were faulty.

Does any-one know?  I suspect a permanent fix for me might be to
simply remove both scripts?

---

### Post by owenspa on 2010-09-30
I can answer this myself.  Simply run

```
dpkg --purge nvidia-common
```

and the files go away.

I had being relying on "apt-get purge nvidia-common" that consistantly reported that it couldn't do anything as the package wasn't installed.

---

### Post by CyberBob on 2010-10-01
WOW.  Great replies - Thank You!

All I had to do was:

```

solimeno@Gabbriellini:~$ sudo dpkg --purge nvidia-common
(Reading database ... 57131 files and directories currently installed.)
Removing nvidia-common ...
Purging configuration files for nvidia-common ...

solimeno@Gabbriellini:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-25-generic (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic

Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-25-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-25-generic-pae /boot/vmlinuz-2.6.32-25-generic-pae

Setting up linux-image-generic (2.6.32.25.27) ...
Setting up linux-image (2.6.32.25.27) ...
solimeno@Gabbriellini:~$ 

```

... and the mess has been cleaned up!  I wonder why the nvidia-common package was ever installed anyway - this machine has been configured as a server from day one (several years old) and is a "headless" server - I don't bother connecting a monitor unless I do a distribution upgrade (e.g. 8.04 to 10.04 as I did recently).

Thank you again, owenspa, for sorting this out.

I hope this experience helps others out if the same situation occurs.

---

### Post by fak3r on 2010-10-05
I can add a +1, this worked for me as well, thank you! Just for simplicity, here is what worked...

```
dpkg --purge nvidia-common; dpkg --configure -a
```

---

### Post by duchess^ on 2011-01-17
> **fak3r said:**
> I can add a +1, this worked for me as well, thank you! Just for simplicity, here is what worked...
dpkg --purge nvidia-common; dpkg --configure -a
```
dpkg --purge nvidia-common; dpkg --configure -a
```

This worked for me too when I added [FONT=Courier New]sudo[/FONT] before each command 

Shouldn't this thread be labeled as solved?

---

