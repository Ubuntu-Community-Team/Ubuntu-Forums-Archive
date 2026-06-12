---
title: "Upgrade from 8.10 to 12.04 failing in multiple ways"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by jimhenry on 2012-05-01
I have a Dell Inspiron 15n which came with Ubuntu 8.10 preinstalled.  I've installed a few additional programs (Emacs, etc.) on it but never felt a particular need to upgrade the OS until recently.  Installs of new apps have been failing, apparently because they depend on finding an /intrepid/ directory hierarchy on ubuntu.com which doesn't exist anymore.  So I started following the instructions for upgrading to the current version one version at a time, editing the config files in /etc/apt to point to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty, etc.; this  failed spectacularly in upgrading even as far as 9.04.   I now have a machine that won't boot any farther than the login screen before hanging.  If I press ESC in the boot loader and select "manual reinstall" I can boot 8.10 from an apparently read-only recovery partition; this sort of works, letting me check my email and edit files on an external hard drive, though I can't seem to save configuration settings from one login session to another.

So I've downloaded the 12.04 ISO file and have been trying to create a bootable CD or USB stick.  Both seem to fail.  The CD appears to look right when I stick it in the CD drive on a Windows machine (a Lenovo belonging to a friend), but my Dell Inspiron won't boot from it, and when I boot into Ubuntu 8.10 in recovery mode, it won't even mount the CD manually -- it says it has an unrecognized filesystem type.  I've tried specifying several fs types on the mount command, to no avail.  I burned two CDs from the same ISO file using a Windows CD-burning program recommended on ubuntu.com, and both CDs fail in the same way. I can mount the ISO file itself off of an external hard drive, and the filesystem looks fine there, so I don't think the downloaded file is corrupted.

I tried using the startup disk creator to make a bootable USB flash drive (from an Ativa 4GB flash drive).  When I try to boot from that, I get a "Missing operating system" error message.

Looking at previous theads on the forums here, I see some people saying that the older Startup Disk Creator doesn't always work with ISO files for newer Ubuntu versions, and recommending unetbootin.  However, I downloaded it from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and find I can't run it -- possibly it doesn't work on 8.10?  It looks okay when I run file on it, but when I try to run it, I get a core dump error:

```

ubuntu@ubuntu:/media/cugel$ file unetbootin-linux-575 
unetbootin-linux-575: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, stripped

ubuntu@ubuntu:/media/cugel$ ./unetbootin-linux-575 
Bus error (core dumped)

```I also tried to run the install program from the 8.10 recovery partition, thinking I could at least get back to a stable 8.10 setup even if I can't install anything new; but it hangs when it gets to the partioning stage.  There are no partitions listed and all of the buttons on the window are either greyed out, or do nothing when I click them.  FWIW, I can manually mount  /dev/sda3 and get access to what was the main partition.

Any ideas?  I can see the 12.04 installation disk contents when I look at the USB drive in Nautilus, or when I mount the ISO file directly, and it seems there ought to be a way to install from it without actually booting from it, but I can't seem to figure out how.

---

### Post by jerrrys on 2012-05-01
When you booted the CD from your friends box did you use the option to try it out without installing?

Are you sure your BIOS is set to boot from CD?  My old Dell has to be set to boot from CD everytime I use that option.  It will not remember it at next boot.

---

### Post by jimhenry on 2012-05-01
I haven't tried the "try it out without installing" option on the Windows machine.  I'll try that next.

On my own machine, I have to press F12 before GRUB starts, then I get a list of places to boot from - CD, USB flash drive, hard drive.  I used that menu to attempt booting from the CD and from the USB flash drive.

---

### Post by jimhenry on 2012-05-01
I tested that CD on a Windows machine.  It works fine when I boot from it and "try Ubuntu without installing".

I downloaded the Windows version of unetbootin and used it to recreate the bootable USB flash drive.  When I boot from that on the Lenovo Windows laptop, I can "try Ubuntu without installing" just fine.  But when I try it on the Dell Inspiron laptop, I get farther than I did with the flash drive formatted with Startup Disk Creator, but not very far.  

I get a text mode menu with options like "Help", "Try Ubuntu without installing", "Install Ubuntu", and "Check disk".  When I try "Check disk" it says there are no errors.  But when I select "Try Ubuntu without installing" or  "Install Ubuntu", I get the Ubuntu splash screen, followed twenty or thirty seconds later by an error message about a problem mounting /tmp, and asking if I want to skip it or manually fix it.  Skipping it leads to a blank screen, and apparently a hung process.

