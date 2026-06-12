---
title: "Want to run Ubutu 14.04 from SSD Card but can't set it as boot option in UEFI"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by floyd2 on 2014-09-28
Howdy there, it's me being new again.
I've been using Ubuntu 14.04 for a few months on my desktop.  No complains, I love it 
 I have a 250 g ssd card in my computer.  I'd like to boot Ubuntu 14.04 from it because I've heard it's much faster and also if I don't, I'm not using the card, which seems like a waste.
   So I'm trying to get started and having trouble finding resources.  My initial problem is this: The SSD shows up in the 'boot override' part of the BIOS (which is Gigabyte - UEFI DualBIOS), but not under 'boot options'.  So I guess I need advice on how to make the ssd an option.
  The next thing after that would be how to manage the change.  I don't have a lot of stuff on the pc, so wacking everything onto a usb stick and starting again from the ssd would be fine.

thanks in anticipation,

Floyd

---

### Post by oldfred on 2014-09-28
Is this a new m.sata drive? Have not seen or know about them, but thought they were just another way to connect.

It may not show a bootable device since it is not yet configured. Systems normally will not show a flash drive as a boot choice unless correctly configured as bootable. Data drives or unformatted drives typically are ignored.

How large is SSD?

Do you want to install in UEFI or BIOS boot mode?

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If only installing Ubuntu, you should use gpt partitioning as it can boot from a gpt drive with either UEFI or BIOS if you have correct partitions. Windows only boots from a gpt drive with UEFI.

If installing in UEFI mode many useful links in the link in my signature.

---

### Post by floyd2 on 2014-09-29
Hi, thanks for the reply.  The ssd is 250g.
  As for installing in UEFI or BIOS mode, I don't know.  The one which is better, I guess.  I only want to run Ubuntu off it, so I will check your llinks and give gpt partitioning a whirl.

cheers, Floyd

---

### Post by oldfred on 2014-09-29
How you partition is very personal depending on how you plan to use system. My 64GB SSD has two Ubuntu 12.04 & 14.04 using half each and all data in a rotating hard drive.
Newer SSD have lives similar to hard drives, and if you have a fair amount of RAM, you may never use swap. So all the issues on whether swap is on SSD are moot.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

