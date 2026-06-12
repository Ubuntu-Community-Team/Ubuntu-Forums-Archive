---
title: "[Solved] Ubuntu 22.04 LTS Jammy: New Kernel is not installed automatically"
date: 2023-04-18
forum: Installation &amp; Upgrades
---

### Post by daku8938 on 2023-04-18
[COLOR=#333333][FONT=monospace]On Ubuntu 22.04.1 Jammy, we are running following kernel:

[/FONT][/COLOR]5.15.0-67-generic[COLOR=#333333][FONT=monospace]

The newest available kernel linux-image-5.15.0-69-generic is available:[/FONT][/COLOR]

```
[COLOR=#333333][FONT=monospace]apt-cache policy linux-image-5.15.0-69-generic[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]linux-image-5.15.0-69-generic:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Installed: (none)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Candidate: 5.15.0-69.76[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Version table:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]5.15.0-69.76 500[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]500 http://de.archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages[/FONT][/COLOR]

```

[COLOR=#333333][FONT=monospace]But it is not automatically installed with ```
sudo apt full-upgrade
```
[/FONT][/COLOR]

[COLOR=#333333][FONT=monospace]Why not?  We do *not* want to use Hardware Enabled Stack (HWE) kernels, we prefer to have only minimal updates only for security patches.
But as one can see above, the package [/FONT][/COLOR][COLOR=#333333][FONT=monospace]linux-image-5.15.0-69-generic stems from the [/FONT][/COLOR][COLOR=#333333][FONT=monospace]jammy-security/main  pocket so why is it not installed wit full-upgrade ??[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-04-18
First is this installed:
```
apt policy linux-base
```
Also can you show us this:
```
sudo apt update
```
Edit: I just did a dry run:
```
sudo apt install linux-image-5.15.0-69-generic  linux-headers-5.15.0-69-generic linux-modules-extra-5.15.0-69-generic -s
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-headers-5.15.0-69 linux-modules-5.15.0-69-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools
The following NEW packages will be installed:
  linux-headers-5.15.0-69 linux-headers-5.15.0-69-generic
  linux-image-5.15.0-69-generic linux-modules-5.15.0-69-generic
  linux-modules-extra-5.15.0-69-generic
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Inst linux-headers-5.15.0-69 (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])
Inst linux-headers-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst linux-modules-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64]) []
Inst linux-image-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst linux-modules-extra-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-headers-5.15.0-69 (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])
Conf linux-headers-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-modules-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-image-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-modules-extra-5.15.0-69-generic (5.15.0-69.76 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])


```

---

### Post by deadflowr on 2023-04-18
New kernels are not automatic unless you have the meta-package installed.
look at which meta-package is installed
```
dpkg -l | grep linux-image
```
22.04 has two options, linux-image-generic and linux-image-generic-hwe-22.04
The hwe is the default on desktops. Not sure about servers.

Note that I use the term meta-package, but that's not quite accurate.
The short of it is those two packages are set to always depend on the latest kernel for whatever version they are tied to.
So whenever a new kernel is available, when you have those meta-packages installed, it automatically sets it to install the new kernel.

---

### Post by Impavidus on 2023-04-18
The new kernel will be installed when the metapackage is upgraded. So look at that:```
apt-cache policy linux-image-generic
```Maybe it's still in phased updates. Or maybe the upgrade is available now.

---

### Post by Bashing-om on 2023-04-18
New kernel is out today:
> 
sysop@x2204mini:~$ apt-cache policy linux-image-generic
linux-image-generic:
  Installed: 5.15.0.70.68
  Candidate: 5.15.0.70.68
  Version table:
 *** 5.15.0.70.68 500
<snip>


[INDENT]keeping updated is the smart thing
[/INDENT]

---

### Post by daku8938 on 2023-04-19
Thanks for your responses, I guess they let me to the cause for the problem:

We need to install the package linux-image-virtual

linux-image-virtual is better for us because linux-image-generic has too much dependencies (e.g. for package wireless-regdb) that we do not need and do not want because they make the initrd.img so big that our /boot/ partiton runs full when upgrading kernel.

I do not know why but somehow it seems we lost package linux-image-virtual  for some reason, I will have a look, but the solution for the problem of this thread seems to be:

```

sudo apt install linux-image-virtual
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fdisk gdisk libfdisk1 libinih1
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-5.15.0-70-generic linux-modules-5.15.0-70-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools linux-headers-5.15.0-70-generic linux-modules-extra-5.15.0-70-generic
The following NEW packages will be installed:
  linux-image-5.15.0-70-generic linux-image-virtual linux-modules-5.15.0-70-generic
0 upgraded, 3 newly installed, 0 to remove and 7 not upgraded.
Need to get 34.7 MB of archives.
After this operation, 138 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

---

### Post by Bashing-om on 2023-04-19
daku8938

Good sleuthing on your part :D

Glad ya got it fingered out.

[INDENT]see, it is all in the process
[/INDENT]

---

