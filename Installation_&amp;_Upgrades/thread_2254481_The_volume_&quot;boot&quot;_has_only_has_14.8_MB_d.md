---
title: "The volume &quot;boot&quot; has only has 14.8 MB disk space remaining"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2014-11-27
Please see the error attached below. I configured my Windows 8.1 dual boot system more than 6 months ago and it has been working fine. All Ubuntu partitions are installed inside a manually configured and encrypted LVM volume. I have not made any change to boot that I am aware of and I could not tell you the last time I logged into Windows 8.1, if that is suspect. Please also find a GParted screenshot attached below. If you need me to enter commands and paste the output please advise. The install process, including all commands and output, can be found at this post: [http://ubuntuforums.org/showthread.php?t=2218477&p=13042413#post13042413](http://ubuntuforums.org/showthread.php?t=2218477&p=13042413#post13042413)

I find it very strange this started happening, apparently all of a sudden. Any ideas what is filling up the boot partition, and which boot partition it is referring to? From GParted I have just been reminded there are two. 

What can I do to resolve this? I am hoping to avoid re-installing. Since the Live CD did not offer the setup I have outlined, configuring it took a long time.

---

### Post by ajgreeny on 2014-11-27
See [http://ubuntuforums.org/showthread.php?t=2254430&p=13175634#post13175634](http://ubuntuforums.org/showthread.php?t=2254430&p=13175634#post13175634) which is the same problem as you have, though in that case it may be for a different reason.

---

### Post by Dáire Fagan on 2015-05-12
> **ajgreeny said:**
> See [http://ubuntuforums.org/showthread.php?t=2254430&p=13175634#post13175634](http://ubuntuforums.org/showthread.php?t=2254430&p=13175634#post13175634) which is the same problem as you have, though in that case it may be for a different reason.

Thanks for the reply. Please see below where I tried the instructions from the post unsuccessfully. I am still unable to ugprade or install new software. Please advise:

dusf@generic:~$ sudo apt-get autoremove
[sudo] password for dusf:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-signed-image-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic (= 3.13.0-44.73) but it is not installed
E: Unmet dependencies. Try using -f.

dusf@generic:~$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-44-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-44-generic
0 to upgrade, 1 to newly install, 0 to remove and 270 not to upgrade.
8 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 42.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 583521 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-44-generic (3.13.0-44.73) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.13.0-44-generic' to '/boot/abi-3.13.0-44-generic.dpkg-new': failed to write (No space left on device)
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

dusf@generic:~$ ls /boot | grep vmlinuz
vmlinuz-3.13.0-24-generic
vmlinuz-3.13.0-29-generic
vmlinuz-3.13.0-29-generic.efi.signed
vmlinuz-3.13.0-30-generic
vmlinuz-3.13.0-30-generic.efi.signed
vmlinuz-3.13.0-33-generic
vmlinuz-3.13.0-34-generic
vmlinuz-3.13.0-34-generic.efi.signed
vmlinuz-3.13.0-35-generic
vmlinuz-3.13.0-35-generic.efi.signed
vmlinuz-3.13.0-36-generic
vmlinuz-3.13.0-36-generic.efi.signed
vmlinuz-3.13.0-37-generic
vmlinuz-3.13.0-37-generic.efi.signed
vmlinuz-3.13.0-39-generic
vmlinuz-3.13.0-39-generic.efi.signed
vmlinuz-3.13.0-40-generic
vmlinuz-3.13.0-40-generic.efi.signed
vmlinuz-3.13.0-43-generic
dusf@generic:~$
dusf@generic:~$
dusf@generic:~$ sudo apt-get remove linux-image-3.13.0-24-generic
[sudo] password for dusf:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic but it is not going to be installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-signed-image-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic (= 3.13.0-44.73) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dusf@generic:~$ sudo apt-get remove linux-image-3.13.0-29-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-29-generic : Depends: linux-image-3.13.0-29-generic but it is not going to be installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-signed-image-3.13.0-29-generic : Depends: linux-image-3.13.0-29-generic (= 3.13.0-29.53) but it is not going to be installed
 linux-signed-image-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic (= 3.13.0-44.73) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dusf@generic:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-44-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-image-3.13.0-44-generic
0 to upgrade, 1 to newly install, 0 to remove and 270 not to upgrade.
8 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 42.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 583521 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-44-generic (3.13.0-44.73) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.13.0-44-generic' to '/boot/abi-3.13.0-44-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-44-generic /boot/vmlinuz-3.13.0-44-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-44-generic_3.13.0-44.73_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dusf@generic:~$ sudo apt-get remove linux-image-3.13.0-24-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic but it is not going to be installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-44-generic but it is not going to be installed
 linux-signed-image-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic (= 3.13.0-44.73) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by ajgreeny on 2015-05-12
I got your PM, which in this case was needed or I would not have found this thread again, because, ---
Good heavens; I'm confused; six months on and still that problem, or did my suggestion work originally and it has now happened again?

We have all moved on now to kernel 3.13.0-52 (those who stuck with the 3.13 kernel series) and there have been many new versions since the 3.13.0.44 that you mention above.
Do you still have all those old kernels in your system, ie, from 24 - 43, that you did not manage to remove previously, or did they all go and new ones have taken their place?

Because you chose to use LVM and encryption, which gives you a silly, small and separate /boot partition, you really must make sure that you remove older kernels when you see new ones appear in the regular updates, and keep only two, the one you're using and the previous version, which at the moment would be 3.13.0-51 and 3.13.0-52.

---

