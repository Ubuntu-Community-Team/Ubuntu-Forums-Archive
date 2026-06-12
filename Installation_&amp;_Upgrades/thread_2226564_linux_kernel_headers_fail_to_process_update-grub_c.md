---
title: "linux kernel headers fail to process update-grub correctly"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Daniel_McClanahan on 2014-05-28
Hey,

I don't know what incited this; I manually installed a .deb package (just some scientific software, unrelated), and then get this response after running dpkg -i:
```
danny@pimpbox ~ &#9880; sudo apt-get -f install                         $? 1 23:24:56
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.11.0-20-generic linux-image-extra-3.11.0-20-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 184 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 378073 files and directories currently installed.)
Removing linux-image-extra-3.11.0-20-generic (3.11.0-20.35) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.11.0-20-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.11.0-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.11.0-20-generic (3.11.0-20.35) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.11.0-20-generic.postrm line 328.
dpkg: error processing package linux-image-3.11.0-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.11.0-20-generic
 linux-image-3.11.0-20-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
sudo apt-get -f install  3.22s user 2.27s system 65% cpu 8.343 total
```

I looked at the offending file /etc/kernel/postrm.d/zz-update-grub, and have no clue how to analyze it. It's here, if that matters.
```
#! /bin/sh
set -e

which update-grub >/dev/null 2>&1 || exit 0

if type running-in-container >/dev/null 2>&1 && \
   running-in-container >/dev/null; then
    exit 0
fi

set -- $DEB_MAINT_PARAMS
mode="${1#\'}"
mode="${mode%\'}"
case $0:$mode in
    # Only run on postinst configure and postrm remove, to avoid wasting
    # time by calling update-grub multiple times on upgrade and removal.
    # Also run if we have no DEB_MAINT_PARAMS, in order to work with old
    # kernel packages.
    */postinst.d/*:|*/postinst.d/*:configure|*/postrm.d/*:|*/postrm.d/*:remove)
    if [ -e /boot/grub/grub.cfg ]; then
        exec update-grub
    fi
    ;;
esac

exit 0
```

What does this issue even mean? I wouldn't be worried about it if it didn't stop me from installing any packages or updating grub at all.

Also, update-grub's output is weird:
```
danny@pimpbox /boot/grub &#9880; sudo update-grub                       $? 1 23:35:39
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
danny@pimpbox /boot/grub &#9880;
```
Usually there's a lot more text? It just stops and returns to the command line after those two lines.

I've tried purging and removing the linux headers, but it always fails, since update-grub is called upon removing the headers, and update-grub fails, as shown above.

I'm running 64-bit Ubuntu 14.04. Thanks!

---

### Post by Daniel_McClanahan on 2014-05-29
I got annoyed and saw what would happen if I started deleting things; luckily, it didn't seem to cause too much harm. I tried to remove the offending files from /var/lib/dpkg/info, since I had later kernels installed already.
```
danny@pimpbox /var/lib/dpkg/info &#9880; ls linux-image-*3.11*               15:35:14
-rw-r--r-- 1 root root    0 May 29 15:34 linux-image-3.11.0-20-generic.list
-rw-r--r-- 1 root root  68k May  2 17:09 linux-image-3.11.0-20-generic.md5sums
-rwxr-xr-x 1 root root  39k May  2 17:02 linux-image-3.11.0-20-generic.postinst*
-rwxr-xr-x 1 root root  14k May  2 17:02 linux-image-3.11.0-20-generic.postrm*
-rwxr-xr-x 1 root root  12k May  2 17:02 linux-image-3.11.0-20-generic.preinst*
-rwxr-xr-x 1 root root  12k May  2 17:02 linux-image-3.11.0-20-generic.prerm*
-rw-r--r-- 1 root root    0 May 29 15:34 linux-image-extra-3.11.0-20-generic.list
-rw-r--r-- 1 root root 344k May  2 17:09 linux-image-extra-3.11.0-20-generic.md5sums
-rwxr-xr-x 1 root root  39k May  2 17:02 linux-image-extra-3.11.0-20-generic.postinst*
-rwxr-xr-x 1 root root  14k May  2 17:02 linux-image-extra-3.11.0-20-generic.postrm*


danny@pimpbox /var/lib/dpkg/info &#9880; sudo rm -f linux-image-*3.11*

```

