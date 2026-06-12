---
title: "Want to use rsync to backup to a cloned drive of my system's drive"
date: 2023-07-29
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2023-07-29
What I am trying to do is come up with an easy way to do my backups. I have cloned my system drive by booting into a live Ubuntu USB drive and running dd at a command prompt, like so:


```

# sudo dd if=/dev/sda of=/dev/sdb bs=4096 status=progress

```


I wish to be able to mount the cloned drive and occasionally back my system up to it using rsync to sync the home directories.


Unfortunately I cannot mount the cloned disk while running from the source disk. After I type in the encryption passphrase I get an error in a window:


```

Unable to mount 511 GB Encrypted
Error unlocking /dev/sdd5: Failed to activate device: File exists

```


I am assuming that my problem is that both my system disk and the cloned disk havce the same UUIDs. You can see that here:


```

# lsblk -f
sdb                                                                                                           
&#9500;&#9472;sdb1              ext4        1.0                     89258987-c83e-4e11-b679-5f96fab97741      369M    40% /boot
&#9500;&#9472;sdb2                                                                                                        
&#9492;&#9472;sdb5              crypto_LUKS 1                       20670a50-0e6a-4d04-8b26-ae56d51a1518                  
  &#9492;&#9472;sda5_crypt      LVM2_member LVM2 001                Paptmk-FwvD-3Gyj-Opmo-c8X8-z1rx-VkRZFU                
    &#9500;&#9472;ubuntu--vg-root
    &#9474;               ext4        1.0                     ab49719a-3024-4dab-9702-5340511fa6bb    271.2G    37% /var/snap/firefox/common/host-hunspell
    &#9474;                                                                                                         /
    &#9492;&#9472;ubuntu--vg-swap_1
                    swap        1                       34c0bc2d-20c1-4a47-ad13-2fdd5c2dec1e                  [SWAP]
sdc                                                                                                           
&#9492;&#9472;sdc1              crypto_LUKS 1                       50ea34c4-7dd1-43d5-a43a-e7a2e79e4571                  
  &#9492;&#9472;luks-50ea34c4-7dd1-43d5-a43a-e7a2e79e4571
                    ext4        1.0      123            8d59b1cd-4a05-49d7-92d1-b65eeb11adc7      6.4G     7% /media/robert/123
sdd                                                                                                           
&#9500;&#9472;sdd1              ext4        1.0                     89258987-c83e-4e11-b679-5f96fab97741                  
&#9500;&#9472;sdd2                                                                                                        
&#9492;&#9472;sdd5              crypto_LUKS 1                       20670a50-0e6a-4d04-8b26-ae56d51a1518                  

```


As you can see the UUIDs for sdb1 is identical to sdd1 and the UUID for sdb5 is identical to sdd5.


Now I know if I boot in to a live USB drive I can change the UUID of the cloned drive. When I boot in to the live USB drive, the cloned drive becomes /dev/sdc. With something like this, I can change the UUID with something like this:


```

# umount /dev/sdc1
# tune2fs -U random /dev/sdc1
# mount /dev/sdc1
# lsblk -f

```


I copy the UUID of sdc1.
Then I unlock the sdc5 partition with the "disks" utility


```

# cd /media/ubuntu
# sudo mkdir temp
# sudo mount /dev/mapper/ubuntu--vg-root /media/ubuntu/temp

```


I edit /media/ubuntu/temp/etc/fstab


```

# sudo gvim /etc/fstab

```


And I make /etc/fstab look like this:


```

#<file system>                <mount point>   <type>  <options>         <dump>        <pass>
/dev/mapper/ubuntu--vg-root   /               ext4    errors=remount-ro 0             1
UUID=<paste new UUID here>    /boot           ext4    defaults          0             2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw                0             0

```


Then


```

# umount /media/ubuntu/temp

```


I deactivate the sdc5 partition with "gparted".
I lock the sdc5 partition with the "disks" utility.


```

# cryptsetup luksUUID --uuid=`uuidgen` /dev/sdc5

```


I unlock sdc5 with the "disks" utility


```

# sudo mount /dev/mapper/ubuntu--vg-root /media/ubuntu/temp
# lsblk -f

```


I copy the UUID of sdd5.
I edit /etc/crypttab to look like this:


```

sda5_crypt UUID=<paste the new UUID here> none luks,discard

```


Now what's interesting here is this:


