---
title: "Are /home /swap /boot partitions important for ubuntu installation?"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by acerbuntu on 2012-11-23
Hi guys,

I have triple boot on my acer aspire 5755G and for some issues having with third party boot loaders I was unable to boot Ubuntu 12.04 LTS from extended partition and for this reason I have to change Ubuntu partition to primary partition.

From this as you all know that primary partitions do not allow sub partitions and I only did "/root" partiiton and installed ubuntu 12.04 Lts.

So I am curious to know what happens if I do not create home, swap, & boot partitions, are they really important.

As I will be using ubuntu for 3D design and other high end applications.

My System Specs are as follows:

Screen Size 15.6 inches
Processor Type Intel Core i5 
Processor Speed 2.5 GHz (Turbo boost upto 3.1GHz)
Memory RAM Size 8 GB
Computer Memory Type DDR3 SDRAM
Hard Drive Size 750 GB
Graphics Card DescriptionNVIDIA GeForce GT 630M
Graphics Card Ram Size 1 GB VRAM
Pioneer DVD Super Multi DL Drive
HDMI out
USB 3.0
Audio Combo Jack
Acer Crystal HD Webcam
Average Battery Life (in hours)4.5 hours

Many Thanks in Advance.

---

### Post by cwsnyder on 2012-11-23
If you are using Ubuntu as a desktop computer, not as a server, normal recommendations are to have a /, swap, and /home as the only partitions. Swap and /home can easily be in the extended partition, and even /home can be eliminated so that you only have / and swap.  The normal recommendation to have a separate /home partition, which would contain most of your data and program configuration files is for ease of updating when it is time to update your system files for a new release without requiring a full backup of your /home folder.  At least a small swap partition is recommended to keep from crashing the system if you run out of RAM space.  You can use a RAM based swap (even a file) if you have over 8 G RAM, however.

Of course if you are installing a server, /boot, /var, /, /home and swap would all be recommended.

There you have it.  / only, or /, /home, swap, it really depends on how you use your computer, and your choice.

---

### Post by acerbuntu on 2012-11-23
> **cwsnyder said:**
> If you are using Ubuntu as a desktop computer, not as a server, normal recommendations are to have a /, swap, and /home as the only partitions. Swap and /home can easily be in the extended partition, and even /home can be eliminated so that you only have / and swap.  The normal recommendation to have a separate /home partition, which would contain most of your data and program configuration files is for ease of updating when it is time to update your system files for a new release without requiring a full backup of your /home folder.  At least a small swap partition is recommended to keep from crashing the system if you run out of RAM space.  You can use a RAM based swap (even a file) if you have over 8 G RAM, however.

Of course if you are installing a server, /boot, /var, /, /home and swap would all be recommended.

There you have it.  / only, or /, /home, swap, it really depends on how you use your computer, and your choice.
Hi cwsnyder,

Thanks for your reply. I will only use Ubuntu as desktop computer. Now I remember I should try creating primary partiiton for "/" and rest of /swap and /home to extended partitions.

Any way what is this RAM based swap you metioned above? I have no idea about it,could you please explain in-detail.

Cheers.

---

### Post by oldfred on 2012-11-24
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Herman only has / (root)
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

If you have gpt partitioning you only have primary partitions. Windows will only boot with gpt partitions with UEFI. Ubuntu can use gpt whether using BIOS or UEFI.

I use 25GB / (root) including /home but have all data in other data partitions. We have seen some systems that will not boot from very large / partitions. Boot-Repair then suggests a /boot, I typically suggest smaller  / inside the first 100GB of drive.

---

### Post by YannBuntu on 2012-11-24
Hello
Root only should work. SWAP is very recommended. The rest is optional (except /boot, or ESP, or BIOS-boot in some cases). See comments above.

see also [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by RoosterHam on 2012-11-24
In my desktop situations, I try to keep the complexity of my partitions to a minimum. Since I only use Unix-like systems (ubuntu linux, other linuxes, *bsds) each OS gets a '/', some swap, and a '/home' partition.

My servers receive much more complexity.

Multibooting, to me at least, necessitates as simple an arrangement as practical.

swap seems a bit of a grey area with the amounts of ram currently available, and large file sizes often dealt with.

---

### Post by kurt18947 on 2012-11-25
I don't do much 'work', just web browsing and run of the mill office-type stuff.  I haven't created a swap partition on any machine with 2 GB. RAM for a couple years.  One machine with 512 MB. RAM?  That has a swap partition of around 700 MB.  AFAIK (I'm no expert) a swap **partition** is required if you want to suspend-to-disk/hibernate.  The system write the content of its RAM to disk then powers down.  I don't use hibernate, I just shut down.  I do use suspend where RAM is refreshed but the rest of the system is put in a very low power state.  I have in the past created a swap **file** but haven't done so the past few installs and haven't suffered as a result.  I have installed htop and occasionally run it in a terminal.  I don't recall ever seen more than 1 GB.  RAM in use.

---

### Post by Hagar Delest on 2012-11-25
Personally, I've 2 partitions for the OS (root /): when I upgrade, I install from scratch on the other partition (I don't trust the soft upgrade).
In addition, I've swap, opt (because I use the beta versions of Firefox and Thunderbird that I put here) and a dedicated partition for my documents. Note that I don't have a partition for home (it is kept in the default / tree). When you upgrade, configuration files may change and cause troubles with the new flavor. I've another partition for my profiles (AOO, FF, TB, ...) and I use symlinks in my home that point to these profiles.

---

### Post by malspa on 2012-11-25
For my multi-boot set-ups, I normally have /, swap, and /home for each distro. Separate partitions for data, etc., that I can access from each distro.

---

### Post by acerbuntu on 2012-11-29
> **YannBuntu said:**
> Hello
Root only should work. SWAP is very recommended. The rest is optional (except /boot, or ESP, or BIOS-boot in some cases). See comments above.

see also [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
> **oldfred said:**
> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Herman only has / (root)
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

If you have gpt partitioning you only have primary partitions. Windows will only boot with gpt partitions with UEFI. Ubuntu can use gpt whether using BIOS or UEFI.

I use 25GB / (root) including /home but have all data in other data partitions. We have seen some systems that will not boot from very large / partitions. Boot-Repair then suggests a /boot, I typically suggest smaller  / inside the first 100GB of drive.


Hi guys thank you very much for your valuable information. Now after referring various things finally I managed to linux by creating 3 partitions (/,/home and /Swap) on my triple boot system.
However I do have 8GB of RAM and so I only had 5GB Swap where still it is not been used at all.I think 8GB is more enough to run without swap.

Anyways if you guys still happy to help me with my other problem which i posted on desktop environments a min ago. Please feel free to do that.

Thanks again. This thread is [Solved] now.

---

