---
title: "Problem with install linux with raid 0 - mdadm"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by patryk6 on 2015-09-04
Hello,

after installation Linux (all distro same problem), when I run laptop then i recive error "Invalid partition table!" i can tape Enter and system will start, but I need to solve this problem.

First of all in my laptop I have 2x Samsung 840EVO SSD, and want to create software RAID 0. To create Raid use mdadm, but maybe i make somethink wrong.

There are list of steps what I do:

1. Run Xubuntu (or other distro) from Live USB.

- [COLOR=#000000][FONT=Verdana]apt-get -y install mdadm 
- [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mdadm --assemble --scan

- [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]parted /dev/sda 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana](parted) mklabel gpt [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 1MB 800MB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 800MB 8.8GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary linux-swap 8.8GB 10GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 10GB 100% [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) quit 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]- parted /dev/sdb 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana](parted) mklabel gpt [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 1MB 800MB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 800MB 8.8GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary linux-swap 8.8GB 10GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) mkpart primary ext4 10GB 100% [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](parted) quit [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]3. 
mkfs.ext4 /dev/sda1 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mkfs.ext4 /dev/sda2
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mkfs.ext4 /dev/sda4
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mkfs.ext4 /dev/sdb1
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mkfs.ext4 /dev/sdb2
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mkfs.ext4 /dev/sdb4

4. 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mdadm --create /dev/md0 --level 0 --raid-devices 2 /dev/sd[ab]2 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mdadm --create /dev/md1 --level 0 --raid-devices 2 /dev/sd[ab]4 [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]

Start Install OS, next select to manual use partitions and next create new parttion tables at md0 and md1.

md0 mount as "/ "
md1 mount as "/home "
sda1 mount as "/boot"
sda3 and sdb3 "linux-swap"

5. after installation I don't reboot laptop

6. 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mount --bind /dev/ /target/dev
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mount -t proc proc /target/proc 
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]mount -t sysfs sys /target/sys/

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]chroot /target

7.
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]echo "nameserver 8.8.8.8">>/etc/resolv.conf    (without this can't download nothink)

8.

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]apt-get install mdadm
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]apt-get install --reinstall grub-pc
exit
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
9. Reboot laptop.

Please help me solve this problem :)


[/FONT][/COLOR]

---

### Post by MAFoElffen on 2015-09-05
Question-- Why ar you installing manually and not installing mdadm from partman in the installer from the LiveCD?

Just an offhand observation:
 - In #1 you install mdadm...
 - In #8 you install mdadm (as if it was not installed before.)
After step #1 you configure 2 mdadm volumes, but have /boot in a traditional volume and filesystem... 

If boot is in a regular partition, why do you need to reinstall grub after the install? Would the install install grub as normal?

Maybe I'm just confused. I remember a few years back when you had to do it manually... but the hasn't the installer in Xubuntu adpated to mdadm now in partman?

So by installing mdadm again in step #8, first, wouldn't that fail, with "version already at the newest version?" If you forced it, wouldn't that blank definitions over what your had configured?

Why 2 swaps? I've never seen that before... I've done it to see what would happen, by adding 2 swaps in the fstab... I may be wrong, but from what I saw, that if only seems to use the last swap line it sees.

---

### Post by patryk6 on 2015-09-05
Hi,

