---
title: "Ubuntu 22.04 not bootable after windows update (boot-repair info included)"
date: 2023-11-18
forum: Installation &amp; Upgrades
---

### Post by hlance666 on 2023-11-18
I have a machine with a dual boot setup with Ubuntu 22.04 and Windows 10. After a windows update the boot file was no longer able to be found and windows would always start up without giving me an option to choose to boot Ubuntu.

I ran boot-repair and generated the following paste: [https://paste.ubuntu.com/p/VCpVp3f7sn/](https://paste.ubuntu.com/p/VCpVp3f7sn/)

I am wondering if it is safe to proceed with the recommended repair or if there are other steps I need to take to do the repair? I am not sure if it is fine to just run the suggested repair steps and any help would be greatly appreciated.

Thanks in advance!

---

### Post by tea for one on 2023-11-18
Windows update interfered with Grub - a regular occurrence
It's a good idea to make sure Windows is not hibernating before trying the repair.
Also, you should always have personal data backups.

Then, it should be safe to try the repair.

Although, I'm a bit puzzled by this:-
Line 24 - Mounting failed:   mount: /mnt/BootInfo/nvme0n1p2: wrong fs type, bad option, bad superblock on /dev/nvme0n1p2, missing codepage or helper program, or other error.

Is this an ext4 storage partition for Ubuntu?

---

### Post by hlance666 on 2023-11-18
Thanks for the reply, I'll try the recommended repair.

>  Is this an ext4 storage partition for Ubuntu?

Unfortunately I do not know, I did see this on L127:

```

99  ============================= Drive/Partition Info =============================

    ...

121 fdisk -l (filtered): ___________________________________________________________

    ...

127 nvme0n1p2 1050624 1083391 32768 16M Microsoft reserved
```

---

### Post by hlance666 on 2023-11-18
Hmmm, looks like something went wrong with the repair in this case?

paste: [https://paste.ubuntu.com/p/8N4fdbjdmD/](https://paste.ubuntu.com/p/8N4fdbjdmD/)

Dialog window contents
> An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/8N4fdbjdmD/](https://paste.ubuntu.com/p/8N4fdbjdmD/)


In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

Locked-NVram detected.

I'll email this to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].

---

### Post by tea for one on 2023-11-18
You can try this workaround:-

Create a rEFInd Boot manager installed on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
A USB with rEFInd for emergency use may help to find and boot an OS (if Grub is damaged/not responding)

Select to boot the kernel directly (similar to below) - i.e. avoiding grub.
Boot boot\vmlinuz-6.2.0-35-generic from 30 GiB ext4 volume 

If you can boot Ubuntu, open a terminal
```
sudo grub-install /dev/nvme0n1
```
```
sudo nano /etc/default/grub
```
Add this line in blue
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR="#0000FF"]GRUB_DISABLE_OS_PROBER=false[/COLOR]
```
```
sudo update-grub

```
Power off and reboot

---

### Post by hlance666 on 2023-11-18
I am not sure what happened but my computer appears to be in a state I'm unfamiliar with. 

I tried restarting my computer after doing the boot repair but came across the following on my monitor

```

7382.739750] sd 6:0:0:0: [sda] tag#o access beyond end of device 7382.7398041 I/O error, dev sda, sector 9838308 op 0x0: (READ) flags 0x80700 phys_seg i prio class 2

7382.740440] sd 6:0:0:0: [sda] tag#0 access beyond end of device

7382.7404931 I/O error, dev sda, sector 9838308 op 0x0: (READ) flags 0x0 phys_seg 2 prio class 2

7382.740548

] Buffer I/O error on dev sde2, logical block 2464, async page read

7382.740593] Buffer I/O error on dev sda2, logical block 2465, async page read

7382.741140] sd 6:0:0:0: [sda] tag#o access beyond end of device dev sda, sector 9838528 op 0x0: (READ) flags 0x80700 phys_seg 1 prio class 2

7382.7412021 1/0 error, 7382.742433] sd 6:0:0:0: [sda] tagwo access beyond end of device

7382.742480] I/O error, dev sda, sector 9838528 op 0x0: (READ) flags 0x0 phys_seg 1 prio class 2

7382.742534] Buffer I/O error on dev sda3, logical block 1, async page read

```

---

### Post by hlance666 on 2023-11-18
I manually turned my computer on and off and I'm able to boot Ubuntu and Windows now!

 The error messages makes me think it might not be completely fixed but it looks like it succeeded.

Thanks for helping tea for one :o

---

### Post by tea for one on 2023-11-18
nvme0n1p3 is 98 % full

This is your Windows OS partition.
I would suggest that you have a close look to see if anything can be moved or removed.

---

### Post by oldfred on 2023-11-18
Your p2 is elsewhere shown as the Microsoft Reserved partition. That is required to be unformatted and should not show as ext4.
Since shown as ext4, Boot-Repair tried to mount it, but since unformatted could not. Change with gparted back to unformatted.
[https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows NTFS typically wants 30% free, if down to 10% free, system gets real slow. You just about cannot do a defrag as no working room.

---