```

# lsblk -f
sdc                                                                                                        
&#9500;&#9472;sdc1        ext4                                   8ac757fe-b60c-467b-9333-2e14dadfbfcd                  
&#9500;&#9472;sdc2                                                                                                     
&#9492;&#9472;sdc5        crypto_LUKS                            3e0b83a1-c27e-4915-9cb8-f343908bed64                  
  &#9492;&#9472;luks-3e0b83a1-c27e-4915-9cb8-f343908bed64
              LVM2_member                            Paptmk-FwvD-3Gyj-Opmo-c8X8-z1rx-VkRZFU                
    &#9500;&#9472;ubuntu--vg-root
    &#9474;         ext4                                   ab49719a-3024-4dab-9702-5340511fa6bb    269.8G    37% /media/ubuntu/temp
    &#9492;&#9472;ubuntu--vg-swap_1
              swap                                   34c0bc2d-20c1-4a47-ad13-2fdd5c2dec1e

```


Some of the UUIDs on the cloned disk are still exactly the same as the source disk.


Now I have to repair GRUB. I've done this in the past to unencrypted drives, but I've never done it to an encrypted drive. I'll assume this works on an encrypted drive just as it works on an unencrypted drive.


```

sudo apt-get-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair

```


Using "boot-repair" I first fix the master boot record and then I fix GRUB. I take out the live USB and boot from the cloned drive.


I get to the screen where I am normally asked the encryption password and it says:


```

cryptsetup: Waiting for encrypted source device UUID=20670a50-0e6a-4d04-8b26-ae56d51a1518 ...

```


This was the originial UUID of /dev/sdb5 on the source disk and of /dev/sdc5 on the cloned disk before I changed it. It seems that the /boot partition is somehow looking for this UUID. It also means that "boot-repair" did not take care of this when when I ran it.


Later I tried to mount this disk while running the system on the source disk. I got an error when I tried to mount the encrypted cloned disk. Then I got this:


```

# lsblk -f
sdb                                                                                                   
&#9500;&#9472;sdb1         ext4      1.0                    89258987-c83e-4e11-b679-5f96fab97741      369M    40% /boot
&#9500;&#9472;sdb2                                                                                                
&#9492;&#9472;sdb5         crypto_LU 1                      20670a50-0e6a-4d04-8b26-ae56d51a1518                  
  &#9492;&#9472;sda5_crypt LVM2_memb LVM2 00                Paptmk-FwvD-3Gyj-Opmo-c8X8-z1rx-VkRZFU                
    &#9500;&#9472;ubuntu--vg-root
    &#9474;          ext4      1.0                    ab49719a-3024-4dab-9702-5340511fa6bb    271.2G    37% /var/snap/firefox/common/host-hunspell
    &#9474;                                                                                                 /
    &#9492;&#9472;ubuntu--vg-swap_1
               swap      1                      34c0bc2d-20c1-4a47-ad13-2fdd5c2dec1e                  [SWAP]
sdc                                                                                                   
&#9492;&#9472;sdc1         vfat      FAT32                  55BB-0DF4                                 7.4G     0% /media/robert/55BB-0DF4
sdd                                                                                                   
&#9492;&#9472;sdd1         crypto_LU 1                      50ea34c4-7dd1-43d5-a43a-e7a2e79e4571                  
  &#9492;&#9472;luks-50ea34c4-7dd1-43d5-a43a-e7a2e79e4571
               ext4      1.0     123            8d59b1cd-4a05-49d7-92d1-b65eeb11adc7      6.4G     7% /media/robert/123
sde                                                                                                   
&#9500;&#9472;sde1         ext4      1.0                    8ac757fe-b60c-467b-9333-2e14dadfbfcd    374.8M    39% /media/robert/8ac757fe-b60c-467b-9333-2e14dadfbfcd
&#9500;&#9472;sde2                                                                                                
&#9492;&#9472;sde5         crypto_LU 1                      3e0b83a1-c27e-4915-9cb8-f343908bed64                  
  &#9492;&#9472;luks-3e0b83a1-c27e-4915-9cb8-f343908bed64
               LVM2_memb LVM2 00                Paptmk-FwvD-3Gyj-Opmo-c8X8-z1rx-VkRZFU

```


My guess is that it hung up because /dev/sde5 would have mounted onto "ubuntu--vg-root" and "ubuntu--vg-swap". Those are already in use.


I don't know how to approach this problem.

---

