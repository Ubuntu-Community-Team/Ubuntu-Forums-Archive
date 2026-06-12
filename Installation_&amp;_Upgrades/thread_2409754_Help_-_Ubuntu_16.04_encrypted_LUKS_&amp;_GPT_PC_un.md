---
title: "Help - Ubuntu 16.04 encrypted LUKS &amp; GPT PC unbootable (partitions are intact)"
date: 2019-01-06
forum: Installation &amp; Upgrades
---

### Post by fr33z0n3r on 2019-01-06
I was trying to work on a new 2nd SDD for a new install of Ubuntu,  but somehow my existing install is not unbootable (bootable device not found).  I was doing this work while in my 16.04 install.  This may have been a bad idea :)

Fortunately, I can still get into the encrypted LVM/LUKS partition (via 18.04 live USB) where all of the data is,  but I cannot get it to boot.

Its a UEFI based PC with GPT partitioning on the SSD.

Partition 1 - EFI
Partition 2 - ext2 (linux /boot)
Partition 3 - LVM2 (encrypted LUKS)

I do not have Secure Boot enabled, and I have tried to enable Legacy Boot in addition to UEFI boot without any success.

Of note, I was making partition changes with gparted for the 2nd SSD, and am confident that I never accidentally intentionally made a change to the 1st SSD.  That said, perhaps a change there required a change affecting SSD #1 partitions?

I have no idea if systemd affects using grub or not.  I thought I made some switch/upgrade (in Ubuntu 16.04) to use systemd previously.  No clue if that could impact this.

I've been trying to work from the tutorial for [Manual Encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption") .

For troubleshooting, 
1) I tried the boot-repair recommended fix, which had no impact.  I have no confidence that the "backup" I made at the time is of any value since I made it AFTER the issue started.
2) Also the Encryption [Troubleshooting]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation") page, but it is apparently not compatible with a 16.04 install since "refreshgrub" doesn't exist anywhere on disk.  I used "update-grub" instead.  This did not work.
3) Regarding the BIOS - I've fully reset it - just in case there are any special UEFI values stored there.  Secure Boot is not enabled.  I'm using AHCI mode currently and cannot recall what it was set to previously.


I'm in the Live USB for now,  so any timely feedback or recommendations is appreciated.

---

### Post by oldfred on 2019-01-06
When I update my UEFI, it resets all settings to default. I normally have to change many settings back again, some are optional and others required.
If you reset, you may have turned UEFI Secure boot on.
You want AHCI mode for drives, many often have RAID or Intel SRT settings even if one drive.
You generally do not want CSM/Legacy/BIOS mode. A few systems have needed it on for some strange reason, but you still boot in UEFI boot mode, not legacy.

I do not know LVM, nor encryption.
But to get Boot-Repair to work you often have to manually mount the LVM and decrypt your install for Boot-Repair to work. 
Then do not use a default auto  fix, but the advanced mode full uninstall/reinstall of grub.

If you were installing a second Ubuntu in UEFI mode, it will install its grub into the first drive seen.
Whenever I do a new test install to sdb or flash drive I make sure I have a back up of my ESP. Now I know the only real difference is the /EFI/ubuntu/grub.cfg and which partition/drive it has. That may be your issue. Check that file and make sure it is correct drive & UUID for your /boot partition. It is a standard grub configfile to load another grub.cfg or similar structured file.

