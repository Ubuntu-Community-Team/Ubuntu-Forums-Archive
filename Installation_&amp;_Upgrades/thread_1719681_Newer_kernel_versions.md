---
title: "Newer kernel versions?"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by Ginosal on 2011-04-02
Hi. I've noticed that my linux kernel version is:

2.6.32-27-generic

Isn't it too "old", since the [latest stable kernel]("http://www.kernel.org/") is 2.6.38.2 ? Why doesn't update manager show me newer kernels? I could upgrade by myself, but shouldn't upgrade manager propose them to me? Thanks

---

### Post by zvacet on 2011-04-02
You will get updates for kernel version witch your Ubuntu version use,but not higher.If you want you can compile latest kernel with [kernelchecker.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

### Post by dolphs on 2011-04-02
My question is how did you manage, you do not get the ubuntu kernel updates as I like to compile my own from kernel.org so I am not interested in the Ubuntu specific ones.

Yet the nasty side effect is when the ubuntu kernel gets updated from the repository I need to remove these; so basically I am looking for the option in Ubuntu Server to disable this kernel part from updating ( as I use the kernel from kernel.org ).

Maybe this link helps: [http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu) - but if anyone can confirm this works it would be great

---

### Post by oldfred on 2011-04-02
In synaptic there is a lock version.

Look under package in the heading after you have selected that package you want to lock.

---

### Post by dolphs on 2011-04-02
which file would that be in Ubuntu Server ( as that works without X )? As "sudo aptitude hold linux-image-`uname -r`" does not seem to work:

The following NEW packages will be installed:
  linux-image-2.6.35-28-generic{a}
The following packages will be upgraded:
  apparmor apparmor-utils bash-completion bind9-host bsdutils dnsutils dpkg fuse-utils ifupdown initscripts libapparmor-perl libapparmor1 libbind9-60 libblkid1 libc-bin libc6 libcairo2 libdbus-1-3 libdns66 libdrm-intel1
  libdrm-nouveau1 libdrm-radeon1 libdrm2 libfreetype6 libfuse2 libglib2.0-0 libgssapi-krb5-2 libisc60 libisccc60 libisccfg60 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60 libpam-modules libpam-runtime
  libpam0g libparted0debian1 libplymouth2 libsqlite3-0 libssl0.9.8 libudev0 libuuid1 libxml2 linux-firmware linux-generic linux-image-generic login mount openssh-client openssh-server openssl parted passwd plymouth
  plymouth-theme-ubuntu-text python python-apt python-minimal sudo sysv-rc sysvinit-utils tar tzdata udev update-manager-core upstart util-linux uuid-runtime xkb-data
The following packages are RECOMMENDED but will NOT be installed:
  dbus libdconf0 libglib2.0-data shared-mime-info
71 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 69.6MB of archives. After unpacking 108MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

---

### Post by jcolyn on 2011-04-02
Go here [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and open the latest kernel folder which is currently 2.6.38.2-natty.

If you are using the 32 bit OS download the linux-header that ends in all.deb then the one that ends in i386.deb and last the linux-image that ends in i386.deb

The other files are not needed..

Now do the next steps in the listed order. This is very important..

Go to the folder you downloaded the files to and double click the linux-headers ending in all.deb. Once installed double click the linux-headers ending in i386.deb. Last double click the linux-image ending in i386.deb.

Reboot

If you have the 64 bit OS get and install in this order linux-headers ending in all.deb. Linux-headers ending in amd64.deb and linux-image ending in amd64.deb.

Reboot

No compiling required and the last step will update grub But.........be sure to install in the above listed order...

---

### Post by domu on 2011-04-03
Could there be any problems with running 2.6.38.2-natty with an older Ubuntu version? It's a long way ahead of the official latest kernel for maverick (10.10) which I think is 2.6.35-28; or for lucid (10.04) which is 2.6.32-30.

I have a command line (terminal) script for identifying installed kernels and, if required, removing unwanted ones, which you can get from [http://www.timedicer.co.uk/]("http://www.timedicer.co.uk/"). Just go to 'My Programs' section and get 'remove-kernel'.

---

### Post by jcolyn on 2011-04-03
> **domu said:**
> Could there be any problems with running 2.6.38.2-natty with an older Ubuntu version? It's a long way ahead of the official latest kernel for maverick (10.10) which I think is 2.6.35-28; or for lucid (10.04) which is 2.6.32-30.

I have a command line (terminal) script for identifying installed kernels and, if required, removing unwanted ones, which you can get from [http://www.timedicer.co.uk/](http://www.timedicer.co.uk/). Just go to 'My Programs' section and get 'remove-kernel'.

I'm running the 2.6.38-2 kernel on a Linux Mint 10 KDE computer. I have not had any issues with it and it runs much better overall..

---

### Post by domu on 2011-04-04
Thanks I'll give it a try...

---

### Post by zvacet on 2011-04-05
@ **Ginosal**

Read [this]("https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg") and see if that can help you.

---

### Post by snowpine on 2011-04-05
> **Ginosal said:**
> Hi. I've noticed that my linux kernel version is:

2.6.32-27-generic

Isn't it too "old", since the [latest stable kernel]("http://www.kernel.org/") is 2.6.38.2 ? Why doesn't update manager show me newer kernels? I could upgrade by myself, but shouldn't upgrade manager propose them to me? Thanks

2.6.32 is a "long term support" kernel that should serve most users well for many years. Unless you are having a specific hardware or performance issue, there is no reason you **need** a newer kernel; this is the reason why the Ubuntu update manager does not propose newer kernels such as 2.6.38.

You may of course upgrade your kernel using other methods (such as the kernel PPA), if you desire.

---

