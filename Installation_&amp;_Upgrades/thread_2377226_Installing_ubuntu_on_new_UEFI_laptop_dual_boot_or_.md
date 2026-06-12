---
title: "Installing ubuntu on new UEFI laptop: dual boot or VM"
date: 2017-11-10
forum: Installation &amp; Upgrades
---

### Post by tony-gould on 2017-11-10
I know this must be v frequently asked, but I had such a nightmare the last time I installed ubuntu dual boot (5 years ago), that I wanted to check. With 10 minutes searching, best article I found is [here]("https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi"), , which says

"[COLOR=#111111][FONT=Ubuntu]Of 12 Laptops ( 4 Toshibas, 3 HP & 5 Lenovo) where Windows 8.1 was pre-installed, on all cases, Ubuntu detected the Windows Boot Manager correctly, gave the option to install alongside Windows 8.1 (It actually said Install alongside Windows Boot Manager) and solved any issues that appeared on previous Ubuntu versions. I basically did not have to do anything else on this cases. This was with Secure Boot on and on an EFI enabled boot system. I also. Tested 4 Windows 10 PCs and it worked perfectly with 15.10 & 16.04."[/FONT][/COLOR]

I like the dual boot setup I have now, and v rarely go into Windows, but it took me several days, after first of all bricking my new laptop, to get it going -- and I was only able to get it going because I'm a developer and had access to Windows 7 boot disks to repair the installation. It was such a nightmare I'm now thinking a VM might be the best solution. But I'd like to develop directly on linux using CUDA directly, etc. I do want to retain the option of going into Windows, however.

The one I'm thinking of is: [[h=2]HP Pavilion 17-ab200na 17.3-inch FHD Laptop (Natural Silver) - (Intel Core i7-7700HQ, 16GB RAM, 128GB SSD, 1TB HDD, NVIDIA GeForce GTX 1050 Graphics 4GB Dedicated, Windows 10 Home)[/h]]("https://www.amazon.co.uk/HP-Pavilion-17-ab200na-17-3-inch-Natural/dp/B01NCNYOEL/ref=sr_1_3?s=computers&ie=UTF8&qid=1510336036&sr=1-3&refinements=p_n_style_browse-bin%3A182753031%7C182754031%2Cp_n_feature_three_browse-bin%3A213559031%2Cp_n_feature_fifteen_browse-bin%3A8322531031%2Cp_n_feature_browse-bin%3A1481782031%7C1481783031%2Cp_36%3A50000-150000&dpID=41wSbM7kQEL&preST=_SX300_QL70_&dpSrc=srch").

Is there anything I should be wary of or should do to cover my back? I guess, go into Windows and create the repair discs before doing anything else?

Thanks for any comments. Maybe it's all v v easy now...

---

### Post by ubfan1 on 2017-11-10
Some reading if your previous machine was not UEFI:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

HP does have some quirks, like limiting the name of the bootloaders it will boot.  You might have to change "ubuntu" to "Windows Boot Manager" or whatever Windows uses to make the nvram selection work.  Another way around this is to set up on the EFI partition /EFI/Boot/bootx64.efi as a copy of shimx64.efi and copy grubx64.efi to that directory too.  This might work as a fallback if the "ubuntu" entry has a problem.  Some machines still have a problem booting Windows from grub when secure boot is enabled -- the EFI menu (some function key at power-on allows selection of device/os to boot) should bypass grub and go directly to Windows.

Do set up the Ubuntu supplied Nvidia drivers before trying CUDA installation.

---

### Post by coldraven on 2017-11-11
On this Lenovo B590 I managed to create my first dual boot with EFI involved. (Win 8.1) I did make one error, I had wanted a separate root and home but got everything in the smaller of the partitions leaving the big one empty. My only advice is to proceed slowly and backtrack if confused before making changes.

---

### Post by tony-gould on 2017-11-11
Thanks both. It sounds like it's possible, and probably less dangerous than it was 5 years ago. I'm not sure ubfan1 what you meant by "[COLOR=#000000]You might have to change "ubuntu" to "Windows Boot Manager" or whatever Windows uses to make the nvram selection work[/COLOR]" but perhaps I will find out! :)

---

### Post by efflandt on 2017-11-11
I have certain trust issues with any added OS messing with partitions automatically. I have an HP PC with early Athlon64 3200+ (2 GHz) purchased in 2004 that came with some WinXP Home version. HP had its 200 GB drive LBA configured with an unusual 240 heads. Not knowing that I should have disabled virtual memory in WinXP before attempting to resize its partition with ntfsresize (on a Knoppix CD I think), I could only free up about 24-25 GB, so I created (2) partitions about 12 GB each. When I installed 64-bit WinXP Pro beta on one of those 12 GB partitions, it changed LBA of my drive from its unusual 240 heads to 255 heads and neither WinXP Home or 64-bit WinXP could boot. I spent significant time doing the math and trial and error testing reconfiguring the partition table with fdisk using the Knoppix CD for cylinders, heads, and partition start and end points before I was able to get everything to boot properly, without having an fdisk snapshot of what everything was before 64-bit WinXP Pro messed it up. Then when I went to install SuSE (8.0 or 8.2?) and when it was going to reformat the partition that I set aside for that, it listed geometry that just did not look right. It was going to do the very same thing that 64-bit WinXP beta diid, change heads to 255. So I just said NO, went back and told it to use partitions as is, and everything worked fine.

Since then I discovered Ubuntu, 64-bit WinXP beta expired, and I discovered how to shrink WinXP Home more by temporarily disabling its virtual memory on disk. So that old PC currently has obsolete Ubuntu 10.04 32-bit on its 3rd partition and 64-bit on its 4th partition. Believe it or not WinXP still works without ever having to reinstall it. And that old computer with early (the first?) Athlon64 can boot 64-bit 16.04 live/install system even though it is missing some newer 64-bit instructions.

