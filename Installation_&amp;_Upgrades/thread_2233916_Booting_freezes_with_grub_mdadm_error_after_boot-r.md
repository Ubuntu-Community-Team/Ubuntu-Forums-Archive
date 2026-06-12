---
title: "Booting freezes with grub mdadm error after boot-repair with dualboot on raid 0 ssd"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by excetara2 on 2014-07-11
I installed ubuntu alongside Windows 8.1 Pro in a raid 0 ssd drive. I had this configuration working once no problems and I could boot into Ubuntu just fine. I had to reinstall now and it broke everything. I can still boot into windows just fine but not from Grub. When I try to boot into ubuntu from Grub I get:

mdadm: no group found

or the error is similar to that.

I first ran boot-repair and got this output (installed mdadm before running boot-repair):

[http://paste.ubuntu.com/7780526/](http://paste.ubuntu.com/7780526/)

Then I tried without mdadm and got this output:

[http://paste.ubuntu.com/7780582/](http://paste.ubuntu.com/7780582/)

I really just want to dualboot the two systems again. Let me know if anymore information is needed.

---

### Post by oldfred on 2014-07-11
I do not know RAID and do not suggest RAID 0 unless you have really good backups automatically running all the time or do not care about loss of data.

It does say it installed grub without error, Boot-Repair is reporting some error but lately it has done that even with systems that are fixed?

You show Ubuntu as UEFI boot entry. Windows does like to keep making itself default especially 8.1.
       BootOrder: 0001,0000,0004,0006
Boot0000* Windows Boot Manager
Boot0004* UEFI: General
Boot0006* Hard Drive
Boot0001* ubuntu.

I do not know if you use dmraid or mdadmraid with this type configuration?


Script is not showing grub.cfg?
You should have two grub.cfg. One in efi partition /EFI/BOOT/grub/grub.cfg

 that is just a configfile entry to the main install. 
And in main install you should have /boot/grub/grub.cfg as main boot?

Do both grub.cfg files exist?

---

### Post by excetara2 on 2014-07-11
Both grub.cfg files did not exist actually but I ran boot-repair again. Then it showed up but still it tried booting and got an mdadm error.

I don't use mdadm because the raid array is a fakeraid so done by the motherboard I assuming. Linux recognizes it as one drive.

Should I try reinstalling linux? Will that help at all?

I can try to reinstall both and use mbr instead of gpt partitioning because I don't think I really need gpt partitioning.

---

### Post by oldfred on 2014-07-11
There are too many versions of RAID, and I do not fully understand differences. But fakeRAID may need dmraid not mdadm?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Ubuntu will boot in either UEFI or BIOS boot mode from gpt partitioned drives. But Windows is only UEFI from gpt and only BIOS from MBR.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

In Boot-Repair make sure dmraid is installed and maybe uninstall mdadm driver.

Boot-Repair has a full install and reinstall of grub that should recreate the entire grub.cfg. You can manually create grub.cfgs if you want to try that.

      
 In efi partition's folder /EFI/ubuntu add another grub config to tell UEFI where to find grub.cfg with just this one line, change gpt7 to your partition with /boot/grub folder.
configfile (hd0,gpt7)/boot/grub/grub.cfg

It looks like Boot-Repair sees this, but is that mdadm?

/dev/md126p5

Generally fakeraid is more like this:
/dev/isw_djifjjhhid_ASUS_OS
or 
/dev/isw_djifjjhhid_ASUS_OSp5 for partition number 5

This may boot Ubuntu, but better to use UUID for raid partition. 

 menuentry "Daily on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/isw_djifjjhhid_ASUS_OSp5 ro quiet splash
        initrd /initrd.img
}

Or manual install:

 if RAID
For RAID reinstall from live-CD/DVD/USB
sudo apt-get install dmraid
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia, note p5 is partition, without p5 is root of RAID volume
sudo mount /dev/mapper/isw_djifjjhhid_ASUS_OSp5 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_djifjjhhid_ASUS_OS

Aother slightly different RAID:

 [SOLVED] GRUB on RAID1 Ubuntu - Windows7 on seperate disk, no boot after update

[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)

---

