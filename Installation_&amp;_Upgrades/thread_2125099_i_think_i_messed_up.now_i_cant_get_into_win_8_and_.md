---
title: "i think i messed up.now i cant get into win 8 and no Grub menu for dual boot"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by WallyE36 on 2013-03-13
Here is my log

[http://paste.ubuntu.com/5609802/](http://paste.ubuntu.com/5609802/)

---

### Post by WallyE36 on 2013-03-13
[IMG]http://i.imgur.com/uIBRHOU.jpg[/IMG]

---

### Post by WallyE36 on 2013-03-13
ok so i wipe my drive and re-installed ubuntu, can i reinstall windows now and try to dual boot that way? or would it be better the other way around? 
all my stuff is backed up on 2 hard drive so i dont mind wiping my SSD if needed

---

### Post by WallyE36 on 2013-03-13
sooo that didnt work, so now i am back with a fresh install of win 8.... the grub menu just dont show up... and i ended up wiping the drive, what am i doing wrong?

---

### Post by nibal on 2013-03-13
> **WallyE36 said:**
> sooo that didnt work, so now i am back with a fresh install of win 8.... the grub menu just dont show up... and i ended up wiping the drive, what am i doing wrong?

Oh, man! Did you loose data?:( There are a zillion things to do to fix this problem, without formatting/installing anything!
You should boot with the Live Ubuntu CD.
Then from a terminal or console:

```

sudo mount /dev/sda7 /mnt                          // Asuming /dev/sda7 is your '/' partition.
sudo mount /dev/sda1 /mnt/boot                  // Assuming sda1 is your '/boot' partition. If you don't have a separate /boot, just ignore this step
sudo mount --bind /dev /mnt/dev                  // To get the sda* devices in your sick system
sudo mount -t proc /proc /mnt/proc              // ditto
sudo chroot /mnt                                        // Run from your sick system
sudo grub-install /dev/sda                           // Reinstall grub

```

Of course, in place of sda* substitute your own disk devices from /etc/fstab - no UUIDs please.

HTH
Nikos

---

### Post by Mark Phelps on 2013-03-13
IF this PC came with Win8 preinstalled, stop hacking around and wait until oldfred sees this and replies.  New Win8 machines use UEFI BIOS -- and that makes installation a lot harder and different than in the past.

---

### Post by nibal on 2013-03-13
> IF this PC came with Win8 preinstalled, stop hacking around and wait  until oldfred sees this and replies.  New Win8 machines use UEFI BIOS --  and that makes installation a lot harder and different than in the  past.

Well, for UEFI support you need to install special grub 2 packages. You can read about it in:

[https://wiki.archlinux.org/index.php/GRUB2#Create_and_Mount_the_UEFI_System_Partition](https://wiki.archlinux.org/index.php/GRUB2#Create_and_Mount_the_UEFI_System_Partition)

But eventually to rescue your sick system, you will need the liveCD and the procedure I described.

Nikos

---

### Post by WallyE36 on 2013-03-13
i build this system myself and i just installed win8 from a USB and i dont think is on UEFI Bios,
my issue is, now i 100% wipe my SSD and did a clean win8 install, and when i shrink my SSD to make a new free space for ubuntu, i can install in and such but when i reboot, it boot straight into win8

---

### Post by WallyE36 on 2013-03-13
> **nibal said:**
> Oh, man! Did you loose data?:( There are a zillion things to do to fix this problem, without formatting/installing anything!
You should boot with the Live Ubuntu CD.
Then from a terminal or console:

```

sudo mount /dev/sda7 /mnt                          // Asuming /dev/sda7 is your '/' partition.
sudo mount /dev/sda1 /mnt/boot                  // Assuming sda1 is your '/boot' partition. If you don't have a separate /boot, just ignore this step
sudo mount --bind /dev /mnt/dev                  // To get the sda* devices in your sick system
sudo mount -t proc /proc /mnt/proc              // ditto
sudo chroot /mnt                                        // Run from your sick system
sudo grub-install /dev/sda                           // Reinstall grub

```

Of course, in place of sda* substitute your own disk devices from /etc/fstab - no UUIDs please.

HTH
Nikos

naw i didnt lose anything, my SSD is OS only, all my data and programs is on 3 1TB drives running RAID 1 :)

---

### Post by nibal on 2013-03-13
@WallyE36:
> naw i didnt lose anything, my SSD is OS only, all my data and programs is on 3 1TB drives running RAID 1

Nice! BTW the procedure I gave you is no hack. The mounts are completely safe, since they deal with resources from a live CD, which cannot be corrupted even if you try to! Besides for such situations the --bind argument was added to mount.:P. It will allow you to play around with bootloaders with impunity. The point I wanted to get across, is that bootloaders are something outside the filesystem. They install in the MBR of the disk, and there is no good reason if they get corrupted to corrupt the fs. So you don't need to format anything if you loose your boot menu!

From your screenshot, it seems like a broken grub installation. Since you are going to reinstall Ubuntu, this should fix it.

BR,
Nikos

---

### Post by oldfred on 2013-03-13
If it is a new system, it almost for sure has UEFI. But UEFI has CSM which is the old BIOS.
       Compatibility Support Module (CSM), which emulates a BIOS mode.

Best to see what is where now, it sounds like you have installed & reinstalled several times.
Do you want UEFI boot or BIOS boot. UEFI requires gpt partitioning which is recommended for SSD, but Windows only boots from gpt drives with UEFI. 
UEFI is new and not many understand it yet, BIOS/MBR is old (very old) as it is from the first PC with some updates over time.

I do not know RAID, but if installing to a boot drive that should be just standard install. But you will need RAID driver to see the RAID, but there are many types of RAID and I do not really even know the differences.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[URL="https://help.ubuntu.com/community/UbuntuSecureRemix"]https://help.ubuntu.com/community/UbuntuSecureRemix

      [/URL]
 Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

    [URL="https://help.ubuntu.com/community/UbuntuSecureRemix"]
[/URL]

---

