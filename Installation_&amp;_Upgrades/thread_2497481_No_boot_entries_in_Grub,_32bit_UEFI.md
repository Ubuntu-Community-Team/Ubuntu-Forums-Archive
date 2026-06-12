---
title: "No boot entries in Grub, 32bit UEFI"
date: 2024-05-07
forum: Installation &amp; Upgrades
---

### Post by djeyewater on 2024-05-07
I have an old tablet that has a 64 bit processor but 32 bit UEFI.
I've installed Ubuntu on it, but on boot it will just load up the grub shell. I then have to type the commands manually to boot the OS.
My understanding is that I need to install grub-efi-ia32 (and then run grub-install).
But on running apt install grub-efi-ia32 we get error:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 shim-signed : Depends: grub-efi-amd64-signed (>= 1.191~) but it is not going to be installed or
                        grub-efi-arm64-signed (>= 1.191~) but it is not installable or
                        base-files (< 12.3) but 12.3ubuntu2 is to be installed
               Depends: grub-efi-amd64-signed (>= 1.187.2~) but it is not going to be installed or
                        grub-efi-arm64-signed (>= 1.187.2~) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

When installing another package I got the following errors:
```
dpkg: warning: files list file for package 'grub-efi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-efi-amd64-signed' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-efi-ia32-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-efi-amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-efi-amd64-bin' missing; assuming package has no files currently installed
```

So did a --reinstall for each of those but that didn't make any difference to being able to install grub-efi-ia32.

I've run the boot-repair report and system-info script as were suggested in my previous thread about a different issue, and these are below (not sure why, but the system-info.txt file won't upload so I've put it in a pastebin):
boot-repair report: [ATTACH]293737[/ATTACH]
System-info script report: [https://pastebin.com/0LhtSHRZ](https://pastebin.com/0LhtSHRZ)

I've not tried running the actual boot-repair as I'm worried it might try and overwrite the current efi with a 64 bit one leaving me with no boot at all. But maybe I should just run that?

---

### Post by gezzer2 on 2024-05-07
not sure if this is of help but it got my system up and running with a signed boot loader from Debian.
this was on MX Linux which is Debian based the same as Ubuntu

[https://forum.mxlinux.org/viewtopic.php?t=67022](https://forum.mxlinux.org/viewtopic.php?t=67022)

you may need to change a few of the commands to get the Debian i386 shim installed via the terminal ..

---

### Post by oldfred on 2024-05-07
I do not think Boot-Repair knows about 32 bit UEFI on 64 bit systems.
I thought you just had to manually copy the 32 bit UEFI files.

[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)

---

### Post by MAFoElffen on 2024-05-07
No boot-repiar does nto know about 32bit UEFI. It's a manual affair.

I'm in the middle of things at the moment, but if you search my posts here on MacBook 32bit EFI, you should find my posts explaining how to install Grub2 for 32bit UEFI BIOS. I think I remember there was a GitHub I used for reference, with the instructions for that.

I have a 2007 MacBook that I was given to test the UbuntuForums 'system-info' script on, to do physical tests/verification for MAC Hardware. It has 32bit UEFI...

---

### Post by MAFoElffen on 2024-05-07
Had a couple minutes. Looked at my systems notes/journals. Here is what I used: [https://github.com/faalbers/EFI_32_BIT](https://github.com/faalbers/EFI_32_BIT)

---

### Post by djeyewater on 2024-05-15
> **MAFoElffen said:**
> Had a couple minutes. Looked at my systems notes/journals. Here is what I used: [https://github.com/faalbers/EFI_32_BIT](https://github.com/faalbers/EFI_32_BIT)

Thanks, unfortunately that just says to run "sudo apt-get install grub-efi-ia32" which as you can see from my original post I have already tried but it won't install.

---

### Post by djeyewater on 2024-05-15
> **oldfred said:**
> I do not think Boot-Repair knows about 32 bit UEFI on 64 bit systems.
I thought you just had to manually copy the 32 bit UEFI files.

[https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc](https://askubuntu.com/questions/775498/ubuntu-on-32-bit-uefi-only-based-tablet-pc)

Thanks, unfortunately that just seems to about setting up the EFI boot file, which I already have. I can't see there where it says about how to add boot entries to grub?

---

### Post by oldfred on 2024-05-15
Does not grub entry get added when installing?
Or if installed does not os-prober find other installs?
sudo os-prober

examples from cavfan
[https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046](https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046)
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by MAFoElffen on 2024-05-15
When I installed 'grub-efi-ia32'
```

sudo dpkg --add-architecture i386
sudo apt update
sudo apt install -y ia32-libs grub-efi-ia32 grub-efi-ia32-bin
sudo grub install --target=i386-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

```
The valid options for grub-install --target are:
```

--target=TARGET

    install GRUB for TARGET platform [default=x86_64-efi]; available targets: 
    arm-coreboot, arm-efi, arm-uboot, arm64-efi, i386-coreboot, i386-efi, 
    i386-ieee1275, i386-multiboot, i386-pc, i386-qemu, i386-xen, i386-xen_pvh, 
    ia64-efi, loongarch64-efi, mips-arc, mips-qemu_mips, mipsel-arc, 
    mipsel-loongson, mipsel-qemu_mips, powerpc-ieee1275, riscv32-efi, 
    riscv64-efi, sparc64-ieee1275, x86_64-efi, x86_64-xen

```
It used to be that if you didn't specify amd64, that if it had to guess between 'i386 &amd64', that it defaulted to i386... But that isn't how it is anymore (hasn't been for awhile_, so please include the target to i386-pc.

It that doesn't work, I'll upload an Ubuntu i386 .efi file for you can copy over into your <EFI Disk>/EFI/ubuntu/ and <EFi_ Disk>/EFI/Boot Folders...

---

### Post by djeyewater on 2024-08-01
Thanks for the suggestion. Unfortunately when I try and install ia32-libs I get a message that the package doesn't exist.
So I installed ia32-libs_2.2ubuntu18_amd64.deb from [https://old-releases.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/](https://old-releases.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/)
But that gives the error:
```
dpkg: error processing archive ./ia32-libs_2.2ubuntu18_amd64.deb (--install):
 unable to install new version of '/usr/lib32/libusb-0.1.so.4': No such file or directory
```
If I ignore that and try to install grub-efi-ia32 anyway, I get the error:
```
The following packages have unmet dependencies:
 shim-signed : Depends: grub-efi-amd64-signed (>= 1.191~) but it is not going to be installed or
                        grub-efi-arm64-signed (>= 1.191~) but it is not installable or
                        base-files (< 12.3)
               Depends: grub-efi-amd64-signed (>= 1.187.2~) but it is not going to be installed or
                        grub-efi-arm64-signed (>= 1.187.2~) but it is not installable
```

Not sure if it's that I installed the wrong version of ia32-libs or something else?

---

### Post by leongzhaoyuan on 2024-08-05
Hi, I'm also having the same issue and error messages as djeyewater and have tried everything in this thread. Is there anything else I can do please.

---

### Post by oldfred on 2024-08-05
@leonzhoayan
If instructions here have not helped better to start your own thread.
Refer to this one, so we know what you have tried. 
Post details on what hardware.
But if older limited hardware, Ubuntu may be too much and you need a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

