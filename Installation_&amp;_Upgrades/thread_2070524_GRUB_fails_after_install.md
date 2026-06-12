---
title: "GRUB fails after install"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by Haneef Mubarak on 2012-10-13
I have a performance EFI machine on which I attempted to clean install Precise. After that, I always get various errors. While I was on Oneiric, the system worked just fine. I have tried various solutions like BootRepair and just manually looking at the files and messing around. I always get a different error.

Thanks in advance for any help leading to a solution.

---

### Post by oldfred on 2012-10-13
Post the link to the BootInfo report. What errors are you getting?

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Haneef Mubarak on 2012-10-13
[http://paste.ubuntu.com/1277904/](http://paste.ubuntu.com/1277904/)

---

### Post by oldfred on 2012-10-13
You have a very large 6TB drive. Better to have the system or / (root) in a smaller 25 to 50GB partition and use the rest of the drive as /home, data partition(s) or leave some unallocated if not sure what you want to do with it.

You should only be booting 64bit version of Ubuntu in UEFI mode not BIOS/AHCI/Legacy or whatever your UEFI may call it. If you want bios you have also create a bios_grub partition with gpt partitioning for grub to install correctly to the MBR>=.

You have grub installed to the MBR which is for the old BIOS system. You also have some extra grub.cfg and core.img in the efi partition which should not be there. 

I would really suggest reinstalling as the quickest way to correct the issues.

One suggestion for partitioning, but it should vary depending on what you want to use all the space for. Since you have a very large drive you can be more generous on partition sizes than my normal suggestion below.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Haneef Mubarak on 2012-10-13
I prefer a single solid root partition.

Well, actually, I used to have Oneiric installed on the 6 TB HDD (actually 2 separate 3 TB HDDs in Hardware RAID 0), and it worked fine. I wanted to reformat, so I booted to a 64-bit Precise LiveCD (I set my UEFI BIOS to "UEFI: [Disc drive name]"), 

```
sudo dd if=/dev/zero of=/dev/sda
```

and waited for it to complete (around half a day...).

Then I went about the normal way of installing Precise. 

And I got GRUB errors. So I went about fixing those, then kernel errors, then GRUB errors, more GRUB errors, etc.

Anyways, my UEFI BIOS supports both UEFI booting and AHCI/BIOS/Legacy booting at the same time (where you select the bootloader or OS to boot). 

Should I turn off the ability to use AHCI?

What should I do about GRUB in the MBR? I'd like a pure UEFI boot, so I don't really care for GRUB in the MBR.

I've reinstalled over twenty times trying to fix this.

I've tried both a 1 GB and a 200 MB efi partition formatted to FAT32. Neither solved the problem.

I prefer to use a single root partition (ext4).

I use a 32 GiB swap because I hibernate often and I have 32 GiB RAM (4 sticks of 8 GiB in a Quad Channel Configuration). With 32 GiB of RAM though, I really don't think pre-formatting will make it much faster. ;)

So any ideas?

(Thanks for the quick response!)

---

### Post by oldfred on 2012-10-13
If UEFI booting having grub in the MBR does not matter as then it is not used.

This will fix your efi boot. But we have seen a lot of grub not finding all its files when installed in very large root partitions. But it may also be a UEFI or BIOS issue so you can try it and see if it works.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Haneef Mubarak on 2012-10-14
Well I did UEFI boot, but here's the latest error:

```

error: file '/boot/grub/x86_64-efi/normal.mod' not found.
grub rescue> _

```

---

### Post by oldfred on 2012-10-14
My liveCD does not have normal.mod in it either in the /boot/grub/x86_64-efi/ folder.

But my installs of 12.04 and 12.10 have normal.mod but they are BIOS based and paths are different.

Did you houseclean out your efi partition. Which tells me something got installed to the wrong partition as these files should not be in the efi partition.

    Boot files:        [COLOR=Red]/grub/grub.cfg /boot/grub/grub.cfg [/COLOR]
                       /EFI/ubuntu/grubx64.efi [COLOR=Red]/grub/core.img[/COLOR]

Only /EFI/ubuntu/grubx64.efi should be in the efi partition.

---

