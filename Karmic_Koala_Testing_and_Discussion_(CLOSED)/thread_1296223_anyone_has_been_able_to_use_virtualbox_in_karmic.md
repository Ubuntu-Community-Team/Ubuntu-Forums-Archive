---
title: "anyone has been able to use virtualbox in karmic?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-20
Hi
I am wondering whether anyone was able to use virtual box in karmic?
for me it fails with

```

Kernel driver not installed (rc=-1908)

```
 and when I try to fix it using the given suggested command:

```

/etc/init.d/vboxdrv setup

```

Nothing happens and the log file shows the following content:

```

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.0.6

------------------------------
Deleting module version: 3.0.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.0.6/source ->
                 /usr/src/vboxdrv-3.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-14-generic-pae cannot be found at
/lib/modules/2.6.31-14-generic-pae/build or /lib/modules/2.6.31-14-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

Any help is welcome.

---

### Post by cariboo on 2009-10-20
How are you trying to install Virtualbox, I've been using it since alpha 2. If you have downloaded the deb from virtualbox.org, use gedebi to install it. Gdebi will gather all the dependencies needed to install the program.

---

### Post by dinxter on 2009-10-20
A custom kernel I'm guessing? dkms can't find the source to build the module against, try using dkms manually but adding a relevant --kernelsourcedir parameter so that it can find it

---

### Post by gdonwallace on 2009-10-20
I would suggest downloading the .deb file from virtualbox.org.  When the download is complete, gdebi should launch and install the .deb file for you.  That way it will take care of any dependacy problems you may have.

---

### Post by xebian on 2009-10-20
> **legolas_w said:**
> Hi
I am wondering whether anyone was able to use virtual box in karmic?
for me it fails with

```

Kernel driver not installed (rc=-1908)

```
 and when I try to fix it using the given suggested command:

```

/etc/init.d/vboxdrv setup

```

Nothing happens and the log file shows the following content:

```

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.0.6

------------------------------
Deleting module version: 3.0.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.0.6/source ->
                 /usr/src/vboxdrv-3.0.6

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-14-generic-pae cannot be found at
/lib/modules/2.6.31-14-generic-pae/build or /lib/modules/2.6.31-14-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147:[COLOR="Red"] *** Error: unable to find the sources of your current Linux kernel. [/COLOR]Specify KERN_DIR=<directory> and run Make again.  Stop.

```

Any help is welcome.

You need to install the headers for your kernel.  See the error message above in red.

---

### Post by slakkie on 2009-10-20
Install linux-headers-generic-pae meta package that will install the correct version and will do so whenever the kernel is updated. 

```

sudo aptitude install linux-headers-generic-pae
# or
sudo aptitude install linux-headers-$(uname -r)

```

---

