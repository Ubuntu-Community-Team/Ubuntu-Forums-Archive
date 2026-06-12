---
title: "How to avoid filling /boot on encrypted installation of ubuntu 16.04?"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by mossroy2 on 2016-11-23
I've installed several computers with encrypted disk (configured by the  installer, using LUKS/cryptsetup) : /boot has its own partition.
I kept the default settings about upgrades.

After some time, several upgrades are installed (either automatically or manually), and /boot gets filled by kernel versions.
Which  gives error messages like "Not enough free disk space. The upgrade  needs (...) free space on /boot. Please free at least (...) of disk space on  /boot".

My question is not how to free some space on /boot (I know it can be done with apt remove of some old kernels).
I'm wondering how to avoid such situation in the future.

I  read  [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)  , which describes precisely my symptoms. As it's marked as "fix  released" on 16.04, I thought this would not happen any more (with  default settings).

So I'm confused : what should I do to avoid /boot from getting filled by kernel versions (on ubuntu 16.04)?

---

### Post by oldfred on 2016-11-23
Have you reviewed:
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

I regularly get this message when updating from terminal.
And the list of items to remove is the older kernels.

Use 'sudo apt autoremove' to remove them.

---

### Post by mossroy2 on 2016-11-23
Thanks for your reply, oldfred.