However, it ended up having the exact same problem as before, only with the most recent version of the kernel image, linux-image-3.13.0-27-generic.
```
danny@pimpbox /var/lib/dpkg/info &#9880; sudo dpkg --configure linux-image-3.13.0-27-generic
Setting up linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-27-generic
) points to /boot/initrd.img-3.13.0-27-generic
 (/boot/initrd.img-3.13.0-27-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-27-generic
) points to /boot/vmlinuz-3.13.0-27-generic
 (/boot/vmlinuz-3.13.0-27-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.13.0-27-generic
sudo dpkg --configure linux-image-3.13.0-27-generic  9.15s user 7.67s system 106% cpu 15.834 total

```

It complains about various errors at certain lines, and while I checked the file, I still don't really get what it's doing.
/var/lib/dpkg/info/linux-image-3.13.0-27-generic.postinst line 1025 is this:
```
if (-d "/etc/kernel/postinst.d") {
  print STDERR "Examining /etc/kernel/postinst.d.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " . [[[this is line 1025]]]]
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
}

```

However, it looks like the previous linux image was removed from the system (3.11.0-20 is no longer listed):
```
danny@pimpbox /var/lib/dpkg/info &#9880; dpkg --list | grep linux-image                                                                                                                                           15:39:25
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-49-generic                          3.5.0-49.74                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-29-generic                          3.8.0-29.42~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-35-generic                          3.8.0-35.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                          3.8.0-36.52~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                          3.8.0-37.53~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                          3.8.0-38.56~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-39-generic                          3.8.0-39.58~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-49-generic                    3.5.0-49.74                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP

```

Definitely don't want to delete any more headers, though, I'd prefer my system to run if at all possible.

---

### Post by oldfred on 2014-05-29
Did you fully update to trusty? That would be kernel 3.13 and 3.11 is from Saucy.

Any kernels older than 3.13 should be removed from your system if really on trusty and after an upgrade they may be be in dpkg to delete anymore the standard ways.

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

      
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by Daniel_McClanahan on 2014-05-29
```
danny@pimpbox ~ &#9880; uname -a                                             18:10:36
Linux pimpbox 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
danny@pimpbox ~ &#9880; uname -r                                             18:12:29
3.13.0-24-generic
danny@pimpbox ~ &#9880; ls /boot/vmlinuz*                               $? 1 18:12:50
-rw------- 1 root root 5.8M May  2 19:30 /boot/vmlinuz-3.13.0-24-generic
-rw------- 1 root root 5.8M May 15 14:07 /boot/vmlinuz-3.13.0-27-generic

```

The chroot adventure also returned very little.
```
root@pimpbox:~# sudo apt-get purge linux-image-extra-3.5.0-49-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-24-generic linux-image-3.13.0-27-generic linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-27-generic linux-image-extra-3.5.0-49-generic*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 386 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 368953 files and directories currently installed.)
Removing linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-27-generic (3.13.0-27.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-27-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-27-generic (3.13.0-27.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
Generating grub configuration file ...
Found background: /usr/share/desktop-base/bugpokemondesktop.jpg
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-27-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-24-generic
 linux-image-3.13.0-24-generic
 linux-image-extra-3.13.0-27-generic
 linux-image-3.13.0-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@pimpbox:~# dpkg --list | grep linux-image
rH  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-49-generic                    3.5.0-49.74                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
root@pimpbox:~# 
```
I suppose I am glad that it didn't end up deleting my current kernels, that would have been extremely annoying.

One thing I did notice: I modified my /etc/kernel/postinst.d/zz-update-grub, commenting out the if block:
```
#! /bin/sh
set -e

which update-grub >/dev/null 2>&1 || exit 0

if type running-in-container >/dev/null 2>&1 && \
   running-in-container >/dev/null; then
    exit 0
fi

set -- $DEB_MAINT_PARAMS
mode="${1#\'}"
mode="${mode%\'}"
case $0:$mode in
    # Only run on postinst configure and postrm remove, to avoid wasting
    # time by calling update-grub multiple times on upgrade and removal.
    # Also run if we have no DEB_MAINT_PARAMS, in order to work with old
    # kernel packages.
    */postinst.d/*:|*/postinst.d/*:configure|*/postrm.d/*:|*/postrm.d/*:remove)
#    if [ -e /boot/grub/grub.cfg ]; then
#        exec update-grub
#    fi
    ;;
esac

exit 0
```
This actually allowed me to install packages again! So it appears there is a problem with the update-grub script itself, which as shown before is essentially a no-op right now for reasons unknown. However, I then tried to see if this would make the commands you specified work; it didn't, giving the same issue as before.

