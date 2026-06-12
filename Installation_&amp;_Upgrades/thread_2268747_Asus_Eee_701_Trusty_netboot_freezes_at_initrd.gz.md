---
title: "Asus Eee 701: Trusty netboot freezes at initrd.gz"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by Lars Noodén on 2015-03-11
I'd like to do a PXE installation of 14.04 LTS for i386 on an Asus Eee 701.  The Eee seems to do PXE just fine, at first, but locks up after selecting "Install" from the the Installer boot menu.  

I've downloaded the [netboot tarball for Ubuntu 14.04 LTS on i386](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/) to install on the Eee.   I see from dhcpd that it gets an ip address and gets pointed at the tftp server.  I see from tftpd that it finds the tftp server and loads the menus and boot screens.   Then from looking at tftpd it appears to  load the kernel and initrd.gz.  The last tftp request is " read request for 'ubuntu-installer/i386/initrd.gz' " However, it is at this point the installer on the Eee locks up.  tcpdump shows no more packets being transferred.

```

tftpd: x.y.z.a: read request for 'ubuntu-installer/i386/boot-screens/splash.png'
tftpd: x.y.z.a: read request for 'ubuntu-installer/i386/linux'
tftpd: x.y.z.a: read request for 'ubuntu-installer/i386/initrd.gz'

```

What am I missing or what should I change to get the installer running on the Eee 701?

---

### Post by ajgreeny on 2015-03-11
Are you sure that machine will ever run Ubuntu 14.04?  It seems to have only 512MB ram from what I have found, which will be pushing the boundary of Ubuntu requirements.

---

### Post by Lars Noodén on 2015-03-11
I added RAM years ago so it now has 2GB and though there is only 4GB of SSD, there is an additional 16GB SD.  

I've tried "Command-line" installation as well, but that hangs too.

---

### Post by ajgreeny on 2015-03-11
I think the standard Ubuntu installation needs more than 4GB.
I also suspect you can not choose to install and then successfully boot if the OS is installed to the SD, though I may be wrong about that.  Do you know if the machine is able to boot from the SD?

---

### Post by Lars Noodén on 2015-03-11
It looks like it should be able to boot from the SD.  How would that help, though?  The BIOS setup lists "Removable Dev." as one of the boot options.  However, I am not getting to the point where the installation is even starting.  I'm not worried about disk space.  I can install a bare-bones system and then add what I need.  However, the system is not booting into the actual installer.

---

### Post by Lars Noodén on 2015-03-11
According to the dmesg from OpenBSD, it has for a CPU an Intel(R) Celeron(R) M processor 900MHz ("GenuineIntel 686-class) 631 MHz

What kind of kernel or distro would that require?

---

### Post by Lars Noodén on 2015-03-11
It looks like the processor may be the problem for the newer kernels.  

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

However, I've tried adding 'forcepae' to the boot parameters and see no change.

---

### Post by mörgæs on 2015-03-11
(Please disregard old post. Messed up RAM and SSD size.)

Have you tried an alternate Lubuntu?

---

### Post by Lars Noodén on 2015-03-12
> **mörgæs said:**
> Have you tried an alternate Lubuntu?

As far as I know there is only one netboot image.  I'm not knowledgeable enough to rip pieces out of a regular Desktop or Alternate image and make my own.  

However, it turns out that thenetboot's  Advanced option's Expert command-line method finds a usable kernel.  So that was one solution.

---