From what I read in your link, Ubuntu 16.04 does not need any custom settings to have unattended-upgrades remove old kernels.
I checked that unattended upgrades are enabled (through the GUI), and that the 2 lines mentioned in [https://help.ubuntu.com/community/RemoveOldKernels#Configure_Unattended_Upgrades_to_Remove_Unneeded_Kernels_Automatically](https://help.ubuntu.com/community/RemoveOldKernels#Configure_Unattended_Upgrades_to_Remove_Unneeded_Kernels_Automatically) (in the Ubuntu 16.04 paragraph) are NOT present in /etc/apt/apt.conf.d/50unattended-upgrades
If I understood correctly, it should work fine with default settings?

It's not so easy to reproduce kernel updates. But I tried to do it in a VirtualBox VM :
- install Ubuntu 16.04.1 (x64), with full disk encryption, and with  network disabled in VirtualBox (so that the updates are not  automatically installed at this step)
- run "sudo unattended-upgrades -v" which is (I suppose?) what is periodically launched for automatic updates
The kernel gets updated (to 4.4.0-47), but the previous one (4.4.0-31)  is still there. I suppose it's normal because 4.4.0-31 is currently in  use.

If I restart the VM, uname tells me that I'm now running 4.4.0-47. If I run the following command (coming from your link) :
```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
```
I get :
```
ii linux-image-4.4.0-31-generic ...
```
which should mean that this version is installed and eligible for removal?

But ```
sudo apt autoremove
``` does not remove anything.
I only have 2 kernels in this VM : 4.4.0-31 (the one initially installed) and 4.4.0-47 (installed by unattended-upgrades).

Again, my goal is not to remove the kernels (I know how to do it  manually), but to have a way to avoid the problem to happen again (by letting the kernels by removed automatically).

---

### Post by oldfred on 2016-11-23
My /etc/apt/apt.conf.d/20auto-upgrades

```
Changed from this:
APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Unattended-Upgrade "0";
to this:
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";

```
And I believe then mine is also wrong. Should be a 1 and that is why I have to manually run it.

[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)

---

### Post by ian-weisser on 2016-11-23
> **mossroy2 said:**
> But ```
sudo apt autoremove
``` does not remove anything.

That seems like expected behavior.
The script in /etc/kernel/postinst.d/apt-auto-removal that marks older kernels as eligible for autoremoval is understandably conservative - it tries to keep a minimum of two kernels. If the newer is broken you can still boot to the older. In some conditions, it will keep three kernels.

If you are getting out-of-space conditions with only two kernels installed (no room for a third kernel to install), then your /boot partition may be too small, or it may have detritus from previous packages or problems left over in it. The Ubuntu installer tries to make room for four-and-a-fraction installed kernels in /boot, but circumstances may prevent it from succeeding.

---

### Post by mossroy2 on 2016-11-23
The /boot partition has a size of 473MB, both on the physical machine   and in the VM. Each kernel version seems to take ~50MB so it can hold   numerous versions.
I got out of space in /boot on several physical machines, but it needed many versions installed (much more than 4).
So I don't think it comes from a too small /boot partition.

After  a standard installation of ubuntu 16.04.1 (with disk encryption),  are  there any settings that need to be changed so that older kernels  are  automatically removed?
Like /etc/apt/apt.conf.d/10periodic as suggested in [https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html) , or /etc/apt/apt.conf.d/20auto-upgrades as suggested by oldfred?

I understand that the kernel removal has to be conservative and careful : that's highly advisable for something that critical.

The purpose of the VM was to try to have a scenario we could reproduce. Snapshots would help trying different settings.
But  I'm not sure how to simulate several kernel upgrades without  installing  them manually. I suppose I could add a custom apt repository  (with a  -security suffix in the name), put newer kernels in it one at a  time,  and run unattended-upgrades between each. Not that easy...

---

### Post by oldfred on 2016-11-23
I do not think there is anything that prevents you from installing a bunch of old kernels just to see what happens. I look in synaptic and see all the old kernels that are available.

---

### Post by mossroy2 on 2016-11-23
> **oldfred said:**
> I do not think there is anything that prevents you from installing a bunch of old kernels just to see what happens. I look in synaptic and see all the old kernels that are available.
Sure, but in this case these kernels would be marked as manually  installed. So I suppose they will not be automatically deleted like the  ones coming from security updates

---

### Post by ian-weisser on 2016-11-23
Apt marking on kernel packages is already changed by the /etc/kernel/postinst.d script, so go ahead and try installing more kernels.

EDIT: I was mistaken; that's not true...but the apt marking can be changed manually after installation.

---

### Post by mossroy2 on 2016-11-25
Here is what I tested today :
- Install Ubuntu 16.04 amd64 (not 16.04.1) with full disk encryption, and network disabled, inside a new VM in VirtualBox
- Install Guest additions, and transfer all the kernel updates (packages linux-image-*-generic.deb downloaded from [http://packages.ubuntu.com/xenial/linux-image](http://packages.ubuntu.com/xenial/linux-image)) through a shared folder
- Install all these kernel updates except the latest one (4.4.0-47) with sudo dpkg -i. That makes 10 installed kernels, taking 286MB in /boot (which is mounted in a 472MB partition). Note that I did not install the kernel headers and the liniux-image-extra-* packages
- Restart the VM to use kernel 4.4.0-45
- Run "sudo apt autoremove" : nothing is removed
- Enable network for the VM and run "sudo unattended-upgrades -v" : kernel 4.4.0-47 is installed, with other security updates AND kernel 4.4.0-21 is auto-removed (but not the other ones)
- Restart the VM to use kernel 4.4.0-47, run "sudo apt autoremove" : nothing is removed

I have made many snapshots on the VM, so I can easily do some more tests.

---

### Post by ian-weisser on 2016-11-25
Tips I found helpful troubleshooting mysterious apt absences or actions:

- Please verify that all those kernels are actually installed (dpkg -l | grep linux-image)
- Please verify that all those kernels have a matching initrd.img in /boot (ls -l /boot). Each initrd.img should consume about 40MB, so I find your total usage of 286MB curious.

- Before starting a session, check for the next automatic apt update to prevent confusion (systemctl list-timers apt-daily.timer)
- Before starting a session, check the unattended-upgrade log for events that occurred behind yourback (/var/log/unattended-upgrades/unattended-upgrades.log)

- After each apt update, check for a success timestamp (ls -l /var/lib/apt/periodic)
- After each upgrade or unattended-upgrade, check for a success timestamp (ls -l /var/lib/apt/periodic)

---

### Post by mossroy2 on 2016-11-26
```
dpkg -l | grep linux-image
rc  linux-image-4.4.0-21-generic               4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic               4.4.0-22.40                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic               4.4.0-34.53                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic               4.4.0-36.55                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic               4.4.0-38.57                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic               4.4.0-42.62                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic               4.4.0-45.66                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic               4.4.0-47.68                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic         4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic         4.4.0-47.68                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.47.50                                         amd64        Generic Linux kernel image
```
```

ls -l /boot
total 282114
-rw-r--r-- 1 root root  1239612 mai   13  2016 abi-4.4.0-22-generic
-rw-r--r-- 1 root root  1239732 juin   8 23:39 abi-4.4.0-24-generic
-rw-r--r-- 1 root root  1240018 juin  24 14:03 abi-4.4.0-28-generic
-rw-r--r-- 1 root root  1240067 juil. 13 03:59 abi-4.4.0-31-generic
-rw-r--r-- 1 root root  1241623 juil. 27 23:28 abi-4.4.0-34-generic
-rw-r--r-- 1 root root  1241960 août  11 21:58 abi-4.4.0-36-generic
-rw-r--r-- 1 root root  1242262 sept.  6 20:52 abi-4.4.0-38-generic
-rw-r--r-- 1 root root  1242701 oct.   8 04:15 abi-4.4.0-42-generic
-rw-r--r-- 1 root root  1242701 oct.  19 18:34 abi-4.4.0-45-generic
-rw-r--r-- 1 root root  1243086 oct.  27 00:27 abi-4.4.0-47-generic
-rw-r--r-- 1 root root   189520 mai   13  2016 config-4.4.0-22-generic
-rw-r--r-- 1 root root   189521 juin   8 23:39 config-4.4.0-24-generic
-rw-r--r-- 1 root root   189533 juin  24 14:03 config-4.4.0-28-generic
-rw-r--r-- 1 root root   189558 juil. 13 03:59 config-4.4.0-31-generic
-rw-r--r-- 1 root root   189676 juil. 27 23:28 config-4.4.0-34-generic
-rw-r--r-- 1 root root   189696 août  11 21:58 config-4.4.0-36-generic
-rw-r--r-- 1 root root   189732 sept.  6 20:52 config-4.4.0-38-generic
-rw-r--r-- 1 root root   189760 oct.   8 04:15 config-4.4.0-42-generic
-rw-r--r-- 1 root root   189760 oct.  19 18:34 config-4.4.0-45-generic
-rw-r--r-- 1 root root   189809 oct.  27 00:27 config-4.4.0-47-generic
drwxr-xr-x 5 root root     1024 nov.  25 22:39 grub
-rw-r--r-- 1 root root 13897960 nov.  25 21:20 initrd.img-4.4.0-22-generic
-rw-r--r-- 1 root root 13894070 nov.  25 21:25 initrd.img-4.4.0-24-generic
-rw-r--r-- 1 root root 13893499 nov.  25 21:26 initrd.img-4.4.0-28-generic
-rw-r--r-- 1 root root 13869412 nov.  25 21:28 initrd.img-4.4.0-31-generic
-rw-r--r-- 1 root root 13871344 nov.  25 21:32 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root 13872250 nov.  25 21:32 initrd.img-4.4.0-36-generic
-rw-r--r-- 1 root root 13873226 nov.  25 21:32 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root 13878053 nov.  25 21:33 initrd.img-4.4.0-42-generic
-rw-r--r-- 1 root root 13878802 nov.  25 21:33 initrd.img-4.4.0-45-generic
-rw-r--r-- 1 root root 38795106 nov.  25 22:38 initrd.img-4.4.0-47-generic
drwx------ 2 root root    12288 nov.  25 20:10 lost+found
-rw-r--r-- 1 root root   182704 janv. 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 janv. 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 janv. 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3855781 mai   13  2016 System.map-4.4.0-22-generic
-rw------- 1 root root  3855383 juin   8 23:39 System.map-4.4.0-24-generic
-rw------- 1 root root  3859655 juin  24 14:03 System.map-4.4.0-28-generic
-rw------- 1 root root  3866473 juil. 13 03:59 System.map-4.4.0-31-generic
-rw------- 1 root root  3866644 juil. 27 23:28 System.map-4.4.0-34-generic
-rw------- 1 root root  3867829 août  11 21:58 System.map-4.4.0-36-generic
-rw------- 1 root root  3869329 sept.  6 20:52 System.map-4.4.0-38-generic
-rw------- 1 root root  3869895 oct.   8 04:15 System.map-4.4.0-42-generic
-rw------- 1 root root  3869895 oct.  19 18:34 System.map-4.4.0-45-generic
-rw------- 1 root root  3873447 oct.  27 00:27 System.map-4.4.0-47-generic
-rw------- 1 root root  7015440 mai   13  2016 vmlinuz-4.4.0-22-generic
-rw------- 1 root root  7020176 juin   8 23:39 vmlinuz-4.4.0-24-generic
-rw------- 1 root root  7026864 juin  24 14:03 vmlinuz-4.4.0-28-generic
-rw------- 1 root root  7047504 juil. 13 03:59 vmlinuz-4.4.0-31-generic
-rw------- 1 root root  7046160 juil. 27 23:28 vmlinuz-4.4.0-34-generic
-rw------- 1 root root  7045472 août  11 21:58 vmlinuz-4.4.0-36-generic
-rw------- 1 root root  7051680 sept.  6 20:52 vmlinuz-4.4.0-38-generic
-rw------- 1 root root  7053472 oct.   8 04:15 vmlinuz-4.4.0-42-generic
-rw------- 1 root root  7054208 oct.  19 18:34 vmlinuz-4.4.0-45-generic
-rw------- 1 root root  7060896 oct.  27 00:27 vmlinuz-4.4.0-47-generic
```
Maybe the initrd images are smaller because I did not install the linux-image-extra packages?

```
systemctl list-timers apt-daily.timer
NEXT                          LEFT          LAST                          PASSED
sam. 2016-11-26 14:02:49 CET  2h 30min left ven. 2016-11-25 21:06:54 CET  14h ag

1 timers listed.
Pass --all to see loaded but inactive timers, too.
```

In /var/log/unattended-upgrades/unattended-upgrades.log, there is only the one I manually started (there was no network access before that, which prevented it in any case)
```

ls -l /var/lib/apt/periodic
total 0
-rw-r--r-- 1 root root 0 nov.  25 22:39 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 nov.  26 11:30 update-success-stamp
```
(November 25 22:39 was the time when I manually started unattended-upgrades, November 26 11:30 is 5 minutes ago, when I started the VM)

---

### Post by ian-weisser on 2016-11-26
Take a look at the file: /etc/apt/apt.conf.d/01autoremove-kernels

At the bottom is a big section marked '/* Debug information'. Please share.

---

### Post by mossroy2 on 2016-11-26
Here is the end of /etc/apt/apt.conf.d/01autoremove-kernels :
```
/* Debug information:
# dpkg list:
ii  linux-image-4.4.0-21-generic               4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic               4.4.0-22.40                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic               4.4.0-34.53                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic               4.4.0-36.55                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic               4.4.0-38.57                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic               4.4.0-42.62                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic               4.4.0-45.66                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic               4.4.0-47.68                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-21-generic         4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic         4.4.0-47.68                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.47.50                                         amd64        Generic Linux kernel image
# list of installed kernel packages:
4.4.0-21-generic 4.4.0-21.37
4.4.0-22-generic 4.4.0-22.40
4.4.0-24-generic 4.4.0-24.43
4.4.0-28-generic 4.4.0-28.47
4.4.0-31-generic 4.4.0-31.50
4.4.0-34-generic 4.4.0-34.53
4.4.0-36-generic 4.4.0-36.55
4.4.0-38-generic 4.4.0-38.57
4.4.0-42-generic 4.4.0-42.62
4.4.0-45-generic 4.4.0-45.66
4.4.0-47-generic 4.4.0-47.68
# list of different kernel versions:
4.4.0-47.68
4.4.0-45.66
4.4.0-42.62
4.4.0-38.57
4.4.0-36.55
4.4.0-34.53
4.4.0-31.50
4.4.0-28.47
4.4.0-24.43
4.4.0-22.40
4.4.0-21.37
# Installing kernel: 4.4.0-21.37 (4.4.0-21-generic)
# Running kernel: 4.4.0-45.66 (4.4.0-45-generic)
# Last kernel: 4.4.0-47.68
# Previous kernel: 4.4.0-45.66
# Kernel versions list to keep:
4.4.0-21.37
4.4.0-45.66
4.4.0-47.68
# Kernel packages (version part) to protect:
4\.4\.0-21-generic
4\.4\.0-45-generic
4\.4\.0-47-generic
*/

```

---

### Post by ian-weisser on 2016-11-26
Check your apt.daily timer for today to ensure you are not stepping on its toes.

1) Run the script /etc/kernel/postinst.d/apt-auto-removal (as sudo, of course)
Then check the debug information in[COLOR=#000000] /etc/apt/apt.conf.d/01autoremove-kernels again -- see if the script made any changes.[/COLOR][COLOR=#000000]
There will proabaly be no difference. If there is a difference, stop and show us.


2) Check the apt-marking. 
apt-mark showauto | grep linux-image
[/COLOR][COLOR=#000000]apt-mark showmanual | grep linux-image

[/COLOR][COLOR=#000000]Anything marked 'manual' cannot be autoremoved, regardless of what the script does. Change those to auto.
sudo apt-mark auto <packagename>

[/COLOR](Earlier, I said that the kernel/postinst script changes the apt-marking. *I was wrong* about that.)

3) Run the script /etc/kernel/postinst.d/apt-auto-removal (as sudo, of course)
Then check the debug information in[COLOR=#000000] /etc/apt/apt.conf.d/01autoremove-kernels again -- see if changing the apt-marking made any changes.
This time there may be a big change.

[/COLOR]

---

### Post by mossroy2 on 2016-11-26
Running apt-auto-removal was fast, but it made a few changes in [COLOR=#000000]/etc/apt/apt.conf.d/01autoremove-kernels[/COLOR]. See the new version :
```
/* Debug information:
# dpkg list:
rc  linux-image-4.4.0-21-generic               4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic               4.4.0-22.40                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic               4.4.0-34.53                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic               4.4.0-36.55                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic               4.4.0-38.57                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic               4.4.0-42.62                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic               4.4.0-45.66                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic               4.4.0-47.68                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic         4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic         4.4.0-47.68                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.47.50                                         amd64        Generic Linux kernel image
# list of installed kernel packages:
4.4.0-22-generic 4.4.0-22.40
4.4.0-24-generic 4.4.0-24.43
4.4.0-28-generic 4.4.0-28.47
4.4.0-31-generic 4.4.0-31.50
4.4.0-34-generic 4.4.0-34.53
4.4.0-36-generic 4.4.0-36.55
4.4.0-38-generic 4.4.0-38.57
4.4.0-42-generic 4.4.0-42.62
4.4.0-45-generic 4.4.0-45.66
4.4.0-47-generic 4.4.0-47.68
# list of different kernel versions:
4.4.0-47.68
4.4.0-45.66
4.4.0-42.62
4.4.0-38.57
4.4.0-36.55
4.4.0-34.53
4.4.0-31.50
4.4.0-28.47
4.4.0-24.43
4.4.0-22.40
# Installing kernel:  ()
# Running kernel: 4.4.0-47.68 (4.4.0-47-generic)
# Last kernel: 4.4.0-47.68
# Previous kernel: 4.4.0-45.66
# Kernel versions list to keep:
4.4.0-45.66
4.4.0-47.68
# Kernel packages (version part) to protect:
4\.4\.0-45-generic
4\.4\.0-47-generic
*/
```

I think it's simply because last update of the file was right before removing version 4.4.0-21, and before restarting to 4.4.0-47.

Let me know if I can follow your steps 2 and 3

---

### Post by ian-weisser on 2016-11-26
I agree with your assessment. Proceed.

---

### Post by mossroy2 on 2016-11-26
Step 2 :
```
$ sudo apt-mark showauto | grep linux-image
linux-image-4.4.0-47-generic
linux-image-extra-4.4.0-47-generic
linux-image-generic
$ sudo apt-mark showmanual | grep linux-image
linux-image-4.4.0-22-generic
linux-image-4.4.0-24-generic
linux-image-4.4.0-28-generic
linux-image-4.4.0-31-generic
linux-image-4.4.0-34-generic
linux-image-4.4.0-36-generic
linux-image-4.4.0-38-generic
linux-image-4.4.0-42-generic
linux-image-4.4.0-45-generic

```

So I ran :
```
sudo apt-mark auto linux-image-4.4.0-22-generic
linux-image-4.4.0-22-generic set to automatically installed.
```
Then step 3 :
```
sudo /etc/kernel/postinst.d/apt-auto-removal
```
/etc/apt/apt.conf.d/01autoremove-kernels has been touched by this command :```

sudo ls -al /etc/apt/apt.conf.d/01autoremove-kernels 
-r--r--r-- 1 root root 4155 nov.  26 17:22 /etc/apt/apt.conf.d/01autoremove-kernels
```
but its content is the same :
```
/* Debug information:
# dpkg list:
rc  linux-image-4.4.0-21-generic               4.4.0-21.37                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic               4.4.0-22.40                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic               4.4.0-34.53                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic               4.4.0-36.55                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic               4.4.0-38.57                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic               4.4.0-42.62                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic               4.4.0-45.66                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic               4.4.0-47.68                                          amd64        Linux kernel image for version  4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic         4.4.0-21.37                                          amd64        Linux kernel extra modules for  version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic         4.4.0-47.68                                          amd64        Linux kernel extra modules for  version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.47.50                                          amd64        Generic Linux kernel image
# list of installed kernel packages:
4.4.0-22-generic 4.4.0-22.40
4.4.0-24-generic 4.4.0-24.43
4.4.0-28-generic 4.4.0-28.47
4.4.0-31-generic 4.4.0-31.50
4.4.0-34-generic 4.4.0-34.53
4.4.0-36-generic 4.4.0-36.55
4.4.0-38-generic 4.4.0-38.57
4.4.0-42-generic 4.4.0-42.62
4.4.0-45-generic 4.4.0-45.66
4.4.0-47-generic 4.4.0-47.68
# list of different kernel versions:
4.4.0-47.68
4.4.0-45.66
4.4.0-42.62
4.4.0-38.57
4.4.0-36.55
4.4.0-34.53
4.4.0-31.50
4.4.0-28.47
4.4.0-24.43
4.4.0-22.40
# Installing kernel:  ()
# Running kernel: 4.4.0-47.68 (4.4.0-47-generic)
# Last kernel: 4.4.0-47.68
# Previous kernel: 4.4.0-45.66
# Kernel versions list to keep:
4.4.0-45.66
4.4.0-47.68
# Kernel packages (version part) to protect:
4\.4\.0-45-generic
4\.4\.0-47-generic
*/
```

Even if the apt-marking has worked :
```
$sudo apt-mark showauto | grep linux-image
linux-image-4.4.0-22-generic
linux-image-4.4.0-47-generic
linux-image-extra-4.4.0-47-generic
linux-image-generic

$sudo apt-mark showmanual | grep linux-image
linux-image-4.4.0-24-generic
linux-image-4.4.0-28-generic
linux-image-4.4.0-31-generic
linux-image-4.4.0-34-generic
linux-image-4.4.0-36-generic
linux-image-4.4.0-38-generic
linux-image-4.4.0-42-generic
linux-image-4.4.0-45-generic
```

---

### Post by mossroy2 on 2016-11-26
In between, let me thank you for the time you spend on that :)

---

### Post by ian-weisser on 2016-11-26
Your output is promising.
The -22 kernel now seems eligible for autoremoval.
When unattended-upgrade next runs, let's see if it autoremoves.

You need not wait 24 hours, you can run 'sudo unattended-upgrade' for testing.
You can also test it with an ordinary 'sudo apt autoremove'

---

### Post by mossroy2 on 2016-11-26
It worked : kernel 4.4.0-22 was autoremoved :
```
$ sudo unattended-upgrade -v
[sudo] password for test: 
Initial blacklisted packages: 
Initial whitelisted packages: 
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=xenial-security']
Packages that will be upgraded: 
Packages that are auto removed: 'linux-image-4.4.0-22-generic'
(Reading database ... 182067 files and directories currently installed.)
Removing linux-image-4.4.0-22-generic (4.4.0-22.40) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/vboxadd 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-24-generic
Found initrd image: /boot/initrd.img-4.4.0-24-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Packages were successfully auto-removed
```

And this kernel version does not take space any more on /boot.
That's good news : this is a working scenario.

Now I'm wondering why it did not work on my physical computers.
Unfortunately, I already manually removed all the kernels (except the  last 2) on my main computer (because /boot was full), so I won't be able  to diagnose on this one. I'll check the other ones.

---

### Post by ian-weisser on 2016-11-26
Very glad your test case works.

In the few instances I have seen where some record of the problems survives the solution,
either the unremoved packages were apt-marked 'manual'.
or the related kernel headers were apt-marked manual,
or unattended-upgrade was prevented from running by a setting in /etc/apt/apt.conf.d/20auto-upgrades,
or apt was blocked by a sometimes-unrelated problem (out-of-space, package conflict, unconfigured packages).

---

### Post by mossroy2 on 2016-11-26
Thanks again for your help.
This has been very useful for me to understand how this works. And now I know a few ways to diagnose.

For my main computer, I suspect it might come from the fact that I disabled the automatic installation of security updates. I like to know what's going to be installed on my computer and to choose when it is installed. So, in the update settings, I think I had set the security updates to "Download only" instead of "Download and install automatically". I thought that manually installing the updates (through the updates GUI) would have the same effect.
If I understood correctly, I was wrong : setting this to "download only" disables unattended-upgrades (I suppose, based on [https://help.ubuntu.com/community/RemoveOldKernels#GUI_Way](https://help.ubuntu.com/community/RemoveOldKernels#GUI_Way)), so the automatic removal was never triggered.

In other words, the automatic removal of old kernels on Ubuntu 16.04 only works if you set the security updates to "Download and install automatically" ? (which is the default setting on a new installation of Ubuntu 16.04)

Do you confirm?

---

### Post by ian-weisser on 2016-11-26
A good hypothesis. Let's try it...

The design of unattended-upgrade is that it queues transactions with aptdaemon. If it runs and discovers nothing to upgrade, it queues nothing, logs, and quits.
Since 16.04, on additional piece of logic checks for the presence of present but autoremovable packages at application startup. If present, they are queued for autoremoval. The check and autoremoval will even if no other action is queued.

I ran a fresh-install of 16.10 in a VM to test it.
On my test, /etc/apt/apt.conf.d/20auto-upgrades shows the default setting of unattended-upgrade is 'enabled'.
In theory, unattended-upgrade should be run (by the apt.daily script) once each day.

When I have time, I will revist the apt.daily script.

---

### Post by mossroy2 on 2016-11-30
Hi ian-weisser,

I'm not clear on the status of our investigations.
Did you come to a conclusion regarding my hypothesis?
Should I run some other tests to help?

---

### Post by Jarno_Suni on 2016-12-13
> **mossroy2 said:**
> Thanks again for your help.
In other words, the automatic removal of old kernels on Ubuntu 16.04 only works if you set the security updates to "Download and install automatically" ? (which is the default setting on a new installation of Ubuntu 16.04)

Do you confirm?

Yes, it is told in the community document.
If you use [https://help.ubuntu.com/community/RemoveOldKernels#Option_for_All_Ubuntu_Releases](https://help.ubuntu.com/community/RemoveOldKernels#Option_for_All_Ubuntu_Releases), you could  edit /etc/apt/apt.conf.d/50unattended-upgrades and disable all Allowed-Origins, so that nothing would be actually installed automatically, but unattended-upgrade would still remove excessive stuff automatically, if I have understood correctly.

---

### Post by mossroy2 on 2016-12-18
Thanks a lot for your answers and suggestions.

Now that I understood that, I would suggest a few things :
- make it more clear for the end-user that disabling automatic installation of updates in the GUI will also disable the automatic removal of old kernels. The end-user should be aware that it might force him to remove the old kernels manually if /boot is in a separate small partition (which can be risky if he does not know how to do it).
In my case, I did not make the link between the GUI options and the unattended-upgrades package.
- the status of [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093) is misleading : as a "fix released", people think this can not happen any more (it's what I thought). Maybe we could simply state there in which precise conditions it is "working" or not
- ideally, I think it would be better that the 2 features (automatic installation of security updates, and automatic removal of old kernels) would not be linked. And that, by default, old kernels are always removed.

What's your opinion?
I'd be glad to help on that : tell me if I can (by opening other bug(s) for example?)

---

### Post by ian-weisser on 2016-12-18
A recent improvement to LVM means that you can soon use LVM to boot. Eliminating the out-of-space problems on /boot partitions by getting rid of the partition.

Also, the original purpose of pestering users to pay attention to each upgrade has been fairly mooted over the past decade of improvement in systematic CI, automated testing, Phased Updates, Snappy's A/B architecture etc. I expect update-notifier and update-manager will be rethought sometime in the next couple years, and the defaults move toward unattended background upgrades. You will need to opt-in to get notifications.  

LP# 1357093 does have a clear explanation of what is fixed, why, and how in the bug comments. Also explained is why the fix won't be backported to 14.04. The patch to fix LP# 1357093 really did eliminate the problem for most users. Not the way I would have, but admittedly effectively for most.

Personally, I think that failure to autoremove old kernels is a problem with apt design, not a feature appropriate for unattended-upgrade. Discussion is more appropriate for a mailing list than a bug report. For example, apt or aptdaemon could catch the out-of-space error and handle it several ways instead of dumping the error onto the user. However, I'm also unwilling to invest the amount of time and effort required to get it differently fixed this year or next. Anyone with C experience can hack at apt. Anyone with Python3 experience can hack at aptdaemon. All the code is on Launchpad.

---

### Post by mossroy2 on 2016-12-19
Thanks for your answer.

About LVM, that looks like good news, but will it apply to encrypted partitions? That would mean the boot-loader would be LUKS/dm-crypt-aware, and ask for the passphrase before starting the kernel??
If not, the problem will remain for people activating full-disk encryption at install time.

---

### Post by ian-weisser on 2016-12-19
One problem at a time...

---

### Post by trimmer on 2016-12-21
I want to thank this threads participants for the thorough discussion and testing. This has been a troublesome topic for me for a long time. I am going to eliminate the scripts I implemented to take care of this daunting task and attempt to do it the right way.

---

### Post by jon114 on 2016-12-22
Posting here as this thread is displayed as the top result for the out of disk space in /boot error when trying to install updates. I know this thread is for those discussing the means of fixing the problem but for other noobs trying to get their system working again I didn't find a lot of other advice.
I also got the message telling me there was insufficient disk space in /boot to install the latest updates when trying to do an auto update and that I should try sudo apt-get autoclean to make more room.
Autoclean did nothing but after reading through this thread I tried sudo apt autoremove and restarted the update which completed succesfully.
Out of interest this occurred on a laptop running a fresh install of 16.04 LTS that has only ever had auto updates, no manual updates or installs of any kind.
Maybe someone can do a basic "how to fix" sticky, if it happened to me it will happen to others also.
Thanks all.

---

### Post by ian-weisser on 2016-12-22
> **jon114 said:**
> Out of interest this occurred on a laptop running a fresh install of 16.04 LTS that has only ever had auto updates, no manual updates or installs of any kind.
Well, several different problems may cause an out-of-space condition.
No single, easy solution fixes all the possible problems.
The sticky may be complicated and confusing. For an example, see [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

The most common cause was fixed for most users...in 16.04.

---

### Post by jon114 on 2016-12-22
> **ian-weisser said:**
> ...The sticky may be complicated and confusing. 

Hi Ian and thanks for your reply and yes I agree it may be but so is the existing situation and if I'm honest if the first 2 options from the link you supplied didn't work I would be stumped and wouldn't have got any further.

> **ian-weisser said:**
> ...The most common cause was fixed for most users...In 16.04. 

 But I am using 16.04LTS so the problem still exists.

---

### Post by ian-weisser on 2016-12-22
> **jon114 said:**
> But I am using 16.04LTS so the problem still exists.
Exactly
Several different issues can cause an out-of-space condition.
You seem to be assuming that you have a frequent cause among those several.
I think your problem has a fairly rare and unusual cause, because we fixed those frequent causes.

You should open a new thread so we can start your troubleshooting at the beginning.
It's not fair to the original thread author, nor to other help-seekers, to have a different problem appear in mid-stream.

---

