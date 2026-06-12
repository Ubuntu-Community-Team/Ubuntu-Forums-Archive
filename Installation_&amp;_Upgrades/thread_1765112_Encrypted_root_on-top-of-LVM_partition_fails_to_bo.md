---
title: "Encrypted root on-top-of-LVM partition fails to boot after upgrade"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by timotheus2 on 2011-05-22
Before the release of 11.04, I was running Ubuntu (Alternative CD) 10.10 on an x86_64 CPU with an extensive list of packages installed.

All of my partitions are luks encrypted running on top of LVM2. It is not a single encrypted device with LVM2 running inside (the default setup). Why I chose this uncommon setup is beyond the point of this topic.

Some commands to explain my setup.

```
# sudo pvs
  PV         VG               Fmt  Attr PSize   PFree
  /dev/sda2  kithlish-root-vg lvm2 a-     4.65g    0 
  /dev/sda3  kithlish-sys-vg  lvm2 a-   460.73g    0 

``````
# sudo lvs
  LV   VG               Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root kithlish-root-vg -wi-ao   4.65g                                      
  home kithlish-sys-vg  -wi-ao 180.00g                                      
  opt  kithlish-sys-vg  -wi-ao  70.00g                                      
  swap kithlish-sys-vg  -wc-ao  10.00g                                      
  tc   kithlish-sys-vg  -wi-ao  80.73g                                      
  tmp  kithlish-sys-vg  -wi-ao  15.00g                                      
  usr  kithlish-sys-vg  -wi-ao  60.00g                                      
  var  kithlish-sys-vg  -wi-ao  45.00g

``````
# cat /etc/crypttab
# <target name>    <source device>        <key file>    <options>
crypt_root /dev/kithlish-root-vg/root none luks,retry=1
crypt_home /dev/kithlish-sys-vg/home /etc/cryptkey luks,retry=1
crypt_var /dev/kithlish-sys-vg/var /etc/cryptkey luks,retry=1
crypt_usr /dev/kithlish-sys-vg/usr /etc/cryptkey luks,retry=1
crypt_tmp /dev/kithlish-sys-vg/tmp /etc/cryptkey luks,retry=1
crypt_opt /dev/kithlish-sys-vg/opt /etc/cryptkey luks,retry=1
crypt_swap /dev/kithlish-sys-vg/swap /etc/cryptkey luks,retry=1

``````
# cat /etc/cryptmount
#!/bin/sh
for name in home swap opt var usr tmp; do
    /sbin/cryptsetup luksOpen --key-file /etc/cryptkey /dev/kithlish-sys-vg/${name} crypt_${name}
done

``````
# grep -C 2 cryptmount /etc/init/*
/etc/init/mountall.conf-
/etc/init/mountall.conf-script
/etc/init/mountall.conf:    /bin/sh /etc/cryptmount
/etc/init/mountall.conf-
/etc/init/mountall.conf-    . /etc/default/rcS

```As of Ubuntu 10.10, this setup was booting just fine. Upon the upgrade to 11.04, the booting completely failed. GRUB was not installed correctly and I had to boot a recovery CD and reinstall GRUB.

Currently, GRUB boots with the list of kernels. 

```
# cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=/dev/mapper/crypt_root ro quiet splash  vt.handoff=7

```The 11.04 splash is displayed in VGA and the dots indicator moves for over 5 seconds. Then the boot process dumps to a BusyBox command prompt.

The following is the workaround to continue booting:
```
cryptsetup luksOpen /dev/mapper/kithlish--root--vg-root crypt_root
exit

```Despite being able to boot, I would very much like to be able to have the Ubuntu splash prompt for a cryptroot password like it used to. I notice that 'update-grub' does not place the 'cryptroot' parameter in /boot/grub/grub.cfg, and I assume that is the issue.

I examined the initramfs to read the boot scripts. I tried modifying /etc/default/grub with the following and running 'update-grub'. The parameters were added to the boot sequence, but no behavior changed.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cryptroot=source=/dev/mapper/kithlish--root--vg-root,target=crypt_root"

```

---

