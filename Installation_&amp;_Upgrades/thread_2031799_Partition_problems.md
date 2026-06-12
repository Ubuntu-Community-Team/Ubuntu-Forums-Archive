---
title: "Partition problems"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by CRD92 on 2012-07-22
Please bear with me. I am relatively new to Linux and will do my best to explain how I have gotten myself into a bit of a pickle. I thought it best to post here rather than the Absolute Beginners thread as my problem is more suited to this section.

On my laptop, I have been running a dual boot of Windows 7 (taking around 100GB of space due to needing it for music/ itunes) and Linux Mint 13 (taking the rest of the space; around 60GB). I had previously run Ubuntu 12.04 and wanted to return to it as I prefer the interface.
I run the Ubuntu 12.04 ISO and expected there to be an option to replace Linux Mint 13. However, there was no such option, so I installed Ubuntu 12.04 with the intention of deleting the Linux Mint partition later in Gparted and expanding the empty space to maximize the size of the Ubuntu partition. (I'm not sure if this was a sensible idea!)

Now, I am not sure how to delete the Linux Mint partition and would be grateful for any help. The partitions I can see are as following:

/dev/xda1 ntfs (system reserved 100mb)
/dev/sda2 ntfs 94.25gb
/dev/sda3 extended 54.7gb
/dev/sda8 ext4 26.7gb (ubuntu)
/dev/sda7 ext4 24.4gb (linux mint
/dev/sda6 linux-swap 1.74gb
unallocatedd 5mb
/dev/sda5 linux-swap 1.74gb

I am able to format the Linux Mint partition in Gparted, but I am not sure how to expand the Ubuntu partition or if there is any other way of removing Linux Mint from the computer without effecting the Windows partition. Huge thanks to anyone who helps.

---

### Post by oldfred on 2012-07-22
Welcome to the forums.

Best to post screenshot from gparted or 

sudo fdisk -lu

If you install Ubuntu last, it it the one first on grub boot menu or the one you are using to boot? 
 If not you need to update to use Ubuntu's grub to boot first.

You also have two swaps and probably only need one.

If you had used manual install or Something else, then you could have specified which partition to use as / (or the old Mint), its format, and it would find swap automatically. Then you would have reused existing partitions.

---

### Post by CRD92 on 2012-07-22
I found a way around my problem (not necessarily the easiest way, but a way). For future reference, what I did is: deleted the Linux Mint and Ubuntu Partitions using a Mint live CD with Gparted, inserted my Win 7 recovery CD, went to command prompt and typed:
bootrec.exe/fixmbr then pressed restart.
This took my into Win 7 and removed grub. I cleaned up the partitions by right clicking My Computer, manage, disk management, storage, and extended the NTFS Windows partition to the whole disk.
Now I am re-installing Ubuntu next to Windows 7.

---

### Post by darkod on 2012-07-22
It's already too late, but for future reference.
Deleting the linux partitions was OK. But you should have left the space as unallocated and simply install ubuntu. In that case it will take that unallocated space.

Expanding win7 to take the whole disk was a wrong decision. During the install of ubuntu now the installer will have to shrink it which sometimes can break windows. You already had win7 taking only the space you want it to take, why expanding it so that it gets shrinked down later?

And going back to your original intent to replace Mint with Ubuntu, you should have used the manual method (Something Else), and simply install ubuntu onto the existing Mint partition(s). No need to be scared from the manual partitioning, and that's exactly what you need to use if you want best control and to tell the ubuntu installer which partitions to use as what.

---

