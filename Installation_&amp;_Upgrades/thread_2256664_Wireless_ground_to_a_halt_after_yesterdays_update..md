---
title: "Wireless ground to a halt after yesterdays update."
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by warren3 on 2014-12-14
Hi.

I have an update yesterday which required a restart.  Since then my wireless has crapped out.  I get a signal and the first page loads up in the browser.  After that all I get is a spinning circle and pages take an age to load.

I did change my wireless PCI-E card last week from a Realtek to Intel 7260.  I didn't reinstall Ubuntu or anything I just changed the card and booted up and it was fine.  Since the update though it is not working.

Any help would be appreciated.

---

### Post by carl4926 on 2014-12-14
If you boot an earlier kernel from the grub menu. Does it work better?

---

### Post by warren3 on 2014-12-14
Hi.

I am going to try than now.

Thanks.

---

### Post by warren3 on 2014-12-14
Hi.

Yes Wifi is working fine on the old kernel.

---

### Post by carl4926 on 2014-12-14
> **warren3 said:**
> Hi.

Yes Wifi is working fine on the old kernel.
So you say you put intel in?

Let us see
```
lspci -nnk | grep -iA2 net
```
From old kernel and new

---

### Post by warren3 on 2014-12-14
Hi.

  	 	 	 	   Old kernel
 

 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
 	Subsystem: Intel Corporation Wireless-N 7260 [8086:4062]
 	Kernel driver in use: iwlwifi
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
 	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
 	Kernel driver in use: r8169
 

 New kernel
 

 02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
 	Subsystem: Intel Corporation Wireless-N 7260 [8086:4062]
 	Kernel driver in use: iwlwifi
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
 	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
 	Kernel driver in use: r8169

Just to make sure I take it the top kernel in the 'advanced options for ubuntu' is the latest kernel my system has?

Thanks.

---

### Post by carl4926 on 2014-12-14
Yes

Both have the driver loaded correctly though

---

### Post by warren3 on 2014-12-14
Hi.

It seems to be working now!  All back to normal! I don't know what happened there.  But now I have another little strange problem.  I seem to have another option in GRUB that wasn't there before.  I dual boot with Windows 7 and now I have a 2nd option for Windows 7 on sda.  It seems to have appeared after using an old kernel.  Do you know why it has just appeared?

---

### Post by carl4926 on 2014-12-14
> **warren3 said:**
> Hi.

It seems to be working now!  All back to normal! I don't know what happened there.  But now I have another little strange problem.  I seem to have another option in GRUB that wasn't there before.  I dual boot with Windows 7 and now I have a 2nd option for Windows 7 on sda.  It seems to have appeared after using an old kernel.  Do you know why it has just appeared?

Are you sure it hasn't always been there.

What are your partitions?

```
sudo parted -l
```

---

### Post by warren3 on 2014-12-16
Hi.

Here is it:

Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA Crucial_CT120M50 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  90.0GB  90.0GB  primary   ntfs            boot
 2      90.0GB  120GB   30.0GB  extended
 5      90.0GB  112GB   21.5GB  logical   ext4
 6      112GB   120GB   8504MB  logical   linux-swap(v1)


For Windows 7 I boot off sdb which still works fine.  The 500GB drive that is sda is blank and is just for data when I get around to putting all my FLAC files on there, so it is strange this has appeared.  It was definitely not there before.

---

### Post by carl4926 on 2014-12-16
If sda is just data then use gparted (you may have to install it in Ubuntu) to take the boot flag off sda1

---

### Post by carl4926 on 2014-12-16
> **carl4926 said:**
> If sda is just data then use gparted (you may have to install it in Ubuntu) to take the boot flag off sda1

Then run

```
sudo update-grub
```

---

### Post by warren3 on 2014-12-22
Thanks mate.

Internet is still bad.  Just takes ages to connect to webpages after about 5 mintutes of being fine.  Do you think I could post this into the Wireless forum or could you possibly move the thread?

Thanks.

---

### Post by carl4926 on 2014-12-23
> **warren3 said:**
> Thanks mate.

Internet is still bad.  Just takes ages to connect to webpages after about 5 mintutes of being fine.  Do you think I could post this into the Wireless forum or could you possibly move the thread?

Thanks.
If you feel you need to address it, then yes, start a new thread.
I can't move this. You need a member of staff to that

---

