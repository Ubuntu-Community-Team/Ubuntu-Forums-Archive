---
title: "linux-image post-removal script subprocess returned error exit status 1"
date: 2020-10-25
forum: Installation &amp; Upgrades
---

### Post by AndrewMcNZ on 2020-10-25
Hi All

I have recently upgraded from 18.04 LTS to 20.04 LTS. During the upgrade, there were errors to do with removing an old kernel.
If I run Synaptic, and select Broken dependencies, there is one package listed: [FONT=Courier New]linux-image-4.15.0-117-generic[/FONT]
The linux-image is marked for complete removal and cannot be un-marked. If I Apply the changes, then the details windows has the output shown below.

Although I have used Ubuntu LTS releases for many years, they have always just worked and so I have little experience in fixing issues such as the one I have now.
In the output below I can see a number of errors, including "/etc/grub.d/25_custom_proxy: 3: /etc/grub.d/bin/grubcfg_proxy: not found" and "installed linux-image-4.15.0-117-generic package post-removal script subprocess returned error exit status 1". I am guessing that we can ignore the "cryptsetup: WARNING: Option 'size' missing in crypttab" error for now.

Can anyone suggest what I should do next? I have searched the forums for answers but haven't found anything that works. If someone can point me to a relevant thread, I would appreciate that.

Cheers
Andrew Mc

```

(Reading database ... 300694 files and directories currently installed.)
Removing linux-image-4.15.0-117-generic (4.15.0-117.118) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-117-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Found linux image: /boot/vmlinuz-5.4.0-51-generic
Found initrd image: /boot/initrd.img-5.4.0-51-generic
Found linux image: /boot/vmlinuz-5.4.0-48-generic
Found initrd image: /boot/initrd.img-5.4.0-48-generic
Found linux image: /boot/vmlinuz-4.15.0-118-generic
Found initrd image: /boot/initrd.img-4.15.0-118-generic
/etc/grub.d/25_custom_proxy: 3: /etc/grub.d/bin/grubcfg_proxy: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-117-generic (--remove):
 installed linux-image-4.15.0-117-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-4.15.0-117-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-5.4.0-52-generic (5.4.0-52.57) ...
Setting up linux-image-5.4.0-51-generic (5.4.0-51.56) ...
Processing triggers for linux-image-5.4.0-52-generic (5.4.0-52.57) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-52-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-52-generic
cryptsetup: WARNING: Option 'size' missing in crypttab for plain dm-crypt 
    mapping cryptswap1. Please read 
    /usr/share/doc/cryptsetup-initramfs/README.initramfs.gz and add the correct 
    'size' option to your crypttab(5).
cryptsetup: WARNING: Resume target cryptswap1 uses a key file
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Found linux image: /boot/vmlinuz-5.4.0-51-generic
Found initrd image: /boot/initrd.img-5.4.0-51-generic
Found linux image: /boot/vmlinuz-5.4.0-48-generic
Found initrd image: /boot/initrd.img-5.4.0-48-generic
Found linux image: /boot/vmlinuz-4.15.0-118-generic
Found initrd image: /boot/initrd.img-4.15.0-118-generic
/etc/grub.d/25_custom_proxy: 3: /etc/grub.d/bin/grubcfg_proxy: not found
tail: write error: Broken pipe
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-52-generic (--configure):
 installed linux-image-5.4.0-52-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.4.0-51-generic (5.4.0-51.56) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-51-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-51-generic
cryptsetup: WARNING: Option 'size' missing in crypttab for plain dm-crypt 
    mapping cryptswap1. Please read 
    /usr/share/doc/cryptsetup-initramfs/README.initramfs.gz and add the correct 
    'size' option to your crypttab(5).
cryptsetup: WARNING: Resume target cryptswap1 uses a key file
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Found linux image: /boot/vmlinuz-5.4.0-51-generic
Found initrd image: /boot/initrd.img-5.4.0-51-generic
Found linux image: /boot/vmlinuz-5.4.0-48-generic
Found initrd image: /boot/initrd.img-5.4.0-48-generic
Found linux image: /boot/vmlinuz-4.15.0-118-generic
Found initrd image: /boot/initrd.img-4.15.0-118-generic
/etc/grub.d/25_custom_proxy: 3: /etc/grub.d/bin/grubcfg_proxy: not found
tail: write error: Broken pipe
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.4.0-51-generic (--configure):
 installed linux-image-5.4.0-51-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.4.0-52-generic
 linux-image-5.4.0-51-generic

```

---

### Post by Impavidus on 2020-10-26
The directory /etc/grub.d/ contains files that are automatically executed when grub is updated. It contains a file named /etc/grub.d/25_custom_proxy (which doesn't exist on a stock Ubuntu system), that in turn tries to execute /etc/grub.d/bin/grubcfg_proxy, which doesn't exist.

Have you done anything to customise grub that may have put that 25_custom_proxy file there? It looks like it was put there by some tool and not properly removed before the upgrade. Can you find out to which package it belongs?```
dpkg --search /etc/grub.d/25_custom_proxy
```If it doesn't belong to any package, maybe it helps if you remove execute permission from that file. It's not present on a stock Ubuntu system, so it shouldn't be vital (but might contain stuff specific for your hardware, in particular if you bought your computer with Ubuntu preinstalled).```
sudo chmod 644 /etc/grub.d/25_custom_proxy
# Can be undone with
sudo chmod 755 /etc/grub.d/25_custom_proxy
```

---

### Post by AndrewMcNZ on 2020-10-28
Thank you for the reply which has been very helpful. I have now solved the problem and removed the remainder of the old kernel, [FONT=Courier New]linux-image-4.15.0-117-generic[/FONT].

Your comment about customising grub made me look at the repositories listed in Synaptic. I see that, in Other Software, there is a disabled repository for [FONT=Courier New]grub-customizer[/FONT]. The repository was disabled for a previous upgrade. I had obviously installed grub-customizer in the past, but I cannot recall when or why.

When I ran the command,
```
dpkg --search /etc/grub.d/25_custom_proxy
```
I did not find anything:
[FONT=Courier New]**dpkg-query**: no path found matching pattern /etc/grub.d/25_custom_proxy[/FONT]

Then I removed the execution permission for [FONT=Courier New]25_custom_proxy[/FONT] using your suggested command.
```
sudo chmod 644 /etc/grub.d/25_custom_proxy
```

I then ran
```
sudo apt autoremove

```

which ran without errors! :-)

I have since successfully added and removed several packages using Synaptic and all is working as it should.
Thank you very much for your help. It was exactly what I needed.

Cheers
Andrew Mc

---

### Post by Impavidus on 2020-10-29
So grub-customizer wasn't properly removed. That isn't the first time grub-customizer breaks grub.

If everything works fine, you can completely remove /etc/grub.d/25_custom_proxy:```
sudo rm /etc/grub.d/25_custom_proxy
```The command in my previous post only made it non-executable.

---

### Post by AndrewMcNZ on 2020-10-30
Thanks for the advice. I removed the /etc/grub.d/25_custom_proxy file and all is good. :-)

Cheers, Andrew Mc

---

