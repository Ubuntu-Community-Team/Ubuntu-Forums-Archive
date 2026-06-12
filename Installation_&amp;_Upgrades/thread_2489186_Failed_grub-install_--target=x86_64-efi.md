---
title: "Failed: grub-install --target=x86_64-efi"
date: 2023-07-21
forum: Installation &amp; Upgrades
---

### Post by julian-g71 on 2023-07-21
Hi - I wonder if anyone would be able to help me out with quite a specific problem please. I have several hundred Ubuntu 20.04 LTS servers that I need to O/S patch but when I tested this out on a handful of them using the unattended-upgrades.service I could see in the unattended-upgrades-dpkg.log that this failed because of:

```
Failed: grub-install --target=x86_64-efi
WARNING: Bootloader is not properly installed, system may not be bootable
```

The servers do in fact still boot and work perfectly fine, but it looks like the update / upgrade process only half-completed.

A little background ... the servers themselves are all installed from a single golden image that was created using Hashicorp Packer & Oracle Virtualbox to create an image that is then converted to a raw image file and written to the servers physical disk. This process has been used for months and works perfectly fine.

I've patched the live servers previously without issue, this was last done December 2022. But when I patched a handful of servers the other day the issue above came about and I can see that this is actually something to do with Oracle Virtualbox.

The full logs from unattended-upgrades-dpkg.log is:

```
Log started: 2023-07-20  00:08:26
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 142352 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64_2.06-2ubuntu14.1_amd64.deb ...
Unpacking grub-efi-amd64 (2.06-2ubuntu14.1) over (2.04-1ubuntu47.4) ...
Preparing to unpack .../grub-efi-amd64-signed_1.187.3~20.04.1+2.06-2ubuntu14.1_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.187.3~20.04.1+2.06-2ubuntu14.1) over (1.173.2~20.04.1+2.04-1ubuntu47.4) ...
Preparing to unpack .../grub-efi-amd64-bin_2.06-2ubuntu14.1_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.06-2ubuntu14.1) over (2.04-1ubuntu47.4) ...
Setting up grub-efi-amd64-bin (2.06-2ubuntu14.1) ...
Setting up grub-efi-amd64 (2.06-2ubuntu14.1) ...
mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-SATA_VBOX_HARDDISK_VBdc3cd684-4bde77b9-part1 does not exist.
Failed: grub-install --target=x86_64-efi
WARNING: Bootloader is not properly installed, system may not be bootable
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.10.5-2006-amd+
Found initrd image: /boot/initrd.img-5.10.5-2006-amd+
Found linux image: /boot/vmlinuz-5.4.0-131-generic
Found initrd image: /boot/initrd.img-5.4.0-131-generic
Adding boot menu entry for UEFI Firmware Settings
done
Setting up grub-efi-amd64-signed (1.187.3~20.04.1+2.06-2ubuntu14.1) ...
mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-SATA_VBOX_HARDDISK_VBdc3cd684-4bde77b9-part1 does not exist.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 32
Errors were encountered while processing:
 grub-efi-amd64-signed
Log ended: 2023-07-20  00:08:31
```

And specifically this:- mount: /var/lib/grub/esp: special device /dev/disk/by-id/scsi-SATA_VBOX_HARDDISK_VBdc3cd684-4bde77b9-part1 does not exist.

Which doesn't exist and I'm guessing is some sort of a leftover from when it was originally built using Oracle Virtualbox.

So when I then tried to manually run apt update / apt upgrade I got this popup box. Note running dpkg --configure -a also gave the same popup box.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292501&stc=1[/IMG]

I simply pressed OK as that seems correct and then I was able to fully patch the server, ie. the apt update / upgrade now works. The server boots fine and no more popups about the GRUB boot loader.

So my question is does anyone know how I can resolve this issue BEFORE I come to patch any more servers? I simply cannot manually login to several hundred machines just so that I can hit Enter to confirm the above in the popup box.

Any help or advice would be greatly appreciated.

---

### Post by julian-g71 on 2023-07-21
I should just confirm that these machines are all physical machines, they are not VM's and nothing to do with Virtualbox. Oracle Virtualbox was simply the means to create a golden image.

---

### Post by julian-g71 on 2023-07-24
[SIZE=3][FONT=arial]So after a weekend off I've come back to this and pretty much sorted it, well the sequence of events and commands to fix it manually BUT there is still an issue. So basically I need to get rid of this rogue SATA VBOX HARDDISK entry but it's proving more difficult than I expected. I can run these commands manually.

apt install debconf-utils
[COLOR=#172B4D]dpkg-reconfigure shim-signed[/COLOR]
[COLOR=#172B4D]dpkg-reconfigure --frontend=noninteractive grub-efi-amd64

And fix it, BUT I cannot run the [/COLOR]dpkg-reconfigure shim-signed command in noninteractive mode, if I do it still shows a popup box asking me to confirm the efi boot device.

For the dpkg-reconfigure of grub-efi-amd64 with the noninteractive switch its fine and just silently runs the command.

Does anyone know how to run dpkg-reconfigure shim-signed without any prompts? I just want it to accept the default.[/FONT][/SIZE]

---

### Post by julian-g71 on 2023-07-24
[SIZE=3][FONT=arial]I think I have a fix for this, tested the following on a test server and it works. Yet to test on a production server, so if you have a rogue boot entry you can use a few tools / commands to fix it without any interaction.

apt update
apt install debconf-utils expect

create this expect script.
[/FONT][/SIZE]
```
#!/usr/bin/expect -f
spawn dpkg-reconfigure shim-signed
expect "The GRUB boot loader was previously installed to a disk that is no longer present*"
send "\r"

expect eof
```

[SIZE=3][FONT=arial]chmod+x the script and run it.

[COLOR=#172B4D]dpkg-reconfigure --frontend=noninteractive grub-efi-amd64

And then check that my rogue entry has gone.

[/COLOR][COLOR=#172B4D]debconf-show grub-pc[/COLOR]
[COLOR=#172B4D]debconf-show grub-efi-amd64

And finally reboot.

An alternative was to simply mark the grub-efi-amd64 package by way of apt-mark hold grub-efi-amd64 ... but that's not really a fix.[/COLOR][/FONT][/SIZE]

---