I just use this guide:  [http://forum.linuxmint.pl/index.php?topic=7177.0](http://forum.linuxmint.pl/index.php?topic=7177.0)

I'm a new linux user and don't know a lot about this system and need guides. Have you any other guide who expleins step by step what to do?

---

### Post by MAFoElffen on 2015-09-05
What version of what distro flavor of Ubuntu (or it's direct branches) would you like to install and I'll create you one. You have already told us your layout in your first post. I'll create it as a test case and take screen shots for you with an explanation of the whats & whys.

In your plan, you have 2 disks, sda & sdb. Your want a raid 0 partition for root and a raid 0 partition for home. You want a separate boot and swap. If you are not doing those in raid, those could be the same partition number on the 2 disks, that way you don't waste 2 partitions. What I do here in a small, separate disk for boot and swap... Boot is just use when starting up. Swap is used mosting when running, but also when starting (if it was asleep or hibernating). You had the right idea with the size of boot. Most guides say 500 MB... but when you do that size, you later run into running out of space problems.

So that will be your layout right? 3 partitions each disk, 2 each as raid 0 members? 

Now other questions. Why RAID? Why RAID 0? First off, Raid does not take the p[lace of a good Backup. You have a backup plan right? You know you are spanning disks with no parity right --> If your only goal is to span disks (without parity), then why not LVM? If RAID 1, then you would be doing mirroring. LVM also has Mirroring options... Or if this is a learning experience, why not LVM on RAID?

I'm thinking you might want to use RAID 0 because of room to grow... But my choice for that, these days would be an LVM PG, with separate VGs for root, home and swap... The you just add disks as extents and grow your filesystems. Just more to think on...

---

### Post by patryk6 on 2015-09-05
I want to use Xubuntu 15.04.

Yes you have right with layout of my partitions.

I want RAID 0 for performance, I know this is not safe, but I create every weekend backup of my OS ;)

Is LVM striping better then RAID 0?

Try to install Xubuntu at my computer after low level format both SSD and without creating RAID 0, and still have same problem. 

Maybe somethink is wrong with my laptop (Dell Latitude E6430)?

---

### Post by MAFoElffen on 2015-09-06
There's you problem/challenge...

Here's your laptop manaual: [http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6430_Owner%27s%20Manual_en-us.pdf](http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e6430_Owner%27s%20Manual_en-us.pdf)

On page 64, in the BIOS setup... you have an option for Legacy or UEFI BIOS. If you switch that option over to Legacy, using the instructions you were using will work. (Since Ubuntu will be the sole OS, you could use either options.) If you want to continue to use UEFI BIOS, use one of Yann's [BOOT Repair LiveCDs]("http://sourceforge.net/projects/boot-repair-cd/files/"). (<-- DL at that Link)  It will see EFI BIOS and create the EFI boot file for Grub to be able to boot Ubuntu from UEFI mode...

See if that works out for you.

---

### Post by MAFoElffen on 2015-09-06
On Raid or LVM... I used to used RAID for everything. First Hard RAID, then Linux Software RAID (mdadm). I am the Project leader for mdadm-gui project. (it's still far from done) I do a lot of Server support. Besides my customers, I have 14 servers here, 8 workstations, 4 laptops and 2 tablets. For the servers, I also have 4 drive storage enclosures...

I didn't know much about LVM until 2-1/2 years, when I forced myself to learn it. You know, I was so impressed that most my servers and all my virtual hosts are now running LVM. It's quick and easy. It is very flexible. It is somewhat forgiving.

For a while I was doing LVM on top of raid 6. On about half the boxes here now, I've just rest them up on LVM (without RAID).

You can take a backup, then take snap shots from then on.... That makes my backups faster, because the snapshots consist of changes.... Smaller, faster... and I now have incremental rollbacks.

At first it is like learning a new language and a different way of doing things. But it is similar to madam in ways. The learning curves is no more daunting than mdadm was. In fact, I think is was easier.

For setup, for a GPT disk on an EFI system, On disk 0 you have a bios_grub partition, EFI partition, boot partition (ext2), main partition (ext4)... All your other disks you partition and add ext4. The sises of the partition can vary, where mdadm they needed to match in size. That makes it easy to add extents of various disks.

For maintence and reconfigs, you can shrinks filesystems, drop out a disk (say to either remove or change out)... only caviot is a little extra work to change out a Disk 0. It is depnedable enough and prven enough to add it in as a default part of partman in the installer of Ubuntu.

Here's were the difference is for me. Now that you've played with mdadm... Think about how long it takes to create/assemble a big RAID container.Instead of long res-asembel times trying to recover... sometimes it's lot faster to create new and restore your backup... and be back up again. Now think LVM, where you can be back up again in a quarter of the time. I still have some application were I still do RAID 1 for system and RAID 6 (balance of) with LVM... but those are where the data security is priority over my uptime.

---

