---
title: "iSCSI Boot from SAN on 20.04"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by oldguardmd on 2020-04-29
**Expected Outcome:**
Would like to boot from SAN with a Cisco UCS B200 M4 server. 

**What I actually get:**
No support for iSCSI boot appears to be built into the product, and we are trying a number of hacks to get to a working solution. If we see the disk, the network and the user account don't work, otherwise we end up at the initramfs prompt unable to see the partition.

**My Ask:**
What is the proper way to configure ISCSI boot on 20.04.

Architecture:
Three B200 M4s
[LIST]
[*]1 Management Interface (configured through the installer)
[*]1 data interface intended for K8S after install
[*]2 ISCSI interfaces (Same VLAN - Native VLAN)
[*]PureStorage - On the same subnet
[/LIST]


[B]What we have tried:
[/B]
***Attempt 1:***
[LIST]
[*]Boot from ISO and add [COLOR=#000000][FONT=&amp]**disk-detect/ibft/enable=true partman-iscsi/iscsi_auto=true** for the boot options[/FONT][/COLOR]
[*]Enter language and keyboard options
[*]Enter a management IP address and then go immediately to shell:
[*]Start ISCSI using the following commands (no other option is given anywhere in the install process. If you don't do this now, you see no disks):

modprobe iscsi_ibft
iscsistart -N
iscsistart -b

Note: At this point ISCSI is operational, and we can see the boot drive and multipath information (We have two storage NICs in this configuration)
[*]Enter the proxy and accept the archive path
[*]Use the selected ISCSI volume and configure for lvm
[*]When install is complete, return to the shell before rebooting.
[*]Configure the initramfs using the following commands:

mount --bind /sys /target/sys
mount --bind /proc /target/proc
mount --bind /dev /target/dev
chroot /target

echo 'iscsi_ibft' >> /etc/initramfs-tools/modules

echo '#!/bin/bash' > /etc/initramfs-tools/scripts/local-top/iscsi
echo 'iscsistart -N' >> /etc/initramfs-tools/scripts/local-top/iscsi
echo 'sleep 10' >> /etc/initramfs-tools/scripts/local-top/iscsi
echo 'iscsistart -b' >> /etc/initramfs-tools/scripts/local-top/iscsi
echo 'exit 0' >> /etc/initramfs-tools/scripts/local-top/iscsi

update-initramfs -u
[*]Exit shell
[*]Reboot
[/LIST]

NOTE: This worked in earlier versions of Ubuntu. Now it doesn't work at all most attempts. You end up at initramfs prompt. The volume is not seen. I did get this to work one time and have it up and running, but cannot reproduce it, and don't know why.

***Attempt 2***

[LIST]
[*]Same steps as before until you get to the end of the installer, then use the shell and replace the shell commands in option 1 with these:

mount --bind /sys /target/sys
mount --bind /proc /target/proc
mount --bind /dev /target/dev
chroot /target

echo 'iscsi_ibft' >> /etc/initramfs-tools/modules

echo 'ISCSI_AUTO=true' > /etc/iscsi/iscsi.initramfs

update-initramfs -u
[*]Exit shell and reboot
[/LIST]

Notes:  At this point the system reboots and sees the storage, but you cannot logon to the server with the account that was supposed to be created by the installer, and there is no IP on the management interface. We can see from the cloud-init-output.log that the script is failing because I also make a user account from the shell while I am fixing iSCSI boot, and that account works.

---

### Post by oldguardmd on 2020-04-29
Review of the cloud-init-output.log suggests that the protocol entry in the abft ( STATIC ) is not being accepted by the cloud-init script. Seems like the script is expecting none, when STATIC should also be acceptable?

---

### Post by oldguardmd on 2020-04-29
We figured this out. One my peers figure out that there are two scripts that impact iSCSI boot when using ISCSI_AUTO=true. This issue occurs because the information from the ibft shows the protocol as static, but the following scripts are looking for none or dhcp and don't expect static. 

**/usr/share/initramfs-tools/scripts/functions** line 516 should be change from none to **none|static**

     The section you are modifying is the **case $proto** in where **none** is referenced in the python case statement.

**/usr/lib/python3/dist-packages/cloudinit/net/cmdline.py**

We add an additional if statement to address the static entry coming from ibft:
126     proto = data.get('PROTO', data.get('IPV6PROTO'))
127     if not proto:
128    if data.get('filename'):
129       proto = 'dhcp'
130    else:
131       proto = 'none'
132
133     **if proto == 'static':**
134    **proto = 'none'**

Attempt 2 in my original post provides everything else you need. We made the changes in this post at the same time that we made the changes for modules and ISCSI_AUTO, but before we updated initramfs.

Have a great day.

---

