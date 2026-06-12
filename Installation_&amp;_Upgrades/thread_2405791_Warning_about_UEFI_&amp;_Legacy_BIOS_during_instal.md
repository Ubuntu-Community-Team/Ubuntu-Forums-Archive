---
title: "Warning about UEFI &amp; Legacy BIOS during installation"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by hoover67 on 2018-11-11
**[SIZE=3]SOLVED (check last post) [/SIZE]**

Hi folks,



I'm trying to install Ubuntu 18.04 alongside win7 on a machine that also already has a 16.04 install. I'm planning a new installation instead of an Upgrade. 

During installation, the installer displays a warning about possibly not being able to boot legacy bios OSes because it's running in UEFI mode (the installer, that is).

How can I determine if my win7 install uses the legacy bios boot method or UEFI? 

I tried the msinfo32 method as outlined on the web, but I'm not seeing the "BIOS Mode: Legacy" line mentioned there. OTOH I'm also not seeing any references to (U)EFI in win7's diskmanager (I've checked all partitions), so that leaves me slightly confused.

I'd be most grateful for a reliable method to determine win7's boot / bios mode as to not lose access to it after installation (I'm still using it for a couple of games that don't run well in WINE yet or are lacking Hardware support for steering wheels and HOTASes and the like).

TIA & all the best, 

Uwe

---

### Post by TheFu on 2018-11-11
The the BIOS.

You could also use **Boot Repair** to gather the data about the system boot setup.  Just be certain not to actually try any repair, but the information gathering by the tool is still excellent.

---

### Post by hoover67 on 2018-11-11
Thank you TheFu.

I already checked the BIOS (Asus A8VP67 or similar, can't remember the exact version) and I could not find any entries relating to UEFI or legacy BIOS settings even in expert mode. 

I'll check the "boot repair" thingy, thanks. 

All the best, Uwe

---

### Post by oldfred on 2018-11-11
Also since Windows only installs to MBR(msdos) partitioned drive for BIOS boot and only to gpt partitioned drives for UEFI boot, the type of partitioning will tell you which you have. this should show partition table type.
sudo parted -l

Most Windows 7 systems originally installed by vendors were the BIOS/MBR. Only a few just before Windows 8 was released have UEFI installs as vendor was probably confirming its UEFI worked. User can install Windows in UEFI or BIOS boot mode based on how they boot install media. But Windows 7 DVD is BIOS only and has to be copied to a flash drive to move/rename a couple of files to make it UEFI. So few do that.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Many vendors have UEFI, but still call it BIOS as that is what users know.

---

### Post by Dennis N on 2018-11-11
You could examine the mounted partitions from your existing 16.04 with the terminal command **df -h**. If a partition is mounted at /boot/efi, then your 16.04 was a UEFI installation, and you should also install 18.04 as UEFI. If /boot/efi is not shown in the output, then you have a BIOS installation. (Because of the warning, I suspect the previous installs were both BIOS in your case).

Example output from my computer:
```

dmn@Sydney:~$ df -h
Filesystem                      Size  Used Avail Use% Mounted on
udev                            5.8G     0  5.8G   0% /dev
tmpfs                           1.2G  2.0M  1.2G   1% /run
/dev/mapper/os_vg-ubuntu_gnome   23G  8.1G   14G  37% /
tmpfs                           5.9G   79M  5.8G   2% /dev/shm
tmpfs                           5.0M  4.0K  5.0M   1% /run/lock
tmpfs                           5.9G     0  5.9G   0% /sys/fs/cgroup
[COLOR="#FF0000"]/dev/sdb1                        79M  6.2M   73M   8% /boot/efi[/COLOR]
/dev/sda4                       120G   68G   46G  60% /mnt/Common-Files
tmpfs                           1.2G   16K  1.2G   1% /run/user/121
tmpfs                           1.2G   60K  1.2G   1% /run/user/1000
/dev/sdc1                       7.3G  4.4G  2.6G  64% /media/dmn/MyData

```

The Red line tells me this is a UEFI install.

---

### Post by hoover67 on 2018-11-11
Thanks for your replies, guys.

As I installed win7 myself off a DVD and I don't see an efi partition on Ubuntu 16.04 (where I'm typing this right now) I guess it's safe to assume none of the installs are UEFI based.

How should I go about installing 18.04 then? I guess it's safe to assume I'll lose boot access to both partitions (16.04 and win7) if I simply go ahead and install 18.04 in UEFI mode? 

All the best, Uwe

---

### Post by oldfred on 2018-11-11
No, if you do not have an ESP - efi system partition, then it must be BIOS/MBR. 

You then cannot install Ubuntu in UEFI mode on same drive and best to not install in UEFI mode anyway.
Windows in BIOS mode has to have boot flag on pirmary NTFS partition with its boot files. 
But UEFI has to have boot flag on the ESP. 
You cannot have two boot flags on same drive, unless you want to move boot flag every time you boot other system.

And grub will only boot other systems installed in same boot mode. UEFI & BIOS are not really compatible, you can only dual boot from UEFI boot menu, but see other issues above that make it about impossible.

---

### Post by hoover67 on 2018-11-11
Thank you for your comment. 

Is there a way to boot / install 18.04 in Legacy mode, maybe using the alternate installer? As I said I couldn't find any BIOS option related to UEFI / Legacy boot mode. 

I used the standard Ubuntu image and dd'ed it straight to an USB key. 

All the best, Uwe

---

### Post by Dennis N on 2018-11-11
If a computer can boot your USB drive either way, it should give both options in the one-time boot menu. One of the entries for the USB would be prefixed by [UEFI] or differentiated in some way, the one that's not is for BIOS. The way it is booted is the way it is installed.

---

### Post by hoover67 on 2018-11-14
Hi folks,

thanks for your support, this issue can be closed. I managed to boot the stick in non-UEFI mode using the "Boot mode override" entry in my P8P67 BIOS. Mint 19 installed correctly and also picked up the win7 & LM 18 (Ubu 16.04) installations. 

All the best, Uwe

---

