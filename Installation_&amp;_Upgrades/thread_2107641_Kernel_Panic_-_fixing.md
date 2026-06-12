---
title: "Kernel Panic - fixing"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by Potetsjokolade on 2013-01-22
Hello, first of all i just want to tell you that I'm very new to the Linux world, so please be patient.

Ok, so here is my problem. I tried to update my server through webmin, and it all failed, so i though, "hey, just forget it", so i cancled it.

When I'm trying to boot into "12.04.1 LTS (GNU/Linux 3.2.0-3x-generic x86_64)" (x = can't remember) I get kernel panic (kernel panic - not syncing: VFS: unable to mount root fs on unkonwn wn-block), so I've tried to boot into a older kernel, which worked (12.04.1 LTS (GNU/Linux 3.2.0-32-generic x86_64).

Now I want to get back to normal, and by that I mean that it automaticly boots into the newest kernel installed, without getting kernel panic.. Any ideas? I've tried the rescue disc, but i don't know how to find out where my root folder is ( not '/' but:

device to use as root file sytem: 
/dev/sda1 
/dev/sda5
/dev/Server/root
/dev/Server/swap_1
Assemble RAID array)

When I booted into kernel 32, was met with "/boot is using 97.8% of 227MB". And when I tried to apt-get update and apt-get upgrade and I got:


