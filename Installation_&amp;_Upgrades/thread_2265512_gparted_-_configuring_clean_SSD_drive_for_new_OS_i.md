---
title: "gparted - configuring clean SSD drive for new OS installation, UEFI"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by gasior.tt on 2015-02-15
Hello, 

I have just finished my first PC build. I was thinking about dual-boot ubuntu and win7, however I am not sure if I know exactly how I should partition my drives.

My motherboard supports UEFI system. So using USBLive "try ubuntu" I formatted both drives  and then setted partitioning table to GPT for each drive as it is depicted here [http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383).
And now, for ubuntu I have partioned the following:
[LIST=1]
[*]/dev/sda1 efi        20MiB
[*]/dev/sda2 ext4 /   200GiB
[*]/dev/sda3 ext4 /home 200GiB
[*]/dev/sda4 swap     20GiB
[/LIST]

I am completely lost when it comes to configuring drive for Windows7 . Someone knows how to tackle this? I have searched the web and I have no clue. 

Thank you

---

### Post by oldfred on 2015-02-16
For Ubuntu with a separate /home or data partition(s), a / (root) of 25GB would be generous. I use about 11GB of my 25GB partition.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You need to convert Windows 7 to flash drive an do a few updates to make it install in UEFI mode. Default installs seem to be BIOS otherwise. Have not done it but found many posts discussing it.
      
 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by gasior.tt on 2015-02-21
thanks for your reply.

Actually I resolved it this way: 

I followed the steps during ubuntu installation and created the following partitions on my SSD drive: 
[LIST]
[*]1st efi partition,
[*] 2nd ext4 ~100GB for ubutnu,
[*]3rd swap space(for ubuntu),
[*]**4th unallocated space ~100GB (for Windows)**
[/LIST]

After doing this I rebooted PC and inserted  Windows CD. Turned out that it's enough setup to go for Windows. So I assume  that it just needs efi partition and some unallocated space to successfully install win7.

---

### Post by ubfan1 on 2015-02-21
I hope you used more than 20MiB for the size of the EFI partition.  I usually use a generous 300MiB, for my actual dual boot use of 55MiB.

---

