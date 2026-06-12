---
title: "Failed to lock /var/cache/apt/archives/lock"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by anbu-s on 2016-10-17
When I tried to upgrade from ubuntu 16.04 to 16.10, it started downloading all packages - but my internet connection went down half way through.
I've rebooted the machines and tried again and getting this error

Failed to lock /var/cache/apt/archives/lock

Tried to remove the lock file and kill all the apt processes as described in this thread - but the error still persists
[http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

It removes the lock file. But when i run the upgrade again, it gives the same failed to lock message

How do i solve this?

Appreciate your help on this.

---

### Post by kc1di on 2016-10-18
try this in the terminal ```
sudo apt-get autoclean && sudo apt-get clean
```
Then run ```
sudo apt-get update
```
and try again. 
If that does not work
do the following

```
sudo dpkg --configue -a
```

and try again. 

if all that fails do this and try again. 
```
sudo rm /var/lib/apt/lists/lock
```
```
sudo rm /var/cache/apt/archives/lock
```

Good Luck

---

### Post by mikecroall on 2016-10-18
I'm experiencing the same problem. I have tried all of the above but to no avail. Are there any other possibilities?

---

### Post by kc1di on 2016-10-18
It usually means you have another package manager running in the background. 
you could try going to the  task manager and try to stop them.  It would either be synaptic, software installer , or update manager or another instance of apt running.
I'm assuming you have rebooted since this all started also. if not do so.

---

### Post by anbu-s on 2016-10-18
> **kc1di said:**
> try this in the terminal ```
sudo apt-get autoclean && sudo apt-get clean
```
Then run ```
sudo apt-get update
```
and try again. 
If that does not work
do the following

```
sudo dpkg --configue -a
```

and try again. 

if all that fails do this and try again. 
```
sudo rm /var/lib/apt/lists/lock
```
```
sudo rm /var/cache/apt/archives/lock
```

Good Luck

I tried all the steps above - it seem to have downloaded all the packages this time about 2200 of them. But then it fails with the exact same error msg. There is no other update program like synoptic or anything is running. Its really bugging me. I've tried rebooting many times and repeating the same procedure. It fails after dwonloading packages.
Not sure what else to do.

---

### Post by Bashing-om on 2016-10-18
anbu-sl Hello;

In this instance is is now, let us suppose that apt's control files are corrupt.
Now try:
 to initialize the package information:::
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

[INDENT][INDENT][INDENT]maybe Yes
[/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-19
> **Bashing-om said:**
> anbu-sl Hello;

In this instance is is now, let us suppose that apt's control files are corrupt.
Now try:
 to initialize the package information:::
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.
[INDENT][INDENT][INDENT]maybe Yes
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for your reply
I've run all these commands and then tried to do the upgrade by this command

sudo do-release-upgrade

Then got the same failed to lock message. Did the above command redo the lists and creating this issue?
How do i do the upgrade after the lists of commands you've mentioned?

---

### Post by Bashing-om on 2016-10-20
anbu-s; Well, well Not .

Let's make sure the package manager is in a consistent state.
Post back the outputs :
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-20
Here are the results:
```

anbu@Terminatore:~$ sudo apt update
[sudo] password for anbu: 
Hit:1 http://ca.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease
Hit:3 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease       
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:5 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Fetched 94.5 kB in 0s (100 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
anbu@Terminatore:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gir1.2-geoclue-2.0 libcue1 libgail-common:i386 libgail18:i386 libiptcdata0
  libosinfo-1.0-0 linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic
  linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-signed-image-4.4.0-36-generic linux-signed-image-4.4.0-38-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic
  linux-image-4.4.0-45-generic linux-image-extra-4.4.0-45-generic
  linux-signed-image-4.4.0-45-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  linux-signed-generic linux-signed-image-generic
6 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.4 MB of archives.
After this operation, 296 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-45-generic amd64 4.4.0-45.66 [18.8 MB]
Get:2 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-45-generic amd64 4.4.0-45.66 [39.0 MB]
Get:3 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.45.48 [1,788 B]
Get:4 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.45.48 [2,312 B]
Get:5 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-image-4.4.0-45-generic amd64 4.4.0-45.66 [3,992 B]
Get:6 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-generic amd64 4.4.0.45.48 [1,822 B]
Get:7 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-signed-image-generic amd64 4.4.0.45.48 [2,350 B]
Get:8 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-45 all 4.4.0-45.66 [9,988 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-45-generic amd64 4.4.0-45.66 [783 kB]
Get:10 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.45.48 [2,280 B]
Get:11 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-45.66 [839 kB]
Fetched 69.4 MB in 1min 31s (759 kB/s)                                         
Selecting previously unselected package linux-image-4.4.0-45-generic.
(Reading database ... 589196 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-45-generic_4.4.0-45.66_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Selecting previously unselected package linux-image-extra-4.4.0-45-generic.
Preparing to unpack .../linux-image-extra-4.4.0-45-generic_4.4.0-45.66_amd64.deb ...
Unpacking linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
Preparing to unpack .../linux-generic_4.4.0.45.48_amd64.deb ...
Unpacking linux-generic (4.4.0.45.48) over (4.4.0.43.45) ...
Preparing to unpack .../linux-image-generic_4.4.0.45.48_amd64.deb ...
Unpacking linux-image-generic (4.4.0.45.48) over (4.4.0.43.45) ...
Selecting previously unselected package linux-signed-image-4.4.0-45-generic.
Preparing to unpack .../linux-signed-image-4.4.0-45-generic_4.4.0-45.66_amd64.deb ...
Unpacking linux-signed-image-4.4.0-45-generic (4.4.0-45.66) ...
Preparing to unpack .../linux-signed-generic_4.4.0.45.48_amd64.deb ...
Unpacking linux-signed-generic (4.4.0.45.48) over (4.4.0.43.45) ...
Preparing to unpack .../linux-signed-image-generic_4.4.0.45.48_amd64.deb ...
Unpacking linux-signed-image-generic (4.4.0.45.48) over (4.4.0.43.45) ...
Selecting previously unselected package linux-headers-4.4.0-45.
Preparing to unpack .../linux-headers-4.4.0-45_4.4.0-45.66_all.deb ...
Unpacking linux-headers-4.4.0-45 (4.4.0-45.66) ...
Selecting previously unselected package linux-headers-4.4.0-45-generic.
Preparing to unpack .../linux-headers-4.4.0-45-generic_4.4.0-45.66_amd64.deb ...
Unpacking linux-headers-4.4.0-45-generic (4.4.0-45.66) ...
Preparing to unpack .../linux-headers-generic_4.4.0.45.48_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.45.48) over (4.4.0.43.45) ...
Preparing to unpack .../linux-libc-dev_4.4.0-45.66_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-45.66) over (4.4.0-43.63) ...
Setting up linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-4.4.0-45-generic (4.4.0-45.66) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (4.4.0.45.48) ...
Setting up linux-headers-4.4.0-45 (4.4.0-45.66) ...
Setting up linux-headers-4.4.0-45-generic (4.4.0-45.66) ...
Setting up linux-headers-generic (4.4.0.45.48) ...
Setting up linux-generic (4.4.0.45.48) ...
Setting up linux-signed-image-4.4.0-45-generic (4.4.0-45.66) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-generic (4.4.0.45.48) ...
Setting up linux-signed-generic (4.4.0.45.48) ...
Setting up linux-libc-dev:amd64 (4.4.0-45.66) ...
anbu@Terminatore:~$ sudo apf -f install
sudo: apf: command not found
anbu@Terminatore:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-geoclue-2.0 libcue1 libgail-common:i386 libgail18:i386 libiptcdata0
  libosinfo-1.0-0 linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic
  linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anbu@Terminatore:~$ sudo dpkg -C
anbu@Terminatore:~$ cat -n /ec/apt/sources.list
cat: /ec/apt/sources.list: No such file or directory
anbu@Terminatore:~$ cat -n /etc/apt/sources.list
     1    
     2    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3    # newer versions of the distribution.
     4    deb http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted
     5    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    10    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb http://ca.archive.ubuntu.com/ubuntu/ xenial universe
    16    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial universe
    17    deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe
    18    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
    26    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
    27    deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    28    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    deb http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    36    deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    37    
    38    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    39    deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    40    deb http://security.ubuntu.com/ubuntu xenial-security universe
    41    deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    42    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    43    deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    44    
    45    ## Uncomment the following two lines to add software from Canonical's
    46    ## 'partner' repository.
    47    ## This software is not part of Ubuntu, but is offered by Canonical and the
    48    ## respective vendors as a service to Ubuntu users.
    49    deb http://archive.canonical.com/ubuntu xenial partner
    50    deb-src http://archive.canonical.com/ubuntu xenial partner
anbu@Terminatore:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-staging-xenial.list <==
# deb http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial main

==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-staging-xenial.list.distUpgrade <==
# deb http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to yakkety

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 

==> /etc/apt/sources.list.d/mjblenner-ubuntu-ppa-hal-vivid.list <==
# deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu vivid main

==> /etc/apt/sources.list.d/mjblenner-ubuntu-ppa-hal-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu vivid main

==> /etc/apt/sources.list.d/mjblenner-ubuntu-ppa-hal-vivid.list.save <==
# deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu vivid main

==> /etc/apt/sources.list.d/nylas.list <==
# deb [arch=i386,amd64] http://apt.nylas.com/ubuntu vivid main

==> /etc/apt/sources.list.d/nylas.list.distUpgrade <==
# deb [arch=i386,amd64] http://apt.nylas.com/ubuntu vivid main

==> /etc/apt/sources.list.d/nylas.list.save <==
# deb [arch=i386,amd64] http://apt.nylas.com/ubuntu vivid main

==> /etc/apt/sources.list.d/owncloud.list <==
# deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_15.04/ / # disabled on upgrade to wily

==> /etc/apt/sources.list.d/owncloud.list.distUpgrade <==
# deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_15.04/ / # disabled on upgrade to wily

==> /etc/apt/sources.list.d/owncloud.list.save <==
# deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_15.04/ / # disabled on upgrade to wily

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list.save <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-vivid.list <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu vivid main

==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-vivid.list.save <==
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu vivid main
anbu@Terminatore:~$ 



```

---

### Post by Bashing-om on 2016-10-21
anbu-s; Hey ! Hey;

Look'n good - so far :
Your 3rd party PPAs - as you are aware - are disabled with the exception of google-chrome.
For now that is a good thing . 
What now results :
```

sudo apt autoremove

```
with this we clean things up and remove a lot of clutter ( free up a lot of disk space ) .
With the hope and expectation that those older kernels are removed form the system.

[INDENT][INDENT]keep it clean behind us
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
Bashing-Om;
Thanks for the reply. I;ll post the results of the autoremove command as soon as i get home in a few hours.

Should I wait for your analysis after i run the autoremove. Or something i could try for upgrading to 16.10?

---

### Post by Bashing-om on 2016-10-21
anbu-s; Well ..

Yeah be good to see the results of 'auto-remove' . Making things as clean as possible will aid the update-manager .
Also want any proprietary drivers reverted to open source prior to doing the release-upgrade to 16.10 .
( you do realize that 16.10 only has support for 9 months ? whereas the current 14.04 is a Long_Term_Support release .. 14.04 'til April of 2019 )

in all things I follow
[INDENT][INDENT][INDENT]KISS principles
[/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
Here is the output of auto remove

```

anbu@Terminatore:~$ sudo apt  autoremove
[sudo] password for anbu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-geoclue-2.0 libcue1 libgail-common:i386 libgail18:i386 libiptcdata0
  libosinfo-1.0-0 linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic
  linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
0 upgraded, 0 newly installed, 21 to remove and 2 not upgraded.
After this operation, 889 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 621430 files and directories currently installed.)
Removing gir1.2-geoclue-2.0:amd64 (2.4.1-1) ...
Removing libcue1 (1.4.0-1) ...
Removing libgail-common:i386 (2.24.30-1ubuntu1) ...
Removing libgail18:i386 (2.24.30-1ubuntu1) ...
Removing libiptcdata0 (1.0.4-4ubuntu1) ...
Removing libosinfo-1.0-0:amd64 (0.2.12-2ubuntu3) ...
Removing linux-headers-4.4.0-36-generic (4.4.0-36.55) ...
Removing linux-headers-4.4.0-36 (4.4.0-36.55) ...
Removing linux-headers-4.4.0-38-generic (4.4.0-38.57) ...
Removing linux-headers-4.4.0-38 (4.4.0-38.57) ...
Removing linux-headers-4.4.0-42-generic (4.4.0-42.62) ...
Removing linux-headers-4.4.0-42 (4.4.0-42.62) ...
Removing linux-signed-image-4.4.0-36-generic (4.4.0-36.55) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-signed-image-4.4.0-38-generic (4.4.0-38.57) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-signed-image-4.4.0-42-generic (4.4.0-42.62) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Processing triggers for libc-bin (2.23-0ubuntu3) ...
anbu@Terminatore:~$ 




```

---

### Post by Bashing-om on 2016-10-21
anbu-s; Yepper,

That too looks good .. shinning like a new penny thus far .

Next is to check what kernels remain ( and the status ) :
```

dpkg -l | grep linux-

```
( I do anticipate that config files are still present we want to remove )

And verify that it is the open source graphic's driver in use:
```

sudo lshw -C display

```

[INDENT][INDENT]getting closer
[INDENT][INDENT][INDENT]to pulling the trigger
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
Bashing-OM;

Here is the output

```

anbu@Terminatore:~$ dpkg -l | grep linux-
ii  linux-base                                    4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                1.157.4                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                 4.4.0.45.48                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-22                       3.19.0-22.22                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-22-generic               3.19.0-22.22                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-23                       3.19.0-23.24                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-23-generic               3.19.0-23.24                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25                       3.19.0-25.26                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic               3.19.0-25.26                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                       3.19.0-26.28                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic               3.19.0-26.28                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                       3.19.0-28.30                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic               3.19.0-28.30                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                       3.19.0-30.34                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic               3.19.0-30.34                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                       3.19.0-31.36                                  all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic               3.19.0-31.36                                  amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-43                        4.4.0-43.63                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                        4.4.0-45.66                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.45.48                                   amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-15-generic                 3.19.0-15.15                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                 3.19.0-22.22                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-23-generic                 3.19.0-23.24                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-25-generic                 3.19.0-25.26                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                 3.19.0-26.28                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                 3.19.0-28.30                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                 3.19.0-30.34                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                 3.19.0-31.36                                  amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-18-generic                  4.2.0-18.22                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-19-generic                  4.2.0-19.23                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-22-generic                  4.2.0-22.27                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-23-generic                  4.2.0-23.28                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-25-generic                  4.2.0-25.30                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                  4.2.0-27.32                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-30-generic                  4.2.0-30.36                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic                  4.2.0-34.39                                   amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic                  4.4.0-36.55                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-43-generic                  4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                  4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic           3.19.0-15.15                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic           3.19.0-22.22                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-23-generic           3.19.0-23.24                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic           3.19.0-25.26                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic           3.19.0-26.28                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic           3.19.0-28.30                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic           3.19.0-30.34                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic           3.19.0-31.36                                  amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-18-generic            4.2.0-18.22                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic            4.2.0-19.23                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-22-generic            4.2.0-22.27                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-23-generic            4.2.0-23.28                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-25-generic            4.2.0-25.30                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic            4.2.0-27.32                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic            4.2.0-30.36                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic            4.2.0-34.39                                   amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic            4.4.0-36.55                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-43-generic            4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic            4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.45.48                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-45.66                                   amd64        Linux Kernel Headers for development
ii  linux-signed-generic                          4.4.0.45.48                                   amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.19.0-15-generic          3.19.0-15.15                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-22-generic          3.19.0-22.22                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-23-generic          3.19.0-23.24                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-25-generic          3.19.0-25.26                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-26-generic          3.19.0-26.28                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-28-generic          3.19.0-28.30                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-30-generic          3.19.0-30.34                                  amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-31-generic          3.19.0-31.36                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-18-generic           4.2.0-18.22                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-19-generic           4.2.0-19.23                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-22-generic           4.2.0-22.27                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-23-generic           4.2.0-23.28                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-25-generic           4.2.0-25.30                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-27-generic           4.2.0-27.32                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-30-generic           4.2.0-30.36                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.2.0-34-generic           4.2.0-34.39                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-34-generic           4.4.0-34.53                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-36-generic           4.4.0-36.55                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-38-generic           4.4.0-38.57                                   amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-42-generic           4.4.0-42.62                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-43-generic           4.4.0-43.63                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-45-generic           4.4.0-45.66                                   amd64        Signed kernel image generic
ii  linux-signed-image-generic                    4.4.0.45.48                                   amd64        Signed Generic Linux kernel image
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
anbu@Terminatore:~$ sudo lshw -C display
[sudo] password for anbu: 
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
anbu@Terminatore:~$ 


```

---

### Post by Bashing-om on 2016-10-21
anbu-s; Welp ...

That ain't good .. I do not know why 'autoremove' did not remove those old kernels.
Ya up for manually removing them ?
No big deal, just tedious .

The good thing, however, is that the graphic's is Intel .. and the kernel will take care of it. No sweat on out parts .

[INDENT][INDENT]keep'n it clean
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
Bashing-om;
Sure. how do i remove them manually? Please send me the commands.

---

### Post by Bashing-om on 2016-10-21
anbu-s; Ho kay !


Looking at what there is to do manually I see a hint here of why 'autoremove" did not complete.

Let us take a gentle poke at removing kernels - a single shot:
```

sudo apt purge linux-signed-image-3.19.0-22-generic
sudo apt purge linux-image-3.19.0-22-generic
sudo apt purge linux-headers-3.19.0-22-generic
sudo apt purge linux-headers-3.19.0-22
sudo apt purge linux-image-extra-3.19.0-22-generic

```
If these go well we take a shotgun approach to the other kernels and batch remove them .

easy does it
[INDENT][INDENT]careful is no mistake
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
all remove commands worked except for the last one - couldn't find linux-image-extra-3.19.0-22-generic
```

anbu@Terminatore:~$ sudo apt purge linux-signed-image-3.19.0-22-generic
[sudo] password for anbu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-signed-image-3.19.0-22-generic*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 38.9 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 524653 files and directories currently installed.)
Removing linux-signed-image-3.19.0-22-generic (3.19.0-22.22) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.19.0-22-generic (3.19.0-22.22) ...
anbu@Terminatore:~$ sudo apt purge linux-image-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.19.0-22-generic* linux-image-extra-3.19.0-22-generic*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 208 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 524649 files and directories currently installed.)
Removing linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
Removing linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.19.0-22-generic (3.19.0-22.22) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
anbu@Terminatore:~$ sudo apt purge linux-headers-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-22-generic*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 14.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 519426 files and directories currently installed.)
Removing linux-headers-3.19.0-22-generic (3.19.0-22.22) ...
anbu@Terminatore:~$ sudo apt purge linux-headers-3.19.0-22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-22*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 66.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 510290 files and directories currently installed.)
Removing linux-headers-3.19.0-22 (3.19.0-22.22) ...
anbu@Terminatore:~$ sudo apt purge linux-image-extra-3.19.0-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-extra-3.19.0-22-generic
E: Couldn't find any package by glob 'linux-image-extra-3.19.0-22-generic'
E: Couldn't find any package by regex 'linux-image-extra-3.19.0-22-generic'
anbu@Terminatore:~$ ^C
anbu@Terminatore:~$ 


```

---

### Post by Bashing-om on 2016-10-21
anbu-s; Humm ...

Not real sure what to make of:
> 
E: Couldn't find any package by glob 'linux-image-extra-3.19.0-22-generic'

As it is clearly installed per:
> 
ii  linux-image-3.19.0-22-generic


Before "shotgunning" the other kernels, let's make sure we do not mess with whatever kernel you are booting presently:
Show us the output of terminal command:
```

uname -r

```

And we proceed on .

[INDENT][INDENT]slowly
[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
Bashing-om;

anbu@Terminatore:~$ uname -r
4.4.0-45-generic

---

### Post by Bashing-om on 2016-10-21
anbu-s; Ho Kay ..

Moving right merrily on:
```

sudo dpkg -P linux-signed-image-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-image-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-headers-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-headers-3.19.0-{23,25,26,28,30,31}
sudo dpkg -P linux-image-extra-3.19.0-{23,25,26,28,30,31}-generic

```

when these complete we next do the 4.4 series .
Keeping in mind we must no mess with the -45 kernel, and we want to keep the -43 kernel as the backup.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-21
> **Bashing-om said:**
> anbu-s; Ho Kay ..

Moving right merrily on:
```

sudo dpkg -P linux-signed-image-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-image-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-headers-3.19.0-{23,25,26,28,30,31}-generic
sudo dpkg -P linux-headers-3.19.0-{23,25,26,28,30,31}
sudo dpkg -P linux-image-extra-3.19.0-{23,25,26,28,30,31}-generic

```

when these complete we next do the 4.4 series .
Keeping in mind we must no mess with the -45 kernel, and we want to keep the -43 kernel as the backup.
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]


All done. they ran successfully. 

Next please, appreciate all your help

---

### Post by Bashing-om on 2016-10-22
anbu-s; Outstanding !

On a 3rd look, I like the 4.4 series kernels just as is .
Let's clean up all those old kernels with the mark 'rc' :
( -R-emoved but -C-onfig files remain )
run:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Before hitting that YES, pay close attention to what all is going to be removed .. yeah a whole bunch - have some idea of what is going to be removed in the event that the package manager has gotten carried away with it's self . I have never known such a thing to happen .. but there is that possibility .

Now what have we ?
show a new:
```

dpkg -l | grep linux-

```

[INDENT][INDENT]Try'n not to smash no fingers
[INDENT][INDENT][INDENT]before we let the hammer down
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-22
Bashing-om;

that ran successfully
here is the output:
```

anbu@Terminatore:~$ dpkg -l|grep linux-
ii  linux-base                                    4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                1.157.4                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                 4.4.0.45.48                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-43                        4.4.0-43.63                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                        4.4.0-45.66                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.45.48                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-43-generic                  4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                  4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-43-generic            4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic            4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.45.48                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-45.66                                   amd64        Linux Kernel Headers for development
ii  linux-signed-generic                          4.4.0.45.48                                   amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.4.0-43-generic           4.4.0-43.63                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-45-generic           4.4.0-45.66                                   amd64        Signed kernel image generic
ii  linux-signed-image-generic                    4.4.0.45.48                                   amd64        Signed Generic Linux kernel image
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
anbu@Terminatore:~$ 

```

---

### Post by Bashing-om on 2016-10-22
anbu-s; Hey ,,,

Almost there .

what now is set for the release-upgrade path ?
show:
```

grep Prompt= /etc/update-manager/release-upgrades

```

[INDENT][INDENT]I think I can, I think I can
[INDENT][INDENT]I think I can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-22
```

anbu@Terminatore:~$ grep Prompt= /etc/update-manager/release-upgrades
Prompt=normal
anbu@Terminatore:~$ 


```

---

### Post by Bashing-om on 2016-10-22
anbu-s; Uh HUH ...

That to is correct !
Ready to pull the trigger ?

do:
```

sudo apt update
sudo apt full-upgrade
sudo do-release-upgrade

```
see what yaketty looks like .

[INDENT][INDENT]did we do good,
[INDENT][INDENT][INDENT]or what
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-22
Bashing-om;

Thanks for all your help man. Appreciate it very much

I'm still getting the same failed to unlock error when i try the upgrade command (i cut out the other output results as they're too long.
```

checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


8 installed packages are no longer supported by Canonical. You can 
still get support from the community. 

22 packages are going to be removed. 189 new packages are going to be 
installed. 2232 packages are going to be upgraded. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]y

Fetching
Fetched 0 B in 0s (0 B/s)                                                      

Upgrading

Could not download the upgrades 

The upgrade has aborted. Please check your Internet connection or 
installation media and try again. 

Failed to lock /var/cache/apt/archives/lock 


Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/yakkety", line 8, in <module>
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeMain.py", line 242, in main
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1880, in run
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1845, in fullUpgrade
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1263, in doDistUpgrade
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1385, in abort
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/sourceslist.py", line 366, in restore_backup
  File "/usr/lib/python3.5/shutil.py", line 236, in copy
    copymode(src, dst, follow_symlinks=follow_symlinks)
  File "/usr/lib/python3.5/shutil.py", line 138, in copymode
    chmod_func(dst, stat.S_IMODE(st.st_mode))
PermissionError: [Errno 1] Operation not permitted: '/etc/apt/sources.list'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 109, in apport_excepthook
    pr.add_proc_info(extraenv=['PYTHONPATH', 'PYTHONHOME'])
  File "/usr/lib/python3/dist-packages/apport/report.py", line 544, in add_proc_info
    self['ExecutableTimestamp'] = str(int(os.stat(self['ExecutablePath']).st_mtime))
PermissionError: [Errno 13] Permission denied: '/tmp/ubuntu-release-upgrader-3tllb4h2/yakkety'

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/yakkety", line 8, in <module>
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeMain.py", line 242, in main
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1880, in run
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1845, in fullUpgrade
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1263, in doDistUpgrade
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py", line 1385, in abort
  File "/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/sourceslist.py", line 366, in restore_backup
  File "/usr/lib/python3.5/shutil.py", line 236, in copy
    copymode(src, dst, follow_symlinks=follow_symlinks)
  File "/usr/lib/python3.5/shutil.py", line 138, in copymode
    chmod_func(dst, stat.S_IMODE(st.st_mode))
PermissionError: [Errno 1] Operation not permitted: '/etc/apt/sources.list'
anbu@Terminatore:~$ 

```

---

### Post by Bashing-om on 2016-10-22
anbu-sl Yuk !

Looks like we are going to have to dig deep:
> 
PermissionError: [Errno 13] Permission denied: '/tmp/ubuntu-release-upgrader-3tllb4h2/yakkety'

find out what " ubuntu-release-upgrader-3tllb4h2/yakkety " is all about .

[INDENT][INDENT]homework time
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-22
I'll look around. Not much info on the internet on this particualr error message. May be i should just stick with 16.04LTS!!

---

### Post by Bashing-om on 2016-10-23
anbu-s; Hummm ..

My research points to "Package python3-distupgrade" . Maybe we have to return to this .

Look, my python coding skills are non-existent, but, maybe we can follow the error condition's bread crumbs and try and find where the fault lies.
Does the file still exist ?
What returns:
```

ls -al  /tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py

```
If the file exits, what now returns:
```

file /tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py

```
where I hope we see: "  Python script, ASCII text executable " .

Then we can take a stab at trying to read and comprehend the scrip to see where lies the fault.

[INDENT][INDENT]try and read the instructions
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-10-25
A similar python error should occur if a lock cannot be created.
So it's likely just a different error for the apt lock.

Unattended-upgrades runs daily under 16.04, and locks apt during it's run.
Try again in a few minutes.
If the lock error persists, run the 'ps -e' command, and check that apt, unattended-upgrades, Software Center, Synaptic, and others are not running.
If not, then remove the locks using sudo like you did before.
Then check apt function with 'sudo apt update && sudo apt-upgrade'
If apt is functioning, then run 'do-release-upgrade'

---

### Post by Bashing-om on 2016-10-25
Oh Ian !!

That ^ is great to know .. Thank you !

[INDENT][INDENT]in that process of learning
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-26
> **Bashing-om said:**
> anbu-s; Hummm ..

My research points to "Package python3-distupgrade" . Maybe we have to return to this .

Look, my python coding skills are non-existent, but, maybe we can follow the error condition's bread crumbs and try and find where the fault lies.
Does the file still exist ?
What returns:
```

ls -al  /tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py

```
If the file exits, what now returns:
```

file /tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py

```
where I hope we see: "  Python script, ASCII text executable " .

Then we can take a stab at trying to read and comprehend the scrip to see where lies the fault.[INDENT][INDENT]try and read the instructions
[/INDENT]
[/INDENT]


The lock error still persists after multiple restarts

here is the output for ls command - the file doesn't exist

```

anbu@Terminatore:~$ ls -al  /tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py
ls: cannot access '/tmp/ubuntu-release-upgrader-3tllb4h2/DistUpgrade/DistUpgradeController.py': No such file or directory
anbu@Terminatore:~$ 

```

I tried this with the latest error msg

```

anbu@Terminatore:~$ sudo ls -al /tmp/ubuntu-release-upgrader-fldrkqbh/DistUpgrade/DistUpgradeController.py
-rw-r--r-- 1 root root 92487 Aug 10 09:04 /tmp/ubuntu-release-upgrader-fldrkqbh/DistUpgrade/DistUpgradeController.py

anbu@Terminatore:~$ sudo file /tmp/ubuntu-release-upgrader-fldrkqbh/DistUpgrade/DistUpgradeController.py
/tmp/ubuntu-release-upgrader-fldrkqbh/DistUpgrade/DistUpgradeController.py: Python script, ASCII text executable

```

---

### Post by Bashing-om on 2016-10-26
anbu-s; Yuk;

dealing with a file size of " 92487 "  is a lot more than we can deal with .

Did you do Ian's instructions from post 33 ?
```

ps -e | grep apt
ps -e | grep unattended-upgrades
ps -e | grep software-center
ps -e | grep synaptic

```

> 
If not, then remove the locks using sudo like you did before.
Then check apt function with 'sudo apt update && sudo apt-upgrade'
If apt is functioning, then run 'do-release-upgrade'


And what are the exact results ?

[INDENT][INDENT]back up and regroup
[/INDENT][/INDENT]

---

### Post by anbu-s on 2016-10-26
> **Bashing-om said:**
> anbu-s; Yuk;

dealing with a file size of " 92487 "  is a lot more than we can deal with .

Did you do Ian's instructions from post 33 ?
```

ps -e | grep apt
ps -e | grep unattended-upgrades
ps -e | grep software-center
ps -e | grep synaptic

```



And what are the exact results ?
[INDENT][INDENT]back up and regroup
[/INDENT]
[/INDENT]


No apt processes found

```

anbu@Terminatore:~$ ps -e | grep apt
anbu@Terminatore:~$ ps -e | grep unattended-upgrades
anbu@Terminatore:~$ ps -e | grep software-center
anbu@Terminatore:~$ ps -e | grep synaptic

```

---

### Post by Bashing-om on 2016-10-26
anbu-s; K;

Think'n .. trying to come up with a way forward.

[INDENT][INDENT]one of those times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-10-27
anbu-s; Welkp ..

I have come up with nothing better than to consider " python3-distupgrade " .

So what have you got installed ?
show:
```

dpkg -l python3-distupgrade
apt list python3-distupgrade
lsb_release -a

```
where in yakkety we are looking for:
> 
Package python3-distupgrade
yakkety (python): manage release upgrades 
1:16.10.6: all

and in xenial:
> 
Package python3-distupgrade
xenial-updates (python): manage release upgrades 
1:16.04.17: all


[INDENT][INDENT]I wish I knew
[INDENT][INDENT][INDENT]but not yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-10-27
> **anbu-s said:**
> No apt processes found

```

anbu@Terminatore:~$ ps -e | grep apt
anbu@Terminatore:~$ ps -e | grep unattended-upgrades
anbu@Terminatore:~$ ps -e | grep software-center
anbu@Terminatore:~$ ps -e | grep synaptic

```

That is just the first step of the instructions in Post #33.
Did you do the rest?
What was the result?

---

### Post by anbu-s on 2016-10-27
> **ian-weisser said:**
> That is just the first step of the instructions in Post #33.
Did you do the rest?
What was the result?

Yes i did remove the locks
After sudo apt update && sudo apt-upgrade when i tried the do-release-upgrade command, it failed exactly at the same stage with a failed to lock error msg.

---

### Post by anbu-s on 2017-02-01
Can anyone help on this issue? I'm still having this lock issue - no matter what I try.
Any other suggestions? I really dont want to load 16.10 from scratch again!!

---

### Post by ian-weisser on 2017-02-01
Help you how?
Are you saying your apt has been locked for three months?

If nobody else is having these problems, then try re-installing apt.

---

### Post by deadflowr on 2017-02-02
One thing I see is rattling my brain and that is you had installed the gnome3-staging ppa.
Did you properly purge it before attempting to run the upgrade?

Maybe, somewhere in the thread you might have mentioned it, but if not, unlike other ppas (where you only need to disable those) you actually need to revert the gnome3-staging packages back to the xenial defaults before the upgrade.
Install ppa-purge to do so.

May or may not be significant.

reference from the ppa launchpad page:
> === Removing ===
Use ppa-purge to remove this PPA. It is *particularly* important to do this before upgrading to a new release!

ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3



---

### Post by anbu-s on 2017-02-02
> **deadflowr said:**
> One thing I see is rattling my brain and that is you had installed the gnome3-staging ppa.
Did you properly purge it before attempting to run the upgrade?

Maybe, somewhere in the thread you might have mentioned it, but if not, unlike other ppas (where you only need to disable those) you actually need to revert the gnome3-staging packages back to the xenial defaults before the upgrade.
Install ppa-purge to do so.

May or may not be significant.

reference from the ppa launchpad page:

Should I just run these 2 commands and then try the upgrade?

ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3

---

### Post by anbu-s on 2017-02-02
gnome3-staging and gnome3 is no longer installed on my pc.
when i try to run the command, I get package not found message Could not find package list for PPA: gnome3-team gnome3

---

### Post by krkeegan on 2017-02-04
I too was suffering from what sounds like the exact same problem.  I tried all of the suggestions here and nothing helped.

First, I changed my /etc/apt/sources.list file back to xenial

One thing I didn't see mentioned is that the upgrade creates a log in /var/log/dist-upgrade

The main.log had some details but ultimately nothing helpful for me.

The one thing that seemed to keep coming up was uninstalling any non-standard packages.

In my case, I like to use aptitude for package management.  I don't know if that is normal.  Anyways, I opened the "Obsolete or Locally Installed Packages" section and uninstalled everything there.  There were a lot of libraries that I know nothing about and some packages that I had installed in the past that I knew I didn't need. The uninstall went fine.  Again, I think you need to have your sources set to xenial for this to work properly.

I then deleted the /var/cache/apt/archive/lock file and restarted.

I was then able to successfully run the gui version of software update to upgrade to 16.10.

Now I have to track down the various third party things I still want to reinstall.

Hope this helps.  I am no expert or even close to one, so maybe someone else who is smarter than me should confirm that this is a recommended action before you proceed.

---

