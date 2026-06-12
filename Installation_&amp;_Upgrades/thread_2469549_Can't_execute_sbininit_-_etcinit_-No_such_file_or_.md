---
title: "Can't execute /sbin/init - /etc/init -No such file or directory/ Permission denied"
date: 2021-12-02
forum: Installation &amp; Upgrades
---

### Post by ra00f on 2021-12-02
Hello,

I've encountered an improper shutdown on my Ubuntu 20.04

Now I get the following error 
> Can't execute /sbin/init - No such file or directory
Target filesystem doesn't have the requested /sbin/init
run-init: can't execute /sbin/init : No such file or directory
run-init: can't execute /etc/init : Permission denied
.....


I've tried to boot through the recovery mode of grub but got the same error.

I've booted via a live USB and installed Boot Repair Package. When I press the Fix button I get the following error
> Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 20.04.3 LTS (sda9). Then try again.
and then asks me to choose from a list of sources.

I've been struggling with this a couple of days. Is there any way to overcome the situation other than a fresh install?

Thanks.

---

### Post by tea for one on 2021-12-02
```
Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 20.04.3 LTS (sda9). Then try again. 
```

The package [COLOR="#0000FF"]grub-efi-amd64-signed[/COLOR] is in focal/main.

```
edited@edited:~$ apt policy grub-efi-amd64-signed
grub-efi-amd64-signed:
  Installed: 1.167.2+2.04-1ubuntu44.2
  Candidate: 1.167.2+2.04-1ubuntu44.2
  Version table:
 *** 1.167.2+2.04-1ubuntu44.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.142+2.04-1ubuntu26 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
edited@edited:~$
```

---

### Post by ra00f on 2021-12-03
Thanks for the reply.

When I open the sources.list, it already has the following lines in it.
> deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) focal-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) focal-updates main restricted

:confused:

---

### Post by ra00f on 2021-12-08
I'm herewith enclosing the boot-info summary created by the boot-repair.

[https://paste.ubuntu.com/p/G2VTghtkZQ/](https://paste.ubuntu.com/p/G2VTghtkZQ/)

Kindly have a look and let me know if there's any solution exists.

Thanks

---

### Post by yancek on 2021-12-09
What exactly does encountered an improper shutdown mean in this case?  Did you force a shutdown with the power button or some thing else?

Are you able to access the BIOS firmware options and select from the Boot Options there either Boot0000 (windows) or Boot000D (Ubuntu)?  You have the ;proper EFI boot files for both Ubuntu and windows on the EFI partition (sda1) so they should boot.

Using the USB, can you boot it and mount sda9 to see if the files in question  actually exist and what permissions they have?

---

### Post by MAFoElffen on 2021-12-12
I'm lost. The reason this does not make sense to me is that if you had a healthy system and in a terminal or console session typed
```

which init

```
it should return
```

/usr/sbin/init

```
That is where that executable 'init' exists. It is called by Kernel, and is the parent of all processes in the system.

What you are describing is system corruption problem, not a boot loader problem that can be corrected via the boot repair ISO. The reason rescue mode does not work, is that the problem is in the base of the system.

My condolences. I am sorry for your loss...

Unfortunately, it falls into the same box as if the dpkg or apt systems are bad... in that the only way I know of correcting it, is to reinstall the system.

When was the last time you did a backup? If not recent (or never), then backup your data and configuration files... Then reinstall The OS, reconfigure your configuration files, then restore your data. (Just for your Ubuntu Installation).

If that is 'where' that problem resides... 

You still may have some slight hope... The question is if only the current kernel and intramfs is affected, or if the problem resides within in the root system itself. What I would try first... is while booting, hit the shift key repeatedly, and use that same grub menu to use "Advanced" to try booting an older kernel... You might have a chance then, but that would be by patching and stitching it back together.

---

### Post by tea for one on 2021-12-12
> You still may have some slight hope... The question is if only the current kernel and intramfs is affected, or if the problem resides within in the root system itself. 
What I would try first... is while booting, hit the shift key repeatedly, and use that same grub menu to use "Advanced" to try booting an older kernel
Yes, certainly worth trying.

To reach grub when booting the PC, there are two different keys depending on the mode of OS installation.

Installations in BIOS mode - Use [COLOR="#0000FF"]Shift[/COLOR] key
Installations in UEFI mode - Use [COLOR="#0000FF"]Esc[/COLOR] key

---

### Post by MAFoElffen on 2021-12-12
The reasoning for trying that... In the current state of the system on the current kernel...

If it is so twisted that it cannot find "init" and start it "properly"... "init" starts as process ID #1. If it cannot start, then anything else, including dpkg and APT is not going to work to be able to repair it.

The only other thing I can think of beyond that is to mount and chroot into the installed system to try to get it to work. But in a chroot, there is a fine line there, where the LiveCD's environment ends, and the installed system begins. I'm not positive where that is with a problem like this is, and at what level that line is. I know a broken dpkg or APT is on the Installed system, in that case, those systems still reside in the installed system side of a chroot, and cannot be helped by a chroot. I'm not sure, with this problem, if a helper/host chroot can help or not. It may be enough, but I'm not positive.

But... The indicator that a chroot is not going to work for him, is that Yann's scripts on the the Boot Repair Disk mounts and chroot's into the installed system, and uses that chroot into the installed system to try to repair the boot process of Grub. It has already failed to use the installed system's APT system to find and install 'grub-efi-amd64-signed'... So I think that tells us that the problem resides on the installed system's side of a chroot, and can not be fixed via a chroot.

---

