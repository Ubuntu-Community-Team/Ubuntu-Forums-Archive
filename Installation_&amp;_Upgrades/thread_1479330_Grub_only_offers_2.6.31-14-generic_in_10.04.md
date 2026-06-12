---
title: "Grub only offers 2.6.31-14-generic in 10.04"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by blue_bullet on 2010-05-10
I can only boot 10.04 in an old kernel.  I have managed to get myself completely confused.  This all started last week when an update messed up my nVidia setting and for some strange reason destroyed my email in Thunderbird.  I have recovered the email but am having to boot ubuntu in limited graphics mode.  Here is some output from issuing the sudo update-grub command in a terminal window:  Grub (or Grub 2) seems to be finding the newer kernels, but they are never offered when I reboot.  Can anyone point me in the right direction? 

rob@fargo:~$ uname -a
Linux fargo 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
rob@fargo:~$ sudo update-grub
[sudo] password for rob: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

rob@fargo:~$

---

### Post by davidmohammed on 2010-05-10
try the following

gksudo /etc/default/grub

change the default value to 0 and then save the file

then

sudo update-grub

reboot.

---

### Post by blue_bullet on 2010-05-10
> **davidmohammed said:**
> try the following

gksudo /etc/default/grub

change the default value to 0 and then save the file

then

sudo update-grub

reboot.

I did gksu gedit /etc/default/grub instead.
Default value is already set to 0.

Here is what my grub file looks like:

rob@fargo:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=792 splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
rob@fargo:~$

---

### Post by davidmohammed on 2010-05-10
hmmm - I note when you do a update-grub it says

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

I don't have this on my system probably because its a fresh install.

try renaming menu.lst to menu.lst.bak and rerunning sudo update-grub.

---

### Post by blue_bullet on 2010-05-10
> **davidmohammed said:**
> hmmm - I note when you do a update-grub it says

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

I don't have this on my system probably because its a fresh install.

try renaming menu.lst to menu.lst.bak and rerunning sudo update-grub.

Good catch.  I did that and update-grub said it could not find it and offered to create it.  I said no and rebooted.  Still the old kernel 2.6.31-14-generic (and recovery mode) is the only kernel offered.  I did an upgrade from 9.10 to 10.04 rather than a fresh install.  I have backed up my home directory to an external hd so I may just try a fresh install and get my data back from the external hd.  

This is what I get when running update-grub:


> rob@fargo:~$ sudo update-grub
[sudo] password for rob: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

rob@fargo:~$ 


---

### Post by davidmohammed on 2010-05-10
does this thread help you?

[http://ubuntuforums.org/showthread.php?t=1457636&page=2]("http://ubuntuforums.org/showthread.php?t=1457636&page=2")

---

### Post by blue_bullet on 2010-05-10
Yes, it did fix the problem.  Thank you very much for your help.

Using your suggestion to get rid of the menu.lst file and issuing 

> sudo grub-mkconfig -o /boot/grub/grub.cfg

per the thread fixed everything.  Newer kernels are now available and nVidia problems were eliminated when I rebooted.  

Thank you again for your help.

---