### Post by TheFu on 2023-07-29
a) disk cloning isn't a proper backup.  It is a way to quckly replace a dead disk.  Disks with identical UUIDs cannot be placed into the same computer.  The OS gets confused.  There is no way around this without manually changing the UUIDs post-clone and modifying all the config files under /etc/ to use the new UUIDs.

b) disk cloning when LVM is used also causes issues because the VG and LV names will be identical.  That cannot be allowed.

c) disk cloning of encrypted partitions also causes problems since the name of the LUKS container will be in conflict.  That cannot be allowed.

There are solutions to each of these issues, but cloning isn't one of them.  The only way to effectively clone a disk is to boot from alternate media or a separately installed OS on the system, then use that to create the clone.  BTW, dd isn't the best tool for cloning.  ddrescue is better because it doesn't stop at the first error seen. It keeps going.  Of course, there are other tools like clonezilla, but I've always found those to be less useful/more complex than I needed/wanted.

So, if cloning a disk/partition isn't ideal, what is a better alternative?  Any of the file-system-based tools are.  Most are based on librsync, but not all. Each has pros and cons.  For example, rsync has been used as a mirroring tool for a long time and it does it well.  Heck, I'm using it to migrate everything off 8 10+ yr old HDDs onto a single, larger, HDD right now.  The command is:
```
cd /misc/mybook  # that's the source directory
sudo rsync -av --progress DONE  Other  /d/rom/misc/2TB/

```
DONE/ and Other/ are directories inside  /misc/mybook/.  Both file systems (the source and target) are locally mounted, but either could be over the network.  It is best to "pull" backups from each client to your backup system.  If there's just a backup drive, then that isn't an option. Malware and crypto-ware could corrupt the backup storage.  Anyway, this will clone the SRC directories and files to the TARGET.  1 copy.  I used this when I stopped manually copying files as a backup method, which I did for far too many years, I'm embarrassed to say.

Versioned backups is the next step in backup sophistication.  With versioned backups, the backup software manages the versioning in an efficient manner.  10 versions or 90 or 365 versions don't require 10x the storage.  Using hardlinks which are built into most native Linux file systems, files that didn't change from the last backup are only stored once regardless of 10, 90 or 365 or 500 versions. Each "version" pointing to the same file just uses an inode.  Wikipedia has an article on inodes, if you want to know more.
rsync+hardlinks has been used decades as a backup method. I used it for a long time, until a restore failed.  That taught me about a failure in the hardlink method.  Only the most recent owner, group, ACLs and xattrs are retained.  Most of the time, that doesn't matter ... er ... until it does. Then you are screwed.  Modern backup tools handle versioning not just the data, but the metadata for each file as well.  rdiff-backup deals with that extra stuff and the command is very much like the command for rsync, but it handles the versioning for us.  rdiff-backup is the same speed as rsync for the very first version, but the later versions are much, much, faster. rdiff-backup isn't perfect, but it does have some of the nice things that rsync does - like the last backup looks just like an rsync mirror. Older versions are stored as reverse diff compressed files.  There's nothing proprietary in the backup storage.  Restore of the latest files can be performed with a copy, rsync, or "rdiff-backup -r".  Older versions can manually be restored, but "rdiff-backup -r" is much easier and accepts many different ways to specify which version to restore.

I've posted many times about simple rdiff-backup commands/scripts and the restore process.  It is extremely flexible at restore time, since the backups are disconnected from the underlying storage.

So, if we start over from the beginning, assuming you want like-for-like, but not true clones, the fastest method really is to treat the backup like data storage and never plan to use it as an OS/boot device.  Then you can manually copy the partitioning, manually create a LUKS container, open that LUKS container, create LVM objects as needed inside and use the LVs as data storage for backups.  You can even have the LUKS automatically open when connected to specific computers, but require manual opening with a key-file/passphrase on any other computer, if you like.  This won't stop govts, but it will make sending a disk in for warranty service safer.

For the setup you have, you cannot use cloning as a backup method, unless you have multiple computers.

Completely off-topic, but please use **sudoedit** to modify system files.  You can specify the EDITOR environment variable with any editor you prefer and it will be used.  using sudo directly with GUI programs is often dangerous.

---

### Post by robertcull1 on 2023-07-30
Thank you for this thoughtful post. You have opened a different world for me when it comes to computer backup. I will study what you have said on my own and do my best to figure it out. If I have any problem, I will come back here and ask about it or perhaps start a new thread if that is more appropriate.

Thumbs up, TheFu!

---

