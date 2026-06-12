---
title: "Ubuntu does not boot after Windows Update"
date: 2024-03-22
forum: Installation &amp; Upgrades
---

### Post by ichbinluka on 2024-03-22
Hello, 

after performing a Windows update in my dual boot environment ubuntu refuses to boot. I don't even get to GRUB but instead I get this error:

Reloc 0 block size 347304336 greater than reloc dirsize 4096, which is invalid
Relocation failed: Unsupported
Failed to load image: Unsupported
start_image() returned Unsupported

I also created a Boot-Info Summary using the Boot-Repair tool [https://paste.ubuntu.com/p/fDyfGwGQvd/](https://paste.ubuntu.com/p/fDyfGwGQvd/). It seems like the filesystem on sda3, which is where I have Ubuntu installed is corrupt. 

Do you have any idea if I can somehow recover the filesystem?

Thanks in advance

---

### Post by oldfred on 2024-03-22
Are you booting in UEFI boot mode?
Can you boot ubuntu entry in UEFI one time boot menu.

You have a BIOS grub boot entry in MBR which will never work.

Boot-Repair also does not do partition fixes like e2fsck, but reports this:
> Mounting failed:   mount: /mnt/BootInfo/sda3: cannot mount; probably corrupted filesystem on /dev/sda3.


You should try fsck/e2fsck on your sda3, first.
To see all the ext4 partitions
Partition must be unmounted:
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda3
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda3

For any others that see this thread, but have NVMe drive.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p3
sudo e2fsck -f -y -v /dev/nvme0n1p3

---

### Post by yancek on 2024-03-22
Boot repair shows you have Grub installed in the MBR of sda.  You have a BIOS_boot partition (sda1) because it is a GPT drive and requires that ONLY if you do a Legacy install!  sda2 is an EFI partition.  You don't need both a BIOS_boot partition and an EFI partition.  sda2 is an EFI partition with only Ubuntu EFI files while sdb2 is an EFI partition with only windows files. Which of these drives is set to first boot priority in your BIOS?  Did you do this intentionally so that your Ubuntu system is totally separate from your windows system?  Do you have your computer set to boot EFI.  Make sure Legacy boot is disabled and boot from the Ubuntu drive.    Does windows still boot from the BIOS boot option with EFI?

What is sdc?

Windows updates might change the boot order in the BIOS but should not interfere with a Linux filesystem without some user input so I don't know how your Ubuntu partition (sda3) became corrupted.  If it is, use fsck from a 'live' USB to repair.  .There are very many sites with instructions on using fsck and the various options such as the one at the link below.

   [https://phoenixnap.com/kb/fsck-command-linux](https://phoenixnap.com/kb/fsck-command-linux)

---

### Post by ichbinluka on 2024-03-26
Thank you for your help. Running sudo e2fsck -f -y -v /dev/sda3 repaired the filesystem. It seems it was only a coincidence that this happened after a windows update but it is rather linked to problems with the hardware. I'm not exactly sure why I had both a BIOS_boot and EFI partition. I tried using Boot Repair before. Maybe that screwed some things up.

However I ended up copying all the important files to another drive and reinstalling Ubuntu. 
Again, thanks for your help

---

