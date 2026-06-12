---
title: "installing 10.04 server fails: unmet dependencies installing linux-image"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by sulla on 2010-05-03
Dear all!

I find that ubuntu 10.04 server AMD64 (probably others as well) does not install on my machine, I get errors during installing the kernel (linux-image-2.6.32-21-server_2.6.32-21.32_amd64.deb): Somehow the installer produces unmet dependencies and the server installer ends with an error. (dpkg I/O error, but this probably is not the cause).

Machine is a
[LIST]
[*]Mainboard: ASRock 939A785GMH/128M (AMD 785G chipset, 128MB sidport memory)
[*]CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[*]512MB Ram, one module
[*] 2xWD15EADS in raid config (boot raid1) plus a raid1 LVM setup from a previous linux install (LVM system partitions formatted during first attempt of install)
[/LIST]
It's my old workstation that is ment to run as a small-home-office server.

I downloaded the ISO (ubuntu-10.04-server-amd64.iso), verified its checksum (found to be ok), burned it, verified the CD from inside the installer (found to be ok), tested the machines RAM (0 errors in 21 passes), tried to install it several times but always get the same error.

The /var/log/syslog file form the troubled section looks like this:

```
May  2 09:33:21 base-installer: info: kernel linux-generic usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-server usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-virtual usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-generic usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-server usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-virtual usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-2.6.32-21-virtual usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-2.6.32-21-server usable on amd64-k8
May  2 09:33:21 base-installer: info: kernel linux-image-2.6.32-21-generic usable on amd64-k8
May  2 09:33:21 base-installer: info: Using kernel 'linux-server'
May  2 09:33:21 base-installer: info: Setting do_initrd='yes'.
May  2 09:33:21 base-installer: info: Setting link_in_boot='no'.
May  2 09:33:21 base-installer: info: Available initramfs generator(s): 'initramfs-tools'
May  2 09:33:22 in-target: Reading package lists...
May  2 09:33:22 in-target: 
May  2 09:33:22 in-target: Building dependency tree...
May  2 09:33:22 in-target: 
May  2 09:33:22 in-target: Reading state information...
May  2 09:33:22 in-target: 
May  2 09:33:22 in-target: busybox-initramfs is already the newest version.
May  2 09:33:22 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
May  2 09:33:23 in-target: Reading package lists...
May  2 09:33:23 in-target: 
May  2 09:33:23 in-target: Building dependency tree...
May  2 09:33:23 in-target: 
May  2 09:33:23 in-target: Reading state information...
May  2 09:33:23 in-target: 
May  2 09:33:23 in-target: initramfs-tools is already the newest version.
May  2 09:33:23 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
May  2 12:35:55 in-target: Reading package lists...
May  2 12:35:55 in-target: 
May  2 12:35:55 in-target: Building dependency tree...
May  2 12:35:55 in-target: 
May  2 12:35:55 in-target: Reading state information...
May  2 12:35:55 in-target: 
May  2 12:35:55 in-target: The following extra packages will be installed:
May  2 12:35:55 in-target:   linux-firmware linux-image-2.6.32-21-server linux-image-server wireless-crda
May  2 12:35:55 in-target: Suggested packages:
May  2 12:35:55 in-target:   fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
May  2 12:35:55 in-target: Recommended packages:
May  2 12:35:55 in-target:   grub-pc grub lilo
May  2 12:35:55 in-target: The following NEW packages will be installed:
May  2 12:35:55 in-target:   linux-firmware linux-image-2.6.32-21-server linux-image-server linux-server
May  2 12:35:55 in-target:   wireless-crda
May  2 12:36:15 in-target: 0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
May  2 12:36:15 in-target: Need to get 0B/38.7MB of archives.
May  2 12:36:15 in-target: After this operation, 141MB of additional disk space will be used.
May  2 12:36:15 in-target: Selecting previously deselected package wireless-crda.
May  2 12:36:15 in-target: (Reading database ... 
May  2 12:36:15 in-target: 11545 files and directories currently installed.)
May  2 12:36:15 in-target: Unpacking wireless-crda (from .../wireless-crda_1.12_amd64.deb) ...
May  2 12:36:16 in-target: Selecting previously deselected package linux-image-2.6.32-21-server.
May  2 12:36:16 in-target: Unpacking linux-image-2.6.32-21-server (from .../linux-image-2.6.32-21-server_2.6.32-21.32_amd64.deb) ...
May  2 12:36:16 in-target: Done.

```
the trouble starts around here, I guess:
```

May  2 12:36:17 in-target: dpkg-deb: subprocess paste killed by signal (Broken pipe)
May  2 12:36:17 in-target: dpkg: error processing /cdrom//pool/main/l/linux/linux-image-2.6.32-21-server_2.6.32-21.32_amd64.deb (--unpack):
May  2 12:36:17 in-target:  short read in buffer_copy (backend dpkg-deb during `./boot/vmlinuz-2.6.32-21-server')
May  2 12:36:17 in-target: No apport report written because the error message indicates a dpkg I/O error
May  2 12:36:17 in-target: Selecting previously deselected package linux-firmware.
May  2 12:36:17 in-target: Unpacking linux-firmware (from .../linux-firmware_1.34_all.deb) ...
May  2 12:36:35 in-target: Selecting previously deselected package linux-image-server.
May  2 12:36:35 in-target: Unpacking linux-image-server (from .../linux-image-server_2.6.32.21.22_amd64.deb) ...
May  2 12:36:36 in-target: Selecting previously deselected package linux-server.
May  2 12:36:36 in-target: Unpacking linux-server (from .../linux-server_2.6.32.21.22_amd64.deb) ...
May  2 12:36:36 in-target: Errors were encountered while processing:
May  2 12:36:36 in-target:  /cdrom//pool/main/l/linux/linux-image-2.6.32-21-server_2.6.32-21.32_amd64.deb
May  2 12:36:36 in-target: E: 
May  2 12:36:36 in-target: Sub-process /usr/bin/dpkg returned an error code (1)
May  2 12:36:36 in-target: 
May  2 12:36:37 in-target: Reading package lists...
May  2 12:36:37 in-target: 
May  2 12:36:37 in-target: Building dependency tree...
May  2 12:36:37 in-target: 
May  2 12:36:37 in-target: Reading state information...
May  2 12:36:37 in-target: 
May  2 12:36:37 in-target: You might want to run `apt-get -f install' to correct these:
May  2 12:36:37 in-target: The following packages have unmet dependencies:
May  2 12:36:37 in-target:   linux-headers-server: Depends: linux-headers-2.6.32-21-server but it is not going to be installed
May  2 12:36:37 in-target:   linux-image-server: Depends: linux-image-2.6.32-21-server but it is not going to be installed
May  2 12:36:37 in-target: E: 
May  2 12:36:37 in-target: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
May  2 12:36:37 in-target:

```
and this is about the end of it:
```

May  2 12:36:37 base-installer: error: exiting on error base-installer/kernel/failed-install
```

