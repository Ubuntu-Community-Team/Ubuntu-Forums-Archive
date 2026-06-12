---
title: "Grub failed to install, 5 HDDs, 4 in GPT one not, how to install grub_bios?"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by alex226 on 2014-07-13
Hi all,

Im quite new to linux so forgive me if i dont know exactly how to format this.

Basically i have a software raid 5 from a windows install (4x2TB) disks in my NAS, i have a 5th disk 250gb which im trying to install ubuntu server on. at the moment it fails on installing grub.

Ive done some searching and come across this [http://ubuntuforums.org/showthread.php?t=1949220](http://ubuntuforums.org/showthread.php?t=1949220) and this [http://serverfault.com/questions/386041/ubuntu-server-gpt-partition-table-mdadm-grub-boot-fail](http://serverfault.com/questions/386041/ubuntu-server-gpt-partition-table-mdadm-grub-boot-fail)

and it says "i[COLOR=#000000]f BIOS you need a tiny bios_grub partition of 1MB for core.img to install to correctly. It can be anywhere on drive."
[/COLOR]
and thats what i have, but i dont know how to get this bios_grub installed through the wizard, ive hit ctrl+alt+f2 and it theres only a few commands available there, ive also looked at some threads that say boot into a live isntall and do it from there, but i searched for unbuntu server live boot and it doesnt seem to exist?

can someone help me out?
Thanks
Alex

---

### Post by oldfred on 2014-07-13
If drive is gpt, then you need to use gparted or gdisks to add the bios_grub partition. It is 1 or2 MB unformatted with the bios_grub flag is using gparted or ef02 code if using gdisk. Grub will automatically use it when installing to MBR of any gpt drive.
I think the installer automatically adds a bios_grub partition only if drive is empty and over something like 1.5TB. gpt is really only required for drives over 2TiB, but I now use it on all new drives whether BIOS or UEFI.

          I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 sudo apt-get install gdisk
sudo gdisk -l /dev/sda
GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by alex226 on 2014-07-14
how do i get ubuntu server into live mode?

just tried booting ubuntu live, it wont boot :| im going to have to format these disks again arent i? theres nothign on them at the moment, it just took 3 days to format them last time (RAID 5) :|

Thanks

---

### Post by oldfred on 2014-07-14
Server is not live mode.
You have to download a Desktop version. The Desktop version does not include the RAID drivers but you can easily add them.
Depending on type of RAID you may need dmraid for BIOS or fakeRAID or mdadm RAID if Linux raid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
sudo apt-get install dmraid
or 
sudo apt-get install mdadm

Then mount RAID volumes with your RAID commands.

---

### Post by alex226 on 2014-07-14
I went through the install again this time i erased all the radi5 partitions and recreated everything using the parttion wizard in the ubuntu install, i created a root partition with bootflag turned on in the 5th HDD (not in the array) and everything went though, grub installed etc.

however after reboot i get nothing, it doesnt boot :( so i figured raid 5 issues again, rebooted with the raid 5 unplugged, boot disk not found. what do i keep doing wrong here?

---

### Post by oldfred on 2014-07-14
Grub does not use boot flag. Windows has to have a boot flag and a few BIOS will not boot without a boot flag, so we still suggest one on a primary partition just so those BIOS do not create issues.

Post link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by alex226 on 2014-07-15
thanks, that repair worked im in! :)

ive also installed gparted partition editor and then i created a new partition out of my raid 5 array, ive now mounted it and i cant create a new folder or document in there (the option is not available) could it be becuase its sycing? if so how can i view the sync?

Thanks

---

### Post by oldfred on 2014-07-15
Is partition formatted with Linux format?
Then the issue may be ownership & permissions.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

    
If partition is mounted at /mnt/data:

 sudo chmod -R a+rwX /mnt/data 
sudo chown -R $USER:$USER /mnt/data

---

### Post by alex226 on 2014-07-16
Thanks

the chown did it now i can use it :)
Thanks again

---