More recently, the only computer I have with UEFI is a low end Win10 HP laptop. I used Windows own Disk Management to shrink its Win10 partition to make room for Linux, rebooted to make sure that all was well, then installed 64-bit Ubuntu 16.04 using "something else" when it got to the partitioning phase to create/format a partition for "/" with no swap. It has 8 GB RAM and I do not intend to suspend or hibernate, simply shut down automatically if battery runs down, since I only run it for non-essential tasks. It tends to boot right into Win10, I have to tap Esc and then F9 to bring up UEFI menu to boot grub into Ubuntu, which could be changed. But by leaving everything like it is, Win10 can reboot itself without interference when doing updates and I have had no problems with Ubuntu disappearing.

So the best advice is to first create whatever Windows repair/recovery/utility/driver disks. Do all Windows updates. Disable "fast boot" (a form of hibernation which marks Windows partition as dirty, so nothing else mounts it) and disable hibernate in Windows. Use Window's own Disk Management to shrink its partition to make unallocated space, then install Linux to the unallocated space. It is up to you if you want to have Ubuntu create the partition(s) in the unallocated space or do it yourself, and whether to try to rearrange UEFI to boot grub first (which Windows may eventually interfere with) or press a few keys (Esc, F9, down cursor) to boot Ubuntu with no interference to Windows update rebooting.

Trying to access hardware directly from a virtual machine gets more involved and judging from my slow laptop, cpu time and disk access from Win10 doing all of its antivirus and malicious software scanning and updates, including hogging your Internet and often 100% disk access might slow you down.

---

### Post by tony-gould on 2017-11-11
> **efflandt said:**
> 
More recently, the only computer I have with UEFI is a low end Win10 HP laptop. I used Windows own Disk Management to shrink its Win10 partition to make room for Linux, rebooted to make sure that all was well, then installed 64-bit Ubuntu 16.04 using "something else" when it got to the partitioning phase to create/format a partition for "/" with no swap. It has 8 GB RAM and I do not intend to suspend or hibernate, simply shut down automatically if battery runs down, since I only run it for non-essential tasks. It tends to boot right into Win10, I have to tap Esc and then F9 to bring up UEFI menu to boot grub into Ubuntu, which could be changed. But by leaving everything like it is, Win10 can reboot itself without interference when doing updates and I have had no problems with Ubuntu disappearing.

So the best advice is to first create whatever Windows repair/recovery/utility/driver disks. Do all Windows updates. Disable "fast boot" (a form of hibernation which marks Windows partition as dirty, so nothing else mounts it) and disable hibernate in Windows. Use Window's own Disk Management to shrink its partition to make unallocated space, then install Linux to the unallocated space. It is up to you if you want to have Ubuntu create the partition(s) in the unallocated space or do it yourself, and whether to try to rearrange UEFI to boot grub first (which Windows may eventually interfere with) or press a few keys (Esc, F9, down cursor) to boot Ubuntu with no interference to Windows update rebooting.

Trying to access hardware directly from a virtual machine gets more involved and judging from my slow laptop, cpu time and disk access from Win10 doing all of its antivirus and malicious software scanning and updates, including hogging your Internet and often 100% disk access might slow you down.

Thanks a lot. That's exactly the kind of detail that could help me out. If I buy the HP laptop, it will have an SSD and HDD, and I will want to allocate some space for linux on each drive, so, e.g., knowing to use Windows own Disk Management is good. At the moment, with my setup on my UEFI Asus laptop that I eventually got going, everything goes through grub, and I have grub setup so that it always boots the most recently used operating system by default. But your tip of letting Windows have its own way is attractive, particularly as most of the time I let the laptop sleep rather than turn it off. I just don't want to get burnt like I did before. V v bad memories.

---

### Post by tony-gould on 2017-11-12
Incidentally, I just looked at a review of ubuntu 17, [COLOR=#006621][FONT=arial]www.zdnet.com/article/ubuntu-17-04-the-bittersweet-linux-release[/FONT][/COLOR], and it seems it does away with the swap partition, which should make things a little easier. Might use that rather than 16 LTS.

---

### Post by kurt18947 on 2017-11-12
> **tony-gould said:**
> Incidentally, I just looked at a review of ubuntu 17, [COLOR=#006621][FONT=arial]www.zdnet.com/article/ubuntu-17-04-the-bittersweet-linux-release[/FONT][/COLOR], and it seems it does away with the swap partition, which should make things a little easier. Might use that rather than 16 LTS.

Just remember that 17.xx has a 9 month lifespan. I haven't installed a swap partition for years. I usually use the "something else" option when installing and do not specify a swap partition. I am asked "are you sure?" and answer in the affirmative. All my machines - all pre-Secure Boot/UEFI - have 4 GB or more RAM and I can create a swap **file** if I feel the need. The only circumstance I've come close to running out of RAM is with a VM running Windows 10 as a guest. I've had no issues with multi-boot.

---

### Post by tony-gould on 2017-11-13
> **kurt18947 said:**
> Just remember that 17.xx has a 9 month lifespan. I haven't installed a swap partition for years. I usually use the "something else" option when installing and do not specify a swap partition. I am asked "are you sure?" and answer in the affirmative. All my machines - all pre-Secure Boot/UEFI - have 4 GB or more RAM and I can create a swap **file** if I feel the need. The only circumstance I've come close to running out of RAM is with a VM running Windows 10 as a guest. I've had no issues with multi-boot.

Will do thanks. I thought I'd install 17 and then upgrade to 18LTS immediately afterwards and stick with that for some years.

---

