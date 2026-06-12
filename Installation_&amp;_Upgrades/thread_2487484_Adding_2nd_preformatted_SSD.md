---
title: "Adding 2nd preformatted SSD"
date: 2023-06-06
forum: Installation &amp; Upgrades
---

### Post by pr0ton1c on 2023-06-06
Hi there,
I have a running Kubuntu 22.04 system that I would like to add an SSD to. I want to use this second SSD **as a back-up drive**. 
The second drive **already has Kubuntu 22.04 installed** on it. So there would be 2 with same system installed. 
However, the additional drive has never been started. 
The question is, can I just add another SSD when it's already formatted with Kubuntu?
That is, can I turn power off, open the case, plug in the additional drive, close the case and power up, with my 
system recognizing the "new" drive without conflict?

[COLOR=#ffa500]**Current system stuff:**[/COLOR]
OS: Kubuntu 22.04.2 LTS x86_64
Host: 90BG003JUS Lenovo H50-55
Kernel: 5.19.0-43-generic
Uptime: 37 mins
Packages: 3035 (dpkg), 26 (flatpak),
Shell: bash 5.1.16
Resolution: 1920x1080
WM: Awesome
Theme: [Plasma], NsCDE [GTK2], Adwai
Icons: Blueberry [Plasma], NsCDE [GT
Terminal: xfce4-terminal
Terminal Font: Anonymous Pro 12
CPU: AMD A10-7800 Radeon R7 4C+8G (4) @ 3.500GHz [10.2°C]
GPU: NVIDIA GeForce GTX 750 Ti
Memory: 3675MiB / 15948MiB (23%)

[COLOR=#ff0000]**&#8203;Drives:**[/COLOR]
Local Storage: total: 480.08 GiB used: 140.94 GiB (29.4%)
ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB
speed: 6.0 Gb/s type: SSD serial: S3YANB0K951479K rev: 4B6Q scheme: GPT
ID-2: /dev/sdb type: USB vendor: SanDisk model: Ultra size: 14.32 GiB
type: N/A
serial: 05014c14309045ea4a08da5c39ba4138de9cdd6d84360ee62c be03b6d3ed0dd8f23700000000000000000000cd7591b4ff12 02108155810788a6a6cc
rev: 1.00 scheme: MBR
&#8203;
Is this enough info? I hope so. Thanks for any help :)

---

### Post by yancek on 2023-06-06
Do you have a full install of Kubuntu also on the 2nd drive"  Is Kubuntu on the 2nd drive an EFI install?  Is Kubuntu on the internal drive an EFI install?  If they both are, you can boot either from the BIOS firmware boot options if the drive is recognized there.  You could also attach the 2nd drive and run:  sudo update-grub from the main internal drive which should detect and enable you to boot the Kubuntu on the 2nd drive.  If you want the 2nd drive for backup, create a partition on that drive with a Linux filesystem specifically for that purpose

If this is not an EFI install but a Legacy/CSM install, you can also attache the 2nd drive and then boot the Kubuntu on the primary drive and update grub to include the Kubuntu on the 2nd drive in the Grub boot menu.

---

### Post by oldfred on 2023-06-06
As long as it is not a clone with duplicate UUIDs, you can boot with it installed.
And to easily dual boot both must be in same boot mode as yancek as posted.

---

### Post by pr0ton1c on 2023-06-08
> **yancek said:**
>  If you want the 2nd drive for backup, create a partition on that drive with a Linux file-system specifically for that purpose.

Yes. This is what I am trying to do. I re-partitioned this drive with one partition and formatted it eft4. My system sees the drive but won't let me transfer files to it.

---

### Post by oldfred on 2023-06-08
Linux partitions need mount point, ownership & permissions to make them usable. 

Lots of details:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Are you permanently mounting with fstab, recommended if internal drive?

sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown -R $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

Some fstab examples:
[https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)

---

### Post by pr0ton1c on 2023-06-09
Thank you so much for your help! It works now \\:D/

---

### Post by mIk3_08 on 2023-06-12
> **pr0ton1c said:**
> Thank you so much for your help! It works now \\:D/
If your query has been sorted then you can mark this thread as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

