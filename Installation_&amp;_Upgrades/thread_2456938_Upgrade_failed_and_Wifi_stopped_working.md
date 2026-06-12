---
title: "Upgrade failed and Wifi stopped working"
date: 2021-01-22
forum: Installation &amp; Upgrades
---

### Post by jed63 on 2021-01-22
Recent upgrades (the last two) have both failed on my Acer Aspire One netbook and the Wifi is not working nor is it shown as an option in the Network Settings. Wired connection still works and all software I usually use (Thunderbird, Firefox and Libre Office) seem to be Ok.  Any ideas how I might get Wifi running again?   Following a recent post about problems with IPV6 I have run some sudo command lines which claimed to have disabled IPV6 but no luck re Wifi.  NB I am a novice Ubuntu user.

---

### Post by ActionParsnip on 2021-01-22
What is the output of:
```

sudo apt-get -f install

```

---

### Post by jed63 on 2021-01-22
sudo apt-get -f install
[sudo] password for john: 
Sorry, try again.
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfprint-2-tod1 libllvm10 libllvm9 linux-image-5.4.0-58-generic
  linux-modules-5.4.0-58-generic linux-modules-extra-5.4.0-58-generic
  python3-click python3-colorama
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 11 not to upgrade.
john@john-AO725:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libfprint-2-tod1 libllvm10 libllvm9 linux-image-5.4.0-58-generic
  linux-modules-5.4.0-58-generic linux-modules-extra-5.4.0-58-generic
  python3-click python3-colorama
0 to upgrade, 0 to newly install, 8 to remove and 11 not to upgrade.
After this operation, 419 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 229252 files and directories currently installed.)
Removing libfprint-2-tod1:amd64 (1:1.90.2+tod1-0ubuntu1~20.04.2) ...
Removing libllvm10:amd64 (1:10.0.0-4ubuntu1) ...
Removing libllvm9:amd64 (1:9.0.1-12) ...
Removing linux-modules-extra-5.4.0-58-generic (5.4.0-58.64) ...
Removing linux-image-5.4.0-58-generic (5.4.0-58.64) ...
/etc/kernel/prerm.d/dkms:
dkms: removing: bcmwl 6.30.223.271+bdcom (5.4.0-58-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.271+bdcom
Kernel:  5.4.0-58-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.4.0-58-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.271+bdcom
completely from the DKMS tree.
------------------------------
Done.
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-58-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-40-generic
Found initrd image: /boot/initrd.img-5.8.0-40-generic
Found linux image: /boot/vmlinuz-5.8.0-36-generic
Found initrd image: /boot/initrd.img-5.8.0-36-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
done
Removing linux-modules-5.4.0-58-generic (5.4.0-58.64) ...
Removing python3-click (7.0-3) ...
Removing python3-colorama (0.4.3-1build1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...

---

