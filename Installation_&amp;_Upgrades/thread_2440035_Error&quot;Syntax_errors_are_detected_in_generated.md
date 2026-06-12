---
title: "Error:&quot;Syntax errors are detected in generated GRUB config file&quot; | Ubuntu 18.04"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by richucj on 2020-04-05
Hi All,
I keep getting the same error message each time I run  "sudo apt-get upgrade" command: in my ubuntu 18.04.

```
dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-4.15.0-45-generic (4.15.0-45.48) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-45-generic
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found linux image: /boot/vmlinuz-4.15.0-43-generic
Found initrd image: /boot/initrd.img-4.15.0-43-generic
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Adding boot menu entry for EFI firmware configuration
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 145
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.15.0-45-generic (--configure):
 installed linux-image-4.15.0-45-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-4.15.0-43-generic (4.15.0-43.46) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-43-generic
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found linux image: /boot/vmlinuz-4.15.0-43-generic
Found initrd image: /boot/initrd.img-4.15.0-43-generic
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Adding boot menu entry for EFI firmware configuration
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 145
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.15.0-43-generic (--configure):
 installed linux-image-4.15.0-43-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for linux-image-4.15.0-91-generic (4.15.0-91.92) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-91-generic
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found linux image: /boot/vmlinuz-4.15.0-43-generic
Found initrd image: /boot/initrd.img-4.15.0-43-generic
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Adding boot menu entry for EFI firmware configuration
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 145
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-4.15.0-91-generic (--configure):
 installed linux-image-4.15.0-91-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 grub-efi-amd64
 grub-efi-amd64-signed
 friendly-recovery
 shim-signed
 linux-image-4.15.0-45-generic
 linux-image-4.15.0-43-generic
 linux-image-4.15.0-91-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

getting the error after upgrading ubuntu 16.04 to 18.04 and I got a message  after the upgrade  finished "[COLOR=#ff0000]the upgrade completed but there were errors[/COLOR]"
I can't even run boot-repair.I get the same error while trying to install boot repair.
please support.
regards,
Richu

---

### Post by webaake on 2020-04-05
```
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
```

There's probably a mismatch in grub config files. I suspect that your old /etc/default/grub still is in use and that it's not compatible with the new version of grub. As your error message said you have  a new file called " grub.cfg.new" - compare that with /etc/default/grub.

Maybe you can post your /etc/default/grub here?

---

### Post by richucj on 2020-04-05
> **webaake said:**
> ```
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
```

There's probably a mismatch in grub config files. I suspect that your old /etc/default/grub still is in use and that it's not compatible with the new version of grub. As your error message said you have  a new file called " grub.cfg.new" - compare that with /etc/default/grub.

Maybe you can post your /etc/default/grub here?


Hi Webaake,
Thank you for your prompt reply.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivsr_i0apic{32}=00:14.0"
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


```
these is the grub file in /etc/default/grub

---

### Post by deadflowr on 2020-04-05
It shouldn't be i0apci but ioapic
From 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivsr_i0apic{32}=00:14.0"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivsr_ioapic{32}=00:14.0"
```
replace the zero with a small letter O, as in o as in own.
But that's just one thing, there may be others.

---

### Post by webaake on 2020-04-05
Thanks to deadflowr you can now try to rebuild it with:

```
sudo update-grub
```

and see what happens.

---

### Post by richucj on 2020-04-05
still getting the same syntax error
```
richucj@richucj-Vostro-15-3568:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-91-generic
Found initrd image: /boot/initrd.img-4.15.0-91-generic
Found linux image: /boot/vmlinuz-4.15.0-45-generic
Found initrd image: /boot/initrd.img-4.15.0-45-generic
Found linux image: /boot/vmlinuz-4.15.0-43-generic
Found initrd image: /boot/initrd.img-4.15.0-43-generic
Found linux image: /boot/vmlinuz-4.15.0-39-generic
Found initrd image: /boot/initrd.img-4.15.0-39-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Adding boot menu entry for EFI firmware configuration
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 145
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
```

---

### Post by deadflowr on 2020-04-05
The /boot/grub/grub.cfg.new file has the exact issue, best to post it to pastebin rather than here since the file can be rather fat.
Just copy that file and paste it here: [https://paste.ubuntu.com/]("https://paste.ubuntu.com/")
Then post a link to it for us.

Hope it make sense.

---

### Post by richucj on 2020-04-05
pls follow the link:[https://paste.ubuntu.com/p/ZfmkrtBFxf/](https://paste.ubuntu.com/p/ZfmkrtBFxf/)

---

### Post by deadflowr on 2020-04-05
Okay, looks like it's the wrong brackets.
should be [32] not (32)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivsr_ioapic{32}=00:14.0"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivsr_ioapic[32]=00:14.0"
```

---

### Post by richucj on 2020-04-05
Thanks, deadflowr issue solved

---

### Post by mörgæs on 2020-04-05
Good, please mark the thread solved.

---