> 
(Reading database ... 256062 files and directories are for the moment installed.)
Makes clear to replace mysql-client 5.5.28-0ubuntu0.12.04.3 (using ... / mysql-client_5.5.29-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-client ...
Makes clear to replace mysql-client-5.5 5.5.28-0ubuntu0.12.04.3 (using ... / mysql-client-5.5_5.5.29-0ubuntu0.12.04.1_amd64.deb) .. .
Unpacking replacement mysql-client-5.5 ...
Makes clear to replace mysql-client-core-5.5 5.5.28-0ubuntu0.12.04.3 (using ... / mysql-client-core-5.5_5.5.29-0ubuntu0.12.04.1_amd64. deb) ...
Unpacking replacement mysql-client-core-5.5 ...
Processing trigger Sere for man-db ...
Setting up mysql-common (5.5.29-0ubuntu0.12.04.1) ...
(Reading database ... 256062 files and directories are for the moment installed.)
Makes clear to replace mysql-server-5.5 5.5.28-0ubuntu0.12.04.3 (using ... / mysql-server-5.5_5.5.29 0ubuntu0.12.04.1_amd64.deb) .. .
mysql stop / waiting
Unpacking replacement mysql-server-5.5 ...
Makes clear to replace mysql-server-core-5.5 5.5.28-0ubuntu0.12.04.3 (using ... / mysql-server-core-5.5_5.5.29-0ubuntu0.12.04.1_amd64. deb) ...
Unpacking replacement mysql-server-core-5.5 ...
Makes clear to replace php5-cli 3.5.10-1ubuntu3.4 (using ... / php5-cli_5.3.10-1ubuntu3.5_amd64.deb) ...
Unpacking replacement php5-cli ...
Makes clear to replace php5-mysql 3.5.10-1ubuntu3.4 (using ... / php5-mysql_5.3.10-1ubuntu3.5_amd64.deb) ...
Unpacking replacement php5-mysql ...
Makes clear to replace php5-gd 5.3.10-1ubuntu3.4 (using ... / php5-gd_5.3.10-1ubuntu3.5_amd64.deb) ...
Unpacking replacement php5-gd ...
Makes clear to replace libapache2-mod-php5 5.3.10-1ubuntu3.4 (using ... / libapache2-mod-php5_5.3.10-1ubuntu3.5_amd64.deb) ...
Unpacking replacement libapache2-mod-php5 ...
Makes clear to replace php5-common 3.5.10-1ubuntu3.4 (using ... / php5-common_5.3.10-1ubuntu3.5_amd64.deb) ...
Unpacking replacement php5-common ...
Processing trigger Sere for man-db ...
Processing trigger Sere for ureadahead ...
ureadahead will be reprofiled Wed next reboot
Setting up libgl1-mesa-dri (8.0.4-0ubuntu0.3) ...
Sets up libglapi-mesa (8.0.4-0ubuntu0.3) ...
Setting up libgl1-mesa-glx (8.0.4-0ubuntu0.3) ...
Setting up libmysqlclient18 (5.5.29-0ubuntu0.12.04.1) ...
Sets up TSconfig (1.0 to 10) ...
Sets up libts-0.0-0 (1.0-10) ...
Setting up linux-image-3.2.0-34-generic (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining / etc / kernel / postinst.d.
run-parts: executing / etc / kernel / postinst.d / initramfs-tools 3.2.0-34-generic / boot/vmlinuz-3.2.0-34-generic
update-initramfs: Generating / boot/initrd.img-3.2.0-34-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for / boot/initrd.img-3.2.0-34-generic with 1
run-parts: / etc / kernel / postinst.d / initramfs-tools Exited with return code 1
Failed to process / etc / kernel / postinst.d that / var/lib/dpkg/info/linux-image-3.2.0-34-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic (- configure):
*during the process installed post-installation script returned error status 2
Setting up linux-image-3.2.0-35-generic (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link / initrd.img is a dangling linkto / boot/initrd.img-3.2.0-34-generic
Examining / etc / kernel / postinst.d.
run-parts: executing / etc / kernel / postinst.d / initramfs-tools 3.2.0-35-generic / boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating / boot/initrd.img-3.2.0-35-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for / boot/initrd.img-3.2.0-35-generic with 1
run-parts: / etc / kernel / postinst.d / initramfs-tools Exited with return code 1
Failed to process / etc / kernel / postinst.d that / var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic (- configure):
*during the process installed post-installation script returned error status 2
dpkg: dependency problems prevent configuration of linux-image-server:
*linux-image-server requires linux-image-3.2.0-34-generic. But:
**Package linux-image-3.2.0-34-generic is not configured yet.
dpkg: error processing linux-image-server (- configure):
*dependency problems - do not set up package
dpkg: dependency problems prevent configuration of linux-server:
*linux server requires linux-image-server (= 3.2.0.34.37). But:
**Package linux-image-server is not configured yet.
dpkg: error processing linux-server (- configure):
*dependency problems - do not set up package
Setting up mysql-client-core-5.5 (5.5.29-0ubuntu0.12.04.1) ...
No apport report written because the error message indicates that it is a feel lgefeil from a previous failure.
*********************************************************************************************************No apport report written for MaxReports already is reached
***************************************************Setting up mysql-client-5.5 (5.5.29-0ubuntu0.12.04.1) ...
Setting up mysql-client (5.5.29-0ubuntu0.12.04.1) ...
Setting up mysql-server-core-5.5 (5.5.29-0ubuntu0.12.04.1) ...
Setting up mysql-server-5.5 (5.5.29-0ubuntu0.12.04.1) ...
mysql start / running, process 20040
Setting up mysql-server (5.5.29-0ubuntu0.12.04.1) ...
Setting up php5-common (3.5.10-1ubuntu3.5) ...
Setting up php5-cli (3.5.10-1ubuntu3.5) ...
Setting up libapache2-mod-php5 (5.3.10-1ubuntu3.5) ...
** Reloading web server config apache2 apache2: Could not reliably determining the server's fully qualified domain name, overusing 127.0.1.1 for ServerName
************************************************************************************************************[OK]
Setting up php5-mysql (5.3.10-1ubuntu3.5) ...
Setting up php5-gd (3.5.10-1ubuntu3.5) ...
Processing trigger Sere for libc-bin ...
ldconfig deferred processing now taking place
Errors occurred in the treatment of:
*linux-image-3.2.0-34-generic
*linux-image-3.2.0-35-generic
*linux-image-server
*linux server
E: Sub-process / usr / bin / dpkg returned an error code (1)


the quote was run trough Google translate for translation.

I really hope you can help me, and if you need more information I'd be happy to provide, just tell me.

Excuse me for bad English

Thanks.

---

### Post by dino99 on 2013-01-22
the good news: you still have at least one kernel that is booting normally.

about the latest faulty kernel:
- watch the logs to find usefull errors logged (.xsession-errors & /var/log/)
- remove "quiet splash" from /etc/default/grub, then update grub (sudo update-grub) . This will let you see the verbose boot mode, to know what happens when you get that panic.

---

### Post by Potetsjokolade on 2013-01-22
> **dino99 said:**
> the good news: you still have at least one kernel that is booting normally.

about the latest faulty kernel:
- watch the logs to find usefull errors logged (.xsession-errors & /var/log/)
- remove "quiet splash" from /etc/default/grub, then update grub (sudo update-grub) . This will let you see the verbose boot mode, to know what happens when you get that panic.

When i do sudo upgrade-grub I get the following:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.0.0-22-server
Found initrd image: /boot/initrd.img-3.0.0-22-server
Found linux image: /boot/vmlinuz-2.6.38-15-server
Found initrd image: /boot/initrd.img-2.6.38-15-server
Found memtest86+ image: /memtest86+.bin
done

```

and in the grub file @ /etc/default/grub I have this. Did you want me to remove "GRUB_HIDDEN_TIMEOUT_QUIET=true"?


> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by Cheesehead on 2013-01-22
> **Potetsjokolade said:**
> When I booted into kernel 32, was met with "/boot is using 97.8% of 227MB"

Seems like your /boot drive is out of space.

When you upgrade or otherwise change kernels, the system creates a large initrd file customized for the new kernel. At boot, the system uses that initrd file to begin loading the system.

Since your /boot drive is out of space, here's the failure message when initrd gets created, but cannot be written to /boot:
> Examining / etc / kernel / postinst.d.
run-parts: executing / etc / kernel / postinst.d / initramfs-tools 3.2.0-34-generic / boot/vmlinuz-3.2.0-34-generic
update-initramfs: Generating / boot/initrd.img-3.2.0-34-generic

gzip: stdout: No space left on device

You have the new kernel, but not the initrd file, so the boot fails.
When you fallback to an older kernel, it's own older initrd file is already on your /boot drive, so the boot succeeds.

You can clean out older kernels and initrds to make space (keep at least one that works!)
Or you can increase the size of your /boot partition.
Or...well, you have lots of options to fix it.

---

### Post by Potetsjokolade on 2013-01-22
> **Cheesehead said:**
> Seems like your /boot drive is out of space.

When you upgrade or otherwise change kernels, the system creates a large initrd file customized for the new kernel. At boot, the system uses that initrd file to begin loading the system.

Since your /boot drive is out of space, here's the failure message when initrd gets created, but cannot be written to /boot:


You have the new kernel, but not the initrd file, so the boot fails.
When you fallback to an older kernel, it's own older initrd file is already on your /boot drive, so the boot succeeds.

You can clean out older kernels and initrds to make space (keep at least one that works!)
Or you can increase the size of your /boot partition.
Or...well, you have lots of options to fix it.

Thanks! I'll try that, so if I want to delete a kernel, which files do I delete, I see there are many files in /boot. 

Additionaly, when I delete some very old kernels, and boots into the kernel that works should I then do apt-get upgrade ?

Edit: so I can pair them right, and not delete any other files

---

### Post by Potetsjokolade on 2013-01-22
Everything is fixed now: **_Solution, remove old kernels in /boot_**

---