Any ideas?  It seems as though the lack of a /tmp directory shouldn't be an insuperable obstacle to installing (or running a sandboxed installation), otherwise it would never work when installed onto a CD instead of a flash drive.  But somehow that's stopping it from going any farther, and the error message about what went wrong with the mount isn't very specific.

---

### Post by jerrrys on 2012-05-01
I have no answer for your Live CD problem.

I would try installing with the "Alternate Install CD"

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by The Rnegade on 2012-05-02
> **jimhenry said:**
> I have a Dell Inspiron 15n which came with Ubuntu 8.10 preinstalled.  I've installed a few additional programs (Emacs, etc.) on it but never felt a particular need to upgrade the OS until recently.  Installs of new apps have been failing, apparently because they depend on finding an /intrepid/ directory hierarchy on ubuntu.com which doesn't exist anymore.  So I started following the instructions for upgrading to the current version one version at a time, editing the config files in /etc/apt to point to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) jaunty, etc.; this  failed spectacularly in upgrading even as far as 9.04.   I now have a machine that won't boot any farther than the login screen before hanging.  If I press ESC in the boot loader and select "manual reinstall" I can boot 8.10 from an apparently read-only recovery partition; this sort of works, letting me check my email and edit files on an external hard drive, though I can't seem to save configuration settings from one login session to another.

So I've downloaded the 12.04 ISO file and have been trying to create a bootable CD or USB stick.  Both seem to fail.  The CD appears to look right when I stick it in the CD drive on a Windows machine (a Lenovo belonging to a friend), but my Dell Inspiron won't boot from it, and when I boot into Ubuntu 8.10 in recovery mode, it won't even mount the CD manually -- it says it has an unrecognized filesystem type.  I've tried specifying several fs types on the mount command, to no avail.  I burned two CDs from the same ISO file using a Windows CD-burning program recommended on ubuntu.com, and both CDs fail in the same way. I can mount the ISO file itself off of an external hard drive, and the filesystem looks fine there, so I don't think the downloaded file is corrupted.

I tried using the startup disk creator to make a bootable USB flash drive (from an Ativa 4GB flash drive).  When I try to boot from that, I get a "Missing operating system" error message.

Looking at previous theads on the forums here, I see some people saying that the older Startup Disk Creator doesn't always work with ISO files for newer Ubuntu versions, and recommending unetbootin.  However, I downloaded it from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and find I can't run it -- possibly it doesn't work on 8.10?  It looks okay when I run file on it, but when I try to run it, I get a core dump error:

```

ubuntu@ubuntu:/media/cugel$ file unetbootin-linux-575 
unetbootin-linux-575: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, stripped

ubuntu@ubuntu:/media/cugel$ ./unetbootin-linux-575 
Bus error (core dumped)

```I also tried to run the install program from the 8.10 recovery partition, thinking I could at least get back to a stable 8.10 setup even if I can't install anything new; but it hangs when it gets to the partioning stage.  There are no partitions listed and all of the buttons on the window are either greyed out, or do nothing when I click them.  FWIW, I can manually mount  /dev/sda3 and get access to what was the main partition.

Any ideas?  I can see the 12.04 installation disk contents when I look at the USB drive in Nautilus, or when I mount the ISO file directly, and it seems there ought to be a way to install from it without actually booting from it, but I can't seem to figure out how.

your operating system is way to old to update to the latest version, even people with the last operating system are having problems upgrading. if you really want to do an upgrade instead of a clean install, you're gonna have to upgrade to the older ubuntu's first. back when i was on fedora you could upgrade to older versions, i assume theres a way on ubuntu. also since your computers so old you might want to make sure that it meets the minimum system requirements of the latest ubuntu

---

### Post by jimhenry on 2012-05-02
> **The Rnegade said:**
> your operating system is way to old to update to the latest version, even people with the last operating system are having problems upgrading. if you really want to do an upgrade instead of a clean install, you're gonna have to upgrade to the older ubuntu's first. ........ also since your computers so old you might want to make sure that it meets the minimum system requirements of the latest ubuntu

I *was* trying to upgrade one version at a time, 8.10 to 9.04, 9.04 to 9.10, etc.  But I never got farther than 9.04 before something got corrupted and the main partition became unusable.  *Now* I'm trying to do a clean install, and that's not working either.

Yes, my system meets the minimum requirements for 12.04, at least according to [https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html).  The machine is three years old; it has a dual-core 2GHz CPU, 4GB of memory, and 160GB hard disk.  The hard disk space seems to be irrelevant to the problems I'm having booting from the CD or the USB flash drive.

I'll try downloading and using the alternate install CD as an earlier poster recommended.

---