I looked more closely at the offending files, though, and found there was a portion (at around line 328) that explicitly commanded the installation to go belly-up. I'm sure there was a very good reason for them being there, but they were screwing up my install, so I tried commenting them out. The section is this, in **/var/lib/dpkg/info/linux-image{-extra,}-3.13.0-{24,27}-generic.post{inst,rm}**:
```
#if (-d "/etc/kernel/postinst.d") {
#  print STDERR "Examining /etc/kernel/postinst.d.\n";
#  system ("run-parts --verbose --exit-on-error --arg=$version " .
#          "--arg=$realimageloc$kimage-$version " .
#          "/etc/kernel/postinst.d") &&
#            die "Failed to process /etc/kernel/postinst.d";
#}
#
#if (-d "/etc/kernel/postinst.d/$version") {
#  print STDERR "Examining /etc/kernel/postinst.d/$version.\n";
#  system ("run-parts --verbose --exit-on-error --arg=$version " .
#          "--arg=$realimageloc$kimage-$version " .
#          "/etc/kernel/postinst.d/$version") &&
#            die "Failed to process /etc/kernel/postinst.d/$version";
#}
```

They weren't commented out previously, I commented them out myself. After commenting out that section for all the files matching the regular expression above, using those commands and purging previous kernels worked fine. So that problem is solved.

The problem remains, though, that my update-grub script isn't working. My /etc/default/grub is this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_BACKGROUND="/usr/share/desktop-base/bugpokemondesktop.jpg"

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


```

I'm not sure what among there might cause it not to update. As shown before, it merely recognizes the found background image, then stops. Are there any issues in other files that could be causing it to fail?

---

### Post by oldfred on 2014-05-29
If you take background image out does it work? Comment it back out & update-grub.

It it then works.
Then the path may not be correct. The message on found may be just that it is trying to look for that file. And if not actually found it crashes?

---

### Post by ubfan1 on 2014-05-30
I took a look at my system which had been updated from 12.04 to 14.04 and found several obsolete and orphaned packages, including kernel packages.  Intall deborphan (and maybe aptitude) to list/remove such packages, which the apt-get autoremove does not touch.  That might help things out.
Take a look at [http://askubuntu.com/questions/47399...ading-to-14-04]("http://askubuntu.com/questions/473996/how-do-i-remove-obsolete-packages-after-upgrading-to-14-04")  
and [http://askubuntu.com/questions/28694...haned-packages]("http://askubuntu.com/questions/286947/obsolete-packages-vs-orphaned-packages")

---

### Post by Daniel_McClanahan on 2014-05-31
> **oldfred said:**
> If you take background image out does it work? Comment it back out & update-grub.

It it then works.
Then the path may not be correct. The message on found may be just that it is trying to look for that file. And if not actually found it crashes?

Good catch; I tried that, but it seemed not to have had an effect on the process.

[QUOTE=ubfan1]I took a look at my system which had been updated from 12.04 to 14.04  and found several obsolete and orphaned packages, including kernel  packages.  Intall deborphan (and maybe aptitude) to list/remove such  packages, which the apt-get autoremove does not touch.  That might help  things out.
Take a look at [http://askubuntu.com/questions/47399...ading-to-14-04]("http://askubuntu.com/questions/473996/how-do-i-remove-obsolete-packages-after-upgrading-to-14-04")  
and [http://askubuntu.com/questions/28694...haned-packages]("http://askubuntu.com/questions/286947/obsolete-packages-vs-orphaned-packages")[/QUOTE]

This would likely have been a very good idea, if curiosity hadn't brutally slaughtered the cat before I was able to look at your comment. I ended up playing around a bit more and crashed my system. Luckily I was  able to reinstall and restore from backup. No clue what was up; I was  playing with installing a legacy version of fglrx beforehand, with lots of  installation issues, so that might definitely have been a factor; I forgot to mention that above. It never showed up in the error messages, so I ended up forgetting about it.

Thanks to everyone who commented, I really appreciate the help. If I ever try to install legacy fglrx again (likely) I'll take a look at this thread again if/when something goes wrong. Marking as solved since there's no further analysis to be done at this point.

---

