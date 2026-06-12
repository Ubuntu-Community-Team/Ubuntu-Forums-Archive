---
title: "half configured packages"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by mayankbhagya on 2009-12-17
My notebook had auto update enabled. Linux kernel upgraded to 2.6.31-16. But I couldn't install any new software using apt-get after that. It showed the names of a few packages saying "these have problems."

When I dug deeper, I found out that 2 kernel packages were left half-configured in dpkg status file:
linux-headers-2.6.31-16-generic
linux-image-2.6.31-16-generic

Now I can't use my apt-get to install anything properly.. Even the Ubuntu s/ware center has problems installing packages... 

Plz help..:(

---

### Post by nibirumarduk on 2009-12-17
> **mayankbhagya said:**
> My notebook had auto update enabled. Linux kernel upgraded to 2.6.31-16. But I couldn't install any new software using apt-get after that. It showed the names of a few packages saying "these have problems."

When I dug deeper, I found out that 2 kernel packages were left half-configured in dpkg status file:
linux-headers-2.6.31-16-generic
linux-image-2.6.31-16-generic

Now I can't use my apt-get to install anything properly.. Even the Ubuntu s/ware center has problems installing packages... 

Plz help..:(

You need to re-run the upgrade and give us an output of the error. Although all that may be required is just a "sudo dpkg --force-overwrite -i /var/cache/apt/archives/name-of-problematic-package.deb; sudo dpkg --configure -a; sudo update-grub2" (IGNORE quotes)

Also do take a look at [http://ubuntuforums.org/showthread.php?t=1357523](http://ubuntuforums.org/showthread.php?t=1357523)
that is, if the nature of the botched upgrade has more to do with something identified in that thread.

Hope this helps!

---

### Post by mayankbhagya on 2009-12-17
> $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-16-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                        headers-2.6.31-16-generic (2.6.31-16.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-16-generic; however:
  Package linux-headers-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-2.6.31-16-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-16-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Output of sudo apt-get install -f.

---

### Post by mayankbhagya on 2009-12-17
Thanx man.. the other post of yours was just awesome...!!
It worked.. I wrote 'exit 0' in postinst scripts of both the packages before the given line numbers (1002 and 110).

Then, sudo dpkg --configure -a worked!

But since these are kernel packages, inappropriate install won't create any problem, right..?

---

### Post by nibirumarduk on 2009-12-17
> **mayankbhagya said:**
> Thanx man.. the other post of yours was just awesome...!!
It worked.. I wrote 'exit 0' in postinst scripts of both the packages before the given line numbers (1002 and 110).

Then, sudo dpkg --configure -a worked!

But since these are kernel packages, inappropriate install won't create any problem, right..?

You are right. The thing with kernel packages is that there may be certain missing support for certain hardware, functionalities, etc. It depends on what command that particular script wanted to call and for what purpose. 

The suggested method is one of the only 3 ways to get your apt and upgrade functioning again. Would you otherwise have a system where package management tools cannot work/refuse to work in that they cannot install anything you want or perform upgrades? There are trade-offs, like it is in life. This is one. What is important is, does the new kernel run fine for you so far? Detected anything amiss yet? In most cases, I believe it should not.

Best of luck!

---

### Post by mayankbhagya on 2009-12-18
Hmm.. no, not yet. So far it is going good...
Let's hope for the best and wait for the next kernel release...

---

### Post by mayankbhagya on 2010-01-14
After I upgraded to the next kernel (2.6.31-17), my apt-get has again started giving errors in the post installation script.

This is what happens when I try installing something (git in this case):
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting gnuit instead of git
The following NEW packages will be installed:
  gnuit
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
5 not fully installed or removed.
Need to get 324kB of archives.
After this operation, 1,384kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe gnuit 4.9.5-1 [324kB]
Fetched 324kB in 20s (15.9kB/s)                                                                                                                             
Selecting previously deselected package gnuit.
(Reading database ... 193248 files and directories currently installed.)
Unpacking gnuit (from .../gnuit_4.9.5-1_i386.deb) ...
update-alternatives: error: no alternatives for git.
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-17-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-17-generic; however:
  Package linux-image-2.6.31-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.17.30); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-17-generic (2.6.31-17.54) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                       Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-17-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-17-generic; however:
  Package linux-headers-2.6.31-17-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up gnuit (4.9.5-1) ...
No apport report written because MaxReports is reached already
                                                              Ignoring install-info called from maintainer script
The package gnuit should be rebuild with new debhelper to get trigger support

Errors were encountered while processing:
 linux-image-2.6.31-17-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-17-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Some one please help me with this!!!
Shall I post the contents of installation scripts also..?

---