I attach the complete syslog. The initialisation part could be interesting, but I find no severe error messages of the kernel. (except for some ACPI Errors: no handler for region [SACS]...)

I *guess* it's not hardware, because it happens at the same step, always. Could it be some BIOS setting? Some start-up parameters in the installer (noacpi)? What can I try to make it work??

kind regards,
Sulla

---

### Post by sulla on 2010-05-04
I tried it with AHCI mode on an off, no difference.

---

### Post by sulla on 2010-05-05
Installed Debian Lenny now, flawlessly. But I would like ubuntu 10.04, really. Any Ideas, what happens?

---

### Post by BoogeyOfTheMan on 2010-05-05
I know this is stupid, but have you tried burning another disc?

I'm in the process of installing 10.04 server on my old 766mhz celeron and was looking for possible issues I might encounter. Sadly, it seems you know more than I do, so the "burning a new disc" is the best idea I can come up with.

---

### Post by thornomad on 2010-07-06
Did you ever figure out what was wrong here ?  I am having the same issue -- have tried a number of different setups ... not sure what the error means, exactly.  Right now, am trying just to plow through even with the error and see what happens ...

---

### Post by sulla on 2010-08-08
Not quite. I had the memory test from a live-CD (ubuntu server 10.04) run for a couple of days, and it produced a memory error every ~100 passes. Over 8 errors there was a pattern, i.e. the memory addresses producing the error all ended in the same hex-values, they all ended in "...13ac". All errors were produced in test number 8, "modulo 20, random pattern". I then increased memory voltage and reduced the frequency of the ram from DDR333 to DDR266, and the errors went away.

However, for a test, I installed WindowsXP on the machine, and the "torture test" of prime95 always detects a "hardware error" after a few seconds (when running large FFT), without specifying what the error was. Weird, a bit. XP itslef ran smoothly.

What did I make of it? Well, the error of prime95 appeared much quicker than in the linux-memtest, but both software hint into the direction of RAM problems. My conclusion is it is definitely some hardware-issue. If I find a spare DDR module I might swap it into the machine and re-run the tests. I took the machine offline now.

regards,
sulla

---

