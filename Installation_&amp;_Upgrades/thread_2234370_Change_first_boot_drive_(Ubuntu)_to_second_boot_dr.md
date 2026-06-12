---
title: "Change first boot drive (Ubuntu) to second boot drive (Windows 7) in grub menu"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by SUPERFITTER on 2014-07-14
I have a duel boot Ubuntu 14.04 and Windows 7.  I would like to change the boot order, so Windows 7 comes up first and  Ubuntu 14.04 comes up second in the Grub menu. Both systems are on a 1Tb drive. Is this possible to do?
Thank You

---

### Post by slickymaster on 2014-07-14
Just take a read at [this]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order") and you'll be good to go.

---

### Post by oldfred on 2014-07-14
I do not recommend grub customizer anymore as in some cases it is adding its own scripts which can lead to issues. For a boot order change it should not add its scripts as it is a simple edit to grub.

       find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

Some other options are to move 30_custom script to 06_custom. But a major grub update may add a new 30_custom and the old 06 based version may not work. Or you can just copy 40_custom where you add your own entries to 06_custom. then copy the entire Windows boot stanza into 06_custom. Make sure it is executable.  You can also then turn off os-prober if desired as it only would be needed to look for new installs.

---

### Post by slickymaster on 2014-07-14
> **oldfred said:**
> I do not recommend grub customizer anymore as in some cases it is adding its own scripts which can lead to issues. For a boot order change it should not add its scripts as it is a simple edit to grub.

       find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

Wasn't aware of that oldfred. Thanks for the heads up.

---

### Post by SUPERFITTER on 2014-07-14
> **slickymaster said:**
> Wasn't aware of that oldfred. Thanks for the heads up.

I was toooo fast and installed grub customizer and changed the order with win 7 first and Ubuntu 14.04 last, how do I fix the problem? Or should I let it go?

---

### Post by oldfred on 2014-07-14
If it is working that is fine. I would not worry, but if you have issues later, you may need to totally uninstall grub & reinstall it to rewrite all files. 
You can check if customizer added its own scripts:
sudo ls -l /etc/grub.d

And see what edit it did to grub.
 cat /etc/default/grub



Its just we get users with issues, probably after a major grub2 update where grub adds new scripts and older one's from customizer then may not work or it sees both and doubles entries. I think customizer backs up or changes execute bit so standard scripts do not run.

---

### Post by SUPERFITTER on 2014-07-14
I got this when I ran your script:

```
 dennis@dennis1:~$ sudo ls -l /etc/grub.d
[sudo] password for dennis: 
total 88
-rwxr-xr-x 1 root root  9424 Apr 11 06:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 11:58 05_debian_theme
-rwxr-xr-x 1 root root   920 Jul 14 11:38 10_linux_proxy
-rwxr-xr-x 1 root root 11692 Apr 11 06:51 30_os-prober
-rwxr-xr-x 1 root root   919 Jul 14 11:38 31_linux_proxy
-rwxr-xr-x 1 root root 10412 Apr 11 06:51 32_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 08:31 33_memtest86+
-rwxr-xr-x 1 root root   919 Jul 14 11:38 36_linux_proxy
-rwxr-xr-x 1 root root  1416 Apr 11 06:51 37_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 06:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 06:51 41_custom
drwxr-xr-x 4 root root  4096 Jul 14 11:28 backup
drwxr-xr-x 2 root root  4096 Jul 14 11:28 bin
drwxr-xr-x 2 root root  4096 Jul 14 11:38 proxifiedScripts
-rw-r--r-- 1 root root   483 Apr 11 06:51 README
dennis@dennis1:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
dennis@dennis1:~$ 
```
 
Is there a way to uninstall grub customizer?  If I uninstall it it may leave the grub menu the way I want it and I will not have any future problems with grub customizer?

---

### Post by oldfred on 2014-07-14
All the proxy files are from grub customizer. And it created several folders, backup, bin, & proxifiedscripts.

And it looks like rather than the relatively simple edit of grub's default it modified one of the scripts to change the default. So you cannot uninstall it without starting all over.

I would just leave it for now. If it is working better not to create more issues.

Make sure you always have a current version live installer so you can make repairs later if need be. You should have that for every installed system anyway.

I think you have to uninstall grub customizer, but then totally purge grub and reinstall it. You can do that if booted into your system. Or if broken you have to chroot into it or use Supergrub to boot.

Easier with Boot-Repair installed to liveDVD or flash drive to chroot as it walks you thru it, and you have to make sure Internet is working as it has to download a new copy of grub. While uninstalled you cannot boot at all with internal system until new copy is installed.

---

### Post by SUPERFITTER on 2014-07-14
Thanks Oldfred
I will leave it as is and if I run into future problems, I will repost for solutions to those problems.

---

