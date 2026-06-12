---
title: "Ubuntu 16.04 KickStart Automatically Answering Questions"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by radic2 on 2016-05-03
All,

Thanks in advance for your help. Trying to migrate a working kickstart from 14.04 to 16.04, but there appears to be new dialogs that need to be answered, but not documented (from what I can find).

1. "The following Linux Kernel Modules were detected as matching your hardware....." - I need to automatically press "Continue" via the kickstart/preseed.
2. "IEEE 802.1Q Virtual LANs (VLAns) are a way of partitioning a physical network.....is this system connected to a VLAN trunk port?" -  I need to automatically select "No"
3. "Auto-configure networking?" - I need to automatically select "Yes"
4. "Waiting time (in seconds) for link detection:" - Automatically select "Continue"

Here is what previously worked on 14.04 and no long works properly on 16.04.

```
installurl --url http://archive.ubuntu.com/ubuntu/
network --device 00:25:90:d4:e1:ea --onboot yes --bootproto static --ip 1.1.1.2 --netmask 255.255.255.248 --gateway 1.1.1.1 --nameserver 8.8.8.8 --hostname Test
lang en_US.UTF-8
keyboard us
rootpw Test123
firewall --disabled
authconfig --enableshadow --enablemd5
selinux --disabled
timezone --utc America/New_York
reboot
preseed passwd/make-user boolean false
preseed partman-lvm/confirm_nooverwrite boolean true
preseed partman-lvm/device_remove_lvm boolean true
preseed partman/confirm_write_new_label boolean true
preseed partman/confirm boolean true
preseed partman/confirm_nooverwrite boolean true
bootloader --location=mbr --driveorder=sda
clearpart --all --initLabel
part /boot --fstype ext4 --size=512
part swap --recommended
part / --fstype ext4 --size=1 --grow
%packages
@ubuntu-server
openssh-server
vim
wget
%pre
echo "Pre-installation script"
%post
echo "Post-installation script"
```

---

### Post by swajime on 2016-05-09
I've got the same question.  How to automate the response to "is this system connected to a VLAN trunk port?".  Except I'm trying to use preseed.cfg instead of kickstart.cfg.

Thanks for any help,


John

---

### Post by swajime on 2016-05-10
nm ... i found it

d-i     netcfg/use_vlan boolean false

---

### Post by radic2 on 2016-06-13
> **swajime said:**
> nm ... i found it

d-i     netcfg/use_vlan boolean false

John, can you let me know how you were able to find that?

Thanks!

---

### Post by swajime on 2016-07-20
> **radic2 said:**
> John, can you let me know how you were able to find that?

Thanks!

By viewing the d-i output on console 4.  It may also be saved in the logs.

---

