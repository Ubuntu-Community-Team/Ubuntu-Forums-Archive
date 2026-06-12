---
title: "HDD to SDD on EFI - get rid of it? move boot loader?"
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by irvingdave1 on 2014-01-14
Hi,


I have a win 8 box which I installed Ubuntu on a month ago. Today, I added an SSD and attempted installed a fresh Ubuntu on this too.
It is amazingly quick!
What I have noticed though is that it is still booting from /boot/efi on the original HDD. I'd like to completely get rid of the disk (to add it in to my raid array) from a booting perspective (windows will finally be gone!) - but I'm a little scared about moving boot stuff around in the dark in case I destroy everything.
Any advice on how to move this over safely (so boot/efi is on the SDD) would be greatly appreciated.

Dave

---

### Post by oldfred on 2014-01-14
With UEFI the boot files in  the efi partition on hard drive should work if you just copy them to the efi partition on the SSD. When both drives are plugged in UEFI should then find both efi partitions and present boot options from both. May be difficult to tell apart though.

See also some of the links on two drive UEFI installs in link in my signature. Now older where users manually copied files, but Boot-Repair was updated to also work with dual drive UEFI installs.

Ubuntu on SSD needs to be a UEFI install and SSD must be gpt partitioned with efi partition near beginning of drive.

---

### Post by irvingdave1 on 2014-01-14
Thanks so much for the help! I didn't have an efi partition on the SSD - so perhaps that was the start of my troubles (I wonder whether the installer just sniffed one out from the HDD and used it automatically?).
As I haven't done anything with the new install yet, I'm going to just clear and restart with an efi partition.....

---

### Post by irvingdave1 on 2014-01-14
Things have gone badly wrong :(

I cleared the SSD and wanted to get rid of the old entry from the boot loader.
When booted in to the non SSD install, I ran efibootmgr which reported I was currently in entry 'X' (the SSD install being entry 'Y'). I deleted the entry using efibootmgr -b Y -B. The list was represented with the Y entry gone. (Its possible i guess that i actually took out the wrong entry like the idiot i am.....)

On restart, I come in to what looks like a grub shell..... I _can_ get to BIOS but cant see anything obvious I can do.....

Any ideas how I can get back in? :)

---

### Post by oldfred on 2014-01-14
If files still exist in efi partition, UEFI should readd the entry. May require another reboot to find them? 

Also Boot-Repair can reinstall grub-efi if necessary which should update UEFI NVRAM. 
Or manually add entry back in with efibootmgr.

If secure boot is on, only those systems installed with secure boot will be shown. 
Some with CSM/BIOS only show BIOS systems if that is on, other try UEFi and if not found then try BIOS bootinh mode.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I do not yet have UEFI, but install an efi partition for future use with my new drives. But I have to have the bios_grub to boot currently.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

      
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by irvingdave1 on 2014-01-14
I decided to go ahead and re-install on to the SSD and see what happened. I created an efi partition and let it do its thing. Not only am I back in, but it's using /boot/efi from the SSD too by the looks of things.
Even better, everything else seems to have repaired itself - and I have a grub entry for my non ssd install available again.
Thanks so much for your help - I would have been totally lost!

I love linux!!!!!

---