You can see I edited mine, back to main working install on first drive.
```
fred@Bionic-Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid fbab1042-18dd-476c-9cf7-498a7a92a49e root hd1,gpt8 
search.fs_uuid [COLOR=#ff0000]c29fc361-ea05-420b-b919-850aeef65dd4[/COLOR] root hd0,gpt4
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

From my lsblk -f

&#9492;&#9472;sda4 ext4   bionic   [COLOR=#ff0000]c29fc361-ea05-420b-b919-850aeef65dd4 [/COLOR]/

I do not have a /boot partition, so full grub.cfg is just in / partition's boot folder. Yours should be UUID of /boot partition.

---

### Post by fr33z0n3r on 2019-01-06
Here is my grub.cfg from the LUKS volume

[HTML]root@ubuntu:/# cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid c5681ed1-1da3-4461-9dd0-2238f7576c89 root hd0,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg[/HTML]

That GUID lines up with my Partition #2 (linux /boot)

Does this look wrong?

Also - I have since physically disconnected the new 2nd SSD to prevent ongoing issues.

I did not manually mount my LVM to run boot-repair  but it seems obvious now that you say it.  I am assuming I do the same steps as in my Troubleshooting link and chroot to that LVM "root"?

Also - do you know the flags the partitions should have ideally?  I have forced the esp flag onto the Partition #1, which was set to msftdata (likely part of my original mistake - SOMEHOW!)

Here is the [boot-repair config I'm considering attempting]("https://imgur.com/a/hvtVtkl").

1. SecureBoot was enabled when I entered this.  Should I disable it? (it is disabled in the BIOS)
2. I set the /boot partition, which was showing unchecked.

---

### Post by oldfred on 2019-01-06
If UUID is your /boot & your partition is sda2 which is a normal LVM type install.
And yes boot flag must be on the ESP - efi system partition for UEFI boot.

I do not think parted used to have esp flag, but noticed last time I created an ESP, it also had esp flag. But when I checked boot flag  it also auto checked the esp flag. Next time I will just check esp flag. I know many in past have confused Windows BIOS installs where boot flag is required on primary NTFS partition with Windows boot files and grub does not use boot flag with BIOS/MBR boot. But UEFI want boot flag (maybe just esp now?) so it knows which FAT32 is the one with .efi boot files. A few users have more than one FAT32 partition.
Software is actually assigning a very long GUID type code that UEFI uses, flags or codes like gdisk uses are just to make it easier to understand.

---

### Post by fr33z0n3r on 2019-01-06
Thanks for your input thus far.  I'm going to take a stab in the dark on how to handle the LVM portion, as I cannot find clear directions for my situation.

I'm running boot-repair from the live USB (as opposed to from within the SSD via chroot)

I am unchecking the SecureBoot option that is automatically checked in boot-repair.
I've made backups in boot-repair.
I've manually backed up the grub.cfg files in /boot/efi and /boot/grub  just in case.

I have mounted the LVM/LUKS volume.

When I running boot-repair, it indicates "You may want to retry after decrypting your partitions" - which may imply that boot-reapir must run inside the chrooted LVM/LUKS install.  But I don't want to assume that.

I just wonder about the /dev/mapper notation for the "OS to boot" value.


UPDATE:  It did not fix the issue,  but I am now booting to an initramfs environment.

Thoughts on next steps?

---

### Post by oldfred on 2019-01-06
I do not know all the details on LMV & encryption.
But if you manually mount your encrypted install from the live installer, it should ask for you passphrase and be decrypted. Then Boot-Repair can see the Ubuntu install in you LVM volumes.
You are using volumes, not partitions, although volumes are inside one large partition. And ESP & /boot are small partitions. So I believe /dev/mapper is correct.

I do not use LVM, so these are just references I have found. I am familar with boot issues, grub & Boot-Repair, and only sometimes get involved with LVM & encryption.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://wiki.archlinux.org/index.php/LVM"]https://wiki.archlinux.org/index.php/LVM

      [/URL]
 Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621) 
   sudo apt-get install lvm2
sudo vgchange -ay /dev/mapper/ubuntu--vg-root
mount /dev/mapper/ubuntu--vg-root /mnt
# if UEFI ESP is usually sda1 & /boot sda2, you also need to mount ESP.
mount /dev/sda1 /mnt/boot 
   Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line) 
    [URL="https://wiki.archlinux.org/index.php/LVM"]
      [/URL]  chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380) 
    [ ]("https://wiki.archlinux.org/index.php/LVM")

---

### Post by fr33z0n3r on 2019-01-06
Wow,  that was quite an expedition!  I fixed my original issue and have been able to boot back into my Ubuntu 16.04 install.  There was a major issue once I solved this system bootability issue - noted at the bottom.

To solve that I did the following process (heavily copied from 2 sources):

1) [https://feeding.cloud.geek.nz/posts/recovering-from-unbootable-ubuntu-encrypted-lvm-root-partition/](https://feeding.cloud.geek.nz/posts/recovering-from-unbootable-ubuntu-encrypted-lvm-root-partition/)
2) [https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)


[LIST=1]
[*]Boot with a live USB/CD Ubuntu of the same version as the impacted instance. 
[*]Using fdisk -l and other disk management tools,  make sure you know all partitions names correctly. 
[*]To unlock your LUKS partition, enter the following command.  When running cryptsetup luksOpen, you must use the same name as the one that is in /etc/crypttab on the root parition (sda3_crypt in this example).
```

