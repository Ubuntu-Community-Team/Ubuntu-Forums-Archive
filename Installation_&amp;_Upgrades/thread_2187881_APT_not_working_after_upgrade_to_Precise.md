---
title: "APT not working after upgrade to Precise"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by wilson-eric-n on 2013-11-14
I upgraded my remote VPS from 10.10 to 12.04 (three separate upgrades).

It worked, in the sense that the machine rebooted, and currently reports that I am running 12.04. However, I am unable to install using apt. For example:

```
me@myserver:~$ sudo apt-get install ruby
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 insserv : Depends: libc6 (>= 2.14) but 2.13-20ubuntu5.3 is to be installed
 libc-dev-bin : Depends: libc6 (> 2.15) but 2.13-20ubuntu5.3 is to be installed
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.3)
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu20.2) but 2.13-20ubuntu5.3 is to be installed
 libglib2.0-0 : Depends: libc6 (>= 2.15) but 2.13-20ubuntu5.3 is to be installed
                Recommends: libglib2.0-data but it is not going to be installed
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu11) but 1.0.3-4ubuntu2 is to be installed
 libpango1.0-0 : Depends: libc6 (>= 2.14) but 2.13-20ubuntu5.3 is to be installed
 libplymouth2 : Depends: libc6 (>= 2.14) but 2.13-20ubuntu5.3 is to be installed
 plymouth : Depends: libc6 (>= 2.14) but 2.13-20ubuntu5.3 is to be installed
            Recommends: plymouth-theme-ubuntu-text but it is not going to be installed or
                        plymouth-theme
 ruby : Depends: ruby1.9.1 (>= 1.9.3.194-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Since the output told me to try ```
apt-get -f install
``` I gave it a shot:

```
me@myserver:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libgconf2-4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  emacs23 emacs23-bin-common emacs23-common emacs23-common-non-dfsg fontconfig-config gconf-service gconf-service-backend gconf2-common libc6
  libfontconfig1 libgconf-2-4 libgconf2-4 libjbig0 libjpeg-turbo8 libjpeg8 liblzma5 libnih1 libtiff5
Suggested packages:
  emacs23-el glibc-doc
The following NEW packages will be installed:
  emacs23-common-non-dfsg gconf-service gconf-service-backend libgconf-2-4 libjbig0 libjpeg-turbo8 libjpeg8 liblzma5 libtiff5
The following packages will be upgraded:
  emacs23 emacs23-bin-common emacs23-common fontconfig-config gconf2-common libc6 libfontconfig1 libgconf2-4 libnih1
9 upgraded, 9 newly installed, 0 to remove and 558 not upgraded.
16 not fully installed or removed.
Need to get 0 B/31.7 MB of archives.
After this operation, 4,272 kB disk space will be freed.
Do you want to continue [Y/n]? Y
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Preconfiguring packages ...
(Reading database ... 45794 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5.3 (using .../libc6_2.15-0ubuntu20.2_amd64.deb) ...
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
runlevel:/var/run/utmp: No such file or directory
Checking for services that may need to be restarted...
Checking init scripts...
runlevel:/var/run/utmp: No such file or directory
WARNING: init script for samba not found.
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.


WARNING: this version of the GNU libc requires kernel version
2.6.24 or later. Please upgrade your kernel before installing
glibc.


The installation of a 2.6 kernel _could_ ask you to install a new libc
first, this is NOT a bug, and should *NOT* be reported. In that case,
please add lenny sources to your /etc/apt/sources.list and run:
  apt-get install -t lenny linux-image-2.6
Then reboot into this new kernel, and proceed with your upgrade
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu20.2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu20.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I don't know where to begin with this. I see various suggestions at the end, but I don't know how to determine what is the best course of action for me.

Suggestions appreciated.

---

### Post by ajgreeny on 2013-11-14
What kernel are you using?

Show the output of command ** uname -a**.  12.04 normally runs at least 3.2 and I suspect you are still running the 10.04 kernel, 2.6. or whatever that was.

---

### Post by wilson-eric-n on 2013-11-14
Your suspicion is confirmed:

```

me@myserver:~$ uname -a
Linux myserver 2.6.18-308.el5.028stab099.3 #1 SMP Wed Mar 7 15:56:00 MSK 2012 x86_64 x86_64 x86_64 GNU/Linux

```

What is the next step?

---

### Post by g-a-c on 2013-11-14
Running 12.04 on a late 2.6 kernel on OpenVZ isn't a problem. However I think your kernel is too old.

I have an OpenVZ VPS running with the 2.6.32-042stab081.3 OpenVZ kernel and it's fine, but the patches for 2.6.18 break something in glibc. I'm surprised you even managed to get it to upgrade, when I was on a host with that kernel I couldn't even get the apt-get dist-upgrade to finish. Unfortunately there's nothing you can do, unless your hosts can move your VPS container to a host which has a newer kernel.

edit - 
```
Linux mybox 2.6.32-042stab081.3 #1 SMP Mon Sep 9 20:07:47 MSK 2013 i686 i686 i386 GNU/Linux
me@mybox:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise
me@mybox:~$

```

---

### Post by ajgreeny on 2013-11-14
My 12.04 xubuntu is running on kernel 3.5.0-43 and you can even move easily to 3.8.0-30 and maybe beyond that as well, though I have a few graphic glitches with the 3.8.0 kernel.

On the assumption that you can do this on VPS I would try to install at least the precise original default of 3.2.0, or the later 3.5.0 or 3.8.0, all of which are available in the normal repos for precise; you will just have to search with that version number.  I always use (and always have done) synaptic package manager a sit is very much more flexible and can do a lot more than the software-centre.

---

### Post by g-a-c on 2013-11-14
On an OpenVZ VPS (which mine definitely is, and the OP's seems to be based on the kernel version string), you're limited to the kernel which is on the host. OpenVZ is just containers running on a single shared kernel. So as a customer, upgrading kernels isn't an option. Not to mention there is no 3.x kernels with OpenVZ support that I'm aware of, so for the hosts to move to a 3.x kernel is also virtually impossible. The only solution as I see it is for the OP's host to upgrade their servers to a 2.6.32 OpenVZ kernel, or if they already have this on some of their host servers then to move the OP's container onto one of these servers.

---

### Post by wilson-eric-n on 2013-11-14
@g-a-c Thanks much for your explanation of the situation. I'll contact the host and see what my options are.

---

