---
title: "Kernel compilation: weird result"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by bracc0 on 2007-11-10
Hello guru's,
I am a quite happy ubuntu user since last summer. Still a newbie, but I want to improve :-)

I have tried several times to compile a custom kernel from the vanilla tarball, The procedure is clear to me (at least I believe so) but results are poor :-(

I'll list the steps I did in my last test. Please note that I did the same steps with a Debian 4.0 box, and it was a piece of cake. 

[LIST=1]
[*]downloaded, uncompressed and untared vanilla kernel 2.6.23.1 files
[*]put the resulting directory "linux-2.6.23.1" under /usr/source
[*]created a symbolic link named /usr/src/linux to the new kernel dir
[*]downloaded and installed all the needed-for-kerneklcompile stuff (fakeroot, build-essential, libncurses5-dev, etc.)
[*]run as sudo the make menuconfig utility
[*]loaded in menuconfig a previous existent config file (in my case: /boot/config-2.6.22.14)
[*]saved the new config file as /usr/src/linux/.config
[*]run as sudo the command make-kpkg clean
[*]positioned in /usr/src/linux, 
run as sudo the command ""make-kpkg --initrd --append-to-version=-claudio kernel_image kernel_headers
[*] Installed the resulting packages *deb with "cd .." followed by "sudo dpkg -i  *.deb"
[*]rebooted, and...
[/LIST]

..my new  kernel takes a loooot to come up, audio is disabled, wireless card is disappeared and the system appear to be very slow.

I had a look in the /boot dir:
the file initrd.img-2.6.23-1-claudio is 3 times bigger than the default gutsy kernel image file initrd.img-2.6.22-14-generic

I repeated this VERY SAME PROCEDURE in debian 4.0, this time removing some unused stuff (SCSI cards drivers, graphics card unused, etc.). Well, the recompilation has generated a solid-rock kernel, with benefits in terms of speed.

What's wrong with my kernel recompilation procedure?

I sadly must admit that I've already removed the new-but-slow kernel with the command(s):

sudo dpkg -r  linux-headers-2.6.23-1-claudio
and
sudo dpkg -r  linux-image-2.6.23-1-claudio

so I cannot post any files about that.

Any hint is welcome
Thanks in advance
Claudio

---

### Post by bracc0 on 2007-11-13
Anyone?
TIA 
Claudio

---