[LIST=1]
[*]sudo cryptsetup luksOpen /dev/<LUKS-PARTITION> <CRYPTTAB-LABEL-GUESS> 
[/LIST]

``` 
[*]Determine the volume name you need for the LUKS root volume <VOLUME-ROOT>.  It should be apparent  but it likely either 'system-root' or 'ubuntu-root'
```

[LIST=1]
[*]ls /dev/mapper 
[/LIST]

```
 
[*]Mount your system partition(s). Replace /dev/<BOOTPARTITION> with your /boot partition. Replace /dev/<EFIPARTITION> with your EFI System Partition (ESP), e.g. /dev/sda2 or /dev/nvme01n1p2.  Know/Guess what the volume name is as well <VOLUME-ROOT>```

[LIST=1]
[*]sudo mount /dev/mapper/<VOLUME-ROOT> /mnt/root 
[*]sudo mount /dev/<BOOTPARTITION> /mnt/root/boot 
[*]sudo mount /dev/<EFIPARTITION> /mnt/root/boot/efi 
[*]sudo mount --bind /dev /mnt/root/dev 
[*]sudo mount --bind /run /mnt/root/run 
[/LIST]

```
 
[*]Change root to the instance contained inside the encrypted LUKS (now unlocked by the first command ) ```

[LIST=1]
[*]sudo chroot /mnt/root 
[*]mount --types=proc proc /proc 
[*]mount --types=sysfs sys /sys 
[/LIST]

``` 
[*](if you do not know your crypttab label) Now that you are inside your impacted instance, you can inspect your logical volume setup with this encrypted LUKS container. ```

[LIST=1]
[*]cat /etc/crypttab 
[/LIST]

``` 
[*](if you do not know your crypttab label) You will likely need to restart this process now that you have the  correct name for the volume determined in the last step (which may or may not matter - UNKNOWN)  I recommend restarting the entire Live USB session. 
[*]After ensuring that the labels/names used in all previous steps are correct, perform the following command to update the correct config ```

[LIST=1]
[*]update-initramfs -c -k all 
[/LIST]

``` 
[*]Exit and shutdown/restart 
[/LIST]

[SIZE=5]_**NOTE**_[/SIZE] 
At this point I experienced a complete loss of DNS resolution from my "impacted" instance after I did all MY troubleshooting (which exceeds these directions).  You may also.   You would have to do research/troubleshooting from a different device (I used my phone - ARGH!)

[SIZE=5][B]Readup and plan on learning how to disable "systemd-resolved".

[/B]NOTE 2:
[SIZE=2]Here are my actual commands used:

```
sudo cryptsetup luksOpen /dev/sda3 sda3_crypt
sudo mount /dev/mapper/ubuntu-root /mnt/root
sudo mount /dev/sda2 /mnt/root/boot
sudo mount /dev/sda1 /mnt/root/boot/efi
sudo mount --bind /dev /mnt/root/dev
sudo mount --bind /run /mnt/root/run
sudo chroot /mnt/root
mount --types=proc proc /proc
mount --types=sysfs sys /sys
update-initramfs -c -k all
```[/SIZE][/SIZE]```


```[SIZE=5][SIZE=2]
To disable [SIZE=5][SIZE=2]systemd-resolved
[/SIZE][/SIZE][/SIZE][/SIZE][SIZE=5][SIZE=2]```
sudo systemctl disable systemd-resolved.service
sudo systemctl stop systemd-resolved
nano /etc/resolv.conf
```[/SIZE][/SIZE][SIZE=5][SIZE=2]add in DNS name servers
```
 nameserver  1.1.1.1
 
```[/SIZE][/SIZE]```
[SIZE=5][SIZE=2][SIZE=5][SIZE=2]nameserver 8.8.8.8[/SIZE][/SIZE][/SIZE][/SIZE]
```

---

