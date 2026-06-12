---
title: "Building kernel: debian/rules broken and version wrong with make-kpkg"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by Erwin123 on 2007-07-08
Hello, 

I'm trying to build the Ubuntu Feisty kernel myself. Actually I want to compile Trevino's suspend2 kernel for x86_64. Since I had some trouble with it, I tried to build the linux-image-2.6.20-16-generic package first.

I followed this guide [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild), but it seems to be out of date somehow. Can you please help me?

This is what I tried:

download source linux-source-2.6.20_2.6.20.orig.tar.gz and all the other stuff, extract source and change to source directory, copy current config with "make oldconfig" - everything is fine up to here. Then go on with the guide:

>debian/rules updateconfigs
make: *** No rule to make target `updateconfigs'.  Stop.

>AUTOBUILD=1 fakeroot debian/rules binary-debs
make: *** No rule to make target `binary-debs'.  Stop.

>make-kpkg --rootcmd fakeroot --initrd  kernel-image kernel-headers 
... compiling everything ... at the end:
dpkg-gencontrol: error: package linux-image-2.6.20.3-ubuntu1 not in control info

The suspend2-patched version compiles fine with make-kpkg, but the final version is also wrong:
"linux-image-2.6.20.3-ubuntu1_2.6.20-15.27+suspend2~2.2.9.12+3v1ubuntu0_amd64.deb"
instead of 
"linux-image-debug-2.6.20-16-generic_2.6.20-15.27+suspend2~2.2.10+3v1ubuntu0_amd64.deb". There is a ".3-ubuntu1" too much...

It seems calling debian/rules doesn't work at all and that make-kpkg is going to create the wrong version number. I really tried for days now and are about giving up. What am I missing?

I would appreciate your comments very much,
Erwin

---

### Post by mcook2 on 2007-07-19
Howdy,

I'm trying to rebuild my kernel for Ubuntu Feisty 7.04 amd_64 and I get exactly the same situation as you describe.  My arch is x86_64 and uname -r shows 2.6.20-16-generic.

According to SPM the latest linux-source-2.6.20 is  version 2.6.20-16.29 and that's what I have in /usr/src/linux.

I've been puzzling over this for a few days, thinking the cause must be user error on my part.  No matter what I do make-kpkg will only create objects called *2.6.20-3* which is way old.  

Also, I noticed that make oldconfig run against my current config  file creates a new file with this line at the top:

# Linux kernel version: 2.6.20.3-ubuntu1

And make menuconfig also shows this string in the title bar. 

I was wondering what I might have done wrong and how to fix it - then I saw your post. 

I took a look at using git to get the source and then running make.  This avoids the problem and I can make a kernel, but so far I haven't figured out the rest of the details -  to get the System.map*, abi-*, and initrd* objects lined up, and how to update grub properly.

Regards,

Michael Cook

---

### Post by mcook2 on 2007-07-19
Aha!

Looking at my allegedly 2.6.20-16.29 Makefile, right at the top it says:

VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 20
EXTRAVERSION = .3-ubuntu1
NAME = Homicidal Dwarf Hamster

The README.Debian file says:

    $Id: README.source,v 1.2 1999/10/08 10:33:41 srivasta Exp $

        If you wish to create a kernel image Debian package, e.g.:
 ../linux-image2.6.20_2.6.20-C1.0_i386.deb
 please read /usr/share/doc/kernel-source-2.6.20/README.gz fileand follow
 directions.

        The file /usr/share/doc/kernel-source-2.6.20/Rationale.gz contains
 reasons why you may wish to do so.

This should say it's in /usr/share/doc/linux-source-2.6.20.

The file debian.README is similarly old.  That's nice.  

I'm just gonna edit my Makefile to look like this:

VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 20
EXTRAVERSION = .16-29-ubuntu1-mcook
NAME = Homicidal Dwarf Hamster Not Very Smart

Then I'll do a make oldconfig followed by make-kpkg --initrd --append-to-version=-mybuild kernel_image kernel_headers and see what happens.

I'll let you know,

M.C.

---

### Post by mcook2 on 2007-07-20
Ya, so that seemed to run OK but I got package files called:

linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb
linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb

Ugh! These package names seem to be rather unnecessarily verbose, repetitive and unwieldy, but I did the following regardless:

dpkg -i linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb

And got this report:

> Selecting previously deselected package linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild.
(Reading database ... 161295 files and directories currently installed.)
Unpacking linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild (from linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb) ...
Done.
Setting up linux-image-2.6.20.16-29-ubuntu1-mcook-mybuild (2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20.16-29-ubuntu1-mcook-mybuild
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
find: /lib/firmware/2.6.20.16-29-ubuntu1-mcook-mybuild: No such file or directory
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20.16-29-ubuntu1-mcook-mybuild
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Then I did:

dpkg -i linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb

And got:

> Selecting previously deselected package linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild.
(Reading database ... 163452 files and directories currently installed.)
Unpacking linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild (from linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild_2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom_amd64.deb) ...
Setting up linux-headers-2.6.20.16-29-ubuntu1-mcook-mybuild (2.6.20.16-29-ubuntu1-mcook-mybuild-10.00.Custom) ...

After all this excitement my new kernel boots OK but I'm missing at least some firmware and Nvidia drivers I need from linux-restricted-modules. Presently I'm looking into how to best deal with those problems but they should be easy to fix without having to rebuild my kernel, tho' I might do that anyway to get more user-friendly package names.

Regarding the "debian/rules" part of your original post, in the document at [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") I noticed that it says:

> "Building the kernel (when source is from git repository)

"To build the kernel(s) is very simple. Depending on your needs, you may want to build all the kernel targets, or just one specific to your system. However, you also want to make sure that you do not clash with the stock kernels.

"These instructions are specific to the git-tree, not when downloading the linux-source package " ... 

It then goes on to talk about using AUTOBUILD and debian/rules, and this advice seems to be different to that at [https://wiki.ubuntu.com/KernelCustomBuild]("https://wiki.ubuntu.com/KernelCustomBuild"), and might explain the troubles with:
 
debian/rules updateconfigs  and  AUTOBUILD=1 fakeroot debian/rules binary-debs.

Using GIT to get the source seems like the new right way to go. See [See https://wiki.ubuntu.com/KernelGitGuide]("See https://wiki.ubuntu.com/KernelGitGuide").

If I find out anything else interesting I'll let you know - the stuff to do with modules and restricted drivers and firmware could also turn out a bit complicated.

M.C.

---

