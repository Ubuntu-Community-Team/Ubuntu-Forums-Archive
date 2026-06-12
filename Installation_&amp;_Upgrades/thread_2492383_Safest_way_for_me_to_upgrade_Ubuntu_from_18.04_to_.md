---
title: "Safest way for me to upgrade Ubuntu from 18.04 to 22.04"
date: 2023-11-09
forum: Installation &amp; Upgrades
---

### Post by gipsyshadow on 2023-11-09
Hi all,
I've to upgrade my Ubuntu (Gnome DE) from 18.04LTS to 22.04LTS. I've got only one disk and my partition list is:
```

/dev/sda1     1024000    1228799     204800   100M EFI System
/dev/sda2     1228800    1261567      32768    16M Microsoft reserved
/dev/sda3     1261568  103560396  102298829  48,8G Linux filesystem
/dev/sda4   103561216  266242047  162680832  77,6G Microsoft basic data
/dev/sda5   266242048  286722047   20480000   9,8G Linux filesystem
/dev/sda6   286722048 1953523711 1666801664 794,8G Microsoft basic data

```
and this is the graphical view with gparted
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293035&stc=1[/IMG]
As you can see I've got more than 500GB free disk space so I can resize them before upgrading because I've red newest releases need more disk space due to different snap management, right?
As you can see my home and root are in 2 different partitions and I'd like to upgrade only root so I can keep my sw/system settings on my home.

First of all and considering I won't install other sw in my new Ubuntu release, what new sizes do you suggest for root and home partitions?

Now consider my biggest issue: my internet connection is not stable, I mean it can be stable for all the day along but it can be unstable and I could be disconnected 2-3 or more times in a day. Unfortunately I can't solve this issue. So this is my scenario.

That said, what way do you suggest to use for a "safe" upgrading?
I'd like to avoid a fresh root installation by bootable usb and without internet connection because I'd lose all my installed sw so I'd re-install them.
Else if I started upgrading automatically and my internet connection stopped... would partial downloaded packages erase and could I re-start it again or I'd get damaged packages anyhow with an unstable new system?

---

### Post by ubfan1 on 2023-11-09
Your free disk space is nowhere near your existing root.  My (default) snaps take 9GB (du -s /snap).  Consider installing a new root in the free space, run in parallel until you are happy, and then just remove the old root.  This approach might mess with how you use your /home partition -- Do not mix the dot files of different OSes (.config, .cache, .local, etc.).  I'd use the /home as a data partition, give each user (if more than one) a dir on it, and use links in the OS /home/usr of each OS for dirs like Documents, Music, etc.  That way, each OS keeps their own dot files.
Upgrades typically do the downloads of new packages first, then apply them, so interrupts should not hurt.

---

### Post by TheFu on 2023-11-09
IMHO, upgrading more than one time from LTS-->LTS--> LTS is asking for problems because many core services get changed over 2 LTS cycles.  This leaves the new system is an odd situation with 4+ yr old core services that aren't being maintained and may or may not be used.  When something bad happens, nobody will be able to help.

So, my recommendation is to backup everything you don't want to lose, assuming you don't already have excellent backups, then wipe the entire storage and start over.  This cleans out cruft the all OSes leave behind with every attempted "upgrade", especially over more than 4 yrs of releases.

Also, the last time I tried to upgrade, that process took almost 3 hrs, when doing a fresh install and resetting all my data and system settings would be less than 1 hr.  The longer that parts of disks aren't force re-written, the more likely those areas are to failure.  This is commonly why MS-Windows issue seem to be seen mostly at boot - because the boot areas of the disk are seldom re-written under that OS.

Any upgrade that fails along the way for any reason means you need to restore from backups and try again.  That's the best case.  While you might be able to manually solve things, that is extremely dependent on your personal skills, not ours.  I once started an upgrade with the wrong version of perl setup (I'm a perl programmer and run multiple virtual perl environments on my systems to ensure I don't touch the system perl).  Anyway, the failures were many and odd, but the new OS did boot and run, just many helpers failed to be there.  I screwed around trying to fix it for a few hours, then decided that wiping, doing a fresh install, and restoring my data and settings would be faster and less hassle.  It was.  And all the cruft was gone too - BONUS!

I have made lots of posts here about disk layouts for Linux systems.  None are for dual boot, since I stopped using dual boot around 2010.  IMHO, it is just too much hassle when virtual machines meet all my needs.  No need for dual booting in my use scenarios. YMMV.

---

### Post by yancek on 2023-11-09
Ubuntu 18.04 support ended in April, 2023 so go to the link below and read through it for an explanation of the steps needed.  You are aware that you can only upgrade from one LTS to another LTS, not directoy to 22.04.  You would need to go to 20.04 and after that completes, upgrade to 22.04 if you want.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Given your system, it would be much faster to simply install 22.04 after downloading the iso file and writing it to a USB.  You would first backup all personal data and any configuration files you have modified.  During the install (use the manual or something else option), select the root filesystem partition (sda3) show by the / mount point and install there and format that partition.  Select your /home partition (sda5) for /home and do NOT format that partition.  If you format /home, you lose all your data.  This should take about 30 minutes or less whereas the upgrading method will probably take 4+ hours. 

>  As you can see I've got more than 500GB free disk space

Not according to what you posted.  Your fdisk output doesn't show any relevant information with regard to sectors and adding up your various partitions, it is the entire disk.  sda6 takes up almost 80% of the drive and is a windows ntfs filesystem partition.  Just data?  You can create another partition for Ubuntu data after sda6 after shrinking it or you could move sda6 to the right and free space before it so you can expand sda5 for your home partition.  The second option would require also moving all the data on that partition which would take some time as it has over 250GB and there is always the possibility of data loss with this method.  Not sure exactly what your intentions are here.

---

### Post by MAFoElffen on 2023-11-09
Before making any major changes, whether that is changing the size of partitions or doing a release upgrade... Get a good backup that you can restore to.

---

### Post by gipsyshadow on 2023-11-09
Honestly I didn't think there could be so many complications in double-upgrading my Ubuntu in my scenario anyway it's much better I know them before starting!
I'm a newbie and I'll avoid to be in a gum tree so I think the safest way for me is a fresh root installation though I've to re-install all my sw.

These are my new questions:
- is there a way (eg. via shell) to get a complete list of my Ubuntu installed sw?
- if I'll do only a fresh root installation and I'll reinstall all my programs, can I be sure my settings (eg. in firefox) will be kept?
- what sizes do you suggest my new home and root partitions would be?

---

### Post by MAFoElffen on 2023-11-09
The easiest way is to run the UbuntuForums 'system-info' Script in my signature line... ear the end of the report is a section where it lists all packages that are marked as User Manually installed...

I often use that section to reinstall applications after a release migration.

---

### Post by guiverc on 2023-11-09
I'll provide my 2c, but its mostly thoughts based on what I read.

- My /snap/ is 9.4GB, so roughly what @ubfan1 reported
- I don't see the difficulty in two *release-upgrades; *believing you have sufficient free disk space (in /). 

ie. read the Ubuntu 20.04 LTS Release notes and follow instructions on upgraded 18.04 system to 20.04.  Reboot & quick test to ensure all is good.

then repeat process to go from 20.04 to 22.04; ie. again reading the release notes & follow the provided instructions (upgrading from 20.04).  reboot & test.  It'll just take time...

An alternative I often use, esp. with desktop systems, is to perform the upgrade via re-install. I've written about it here ([https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)) but it's just triggering a non-destructive re-install by re-using existing partition(s) **without format** which is what triggers the install type. This allows you to do it in mere minutes (*longer than a clean install, but it has to download the manually-installed packages you added as well where they're not on the ISO*). This method copes with Ubuntu repository software, and may or may not work with 3rd party packages (*will depend on how they were packaged, if they allowed for this or didn't so as to have latest packages for older release*). Regardless I do like this method for desktop installs (*esp. flavors*), but if you have a server system or use server apps that have configs stored in system directories; you'll need to restore them - so ensure you have good backups.  This is just an *unclean* install.

---

### Post by Tadaen_Sylvermane on 2023-11-09
I recently decided to try Mantic from a Jammy installation. I know the advisement is to use the upgrader tool. But I had no trouble getting to mantic with manually editing the sources.list upgrading each release in turn with apt-upgrade && apt full-upgrade. Let me fix issues in between. In my case there were none. But I don't use PPAs and any non repo packages are flatpaks or snaps. I honestly believe those are why people have upgrades that don't go well. Outside of that I don't see what that program / script offers beyond a single command instead of a sequence. Hides the complexity. Nothing more.

TLDR do it manually...

---

### Post by Dennis N on 2023-11-09
At least for an 18.04 system on esm, you might be able to still use Software Updater to get to 20.04. I say this because mine offers to do that with each esm update. See the attached image. I don't know if esm enrollment is necessary - it may be. I also didn't actually try the upgrade to see how well it works.  

esm extended security maintenance

---

### Post by TheFu on 2023-11-10
> **gipsyshadow said:**
> 
These are my new questions:
- is there a way (eg. via shell) to get a complete list of my Ubuntu installed sw?
- if I'll do only a fresh root installation and I'll reinstall all my programs, can I be sure my settings (eg. in firefox) will be kept?
- what sizes do you suggest my new home and root partitions would be?

There are multiple ways for software to be installed, so there will never be 1, single, method, to get a list. However, the 2 most popular use APT and snap packages.  Getting lists of those are trivial.

**apt-mark show-manual**   # save that output to a file.  It can be fed in post-install to load the manually installed packages.  Sadly, not just the packages we actually, specifically, request are in that list, but all their dependencies too, so it will be long with lots of libraries that could have dependency changes.

**snap list** is the other.  This one generates ugly output for reinstall, but should be much shorter.  I suspect there will only be 10 or less packages you need to have listed/saved.  It is possible to get backup snap packages 100%, but it is extremely wasteful and all the details about it are important to understand beyond the single command.  However, it can include data in the backups for specific users, assuming you didn't screw around and change any default locations.  In the end, the backup is a tgz file, which makes it good for moving systems, but terrible for daily, versioned, backups.

35G for /.  Never larger.
Every other size depends on the use, workloads, and specific packages and types loaded.
For non-trivial systems, I use LVM since I know I can never, ever, guess correctly on sizes.  LVM allows expanding specific LVs as needed while the system is live and working.

Here's a real system, but not necessarily what you need:
```
$ lsblkt   # <----- That's an alias 
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1                          disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M    340M    42%                /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G   25.4G    21%                /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G   15.1G    18%                /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.4G     5% tmp01          /tmp
  &#9500;&#9472;vg01-home01                  lvm   ext4                 20G   12.9G    30% home01         /home
  &#9500;&#9472;vg01-libvirt--01             lvm   ext4                137G    2.8G    98% libvirt--01    /var/lib/libvirt
  &#9500;&#9472;vg01-lxd--containers--01     lvm                        30G                               
```

For a different view of the storage:
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.1G   26G  22% /
/dev/nvme0n1p3                           ext4  672M  283M  340M  46% /boot
/dev/nvme0n1p2                           vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-home01                  ext4   20G  5.8G   13G  32% /home
/dev/mapper/vg01-tmp01                   ext4  3.9G  217M  3.5G   6% /tmp
/dev/mapper/vg01-var01                   ext4   20G  3.5G   16G  19% /var
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt
```

Notice that I haven't assigned even 50% of the storage.  Part of LVM's power is flexibility, but only if we allocate only what we actually require.  For example, my vg01-libvirt--01 LV is specifically sized to hold 1 specific VM.  Most of my VMs use LVM, but aren't "mounted" onto the host system.  My /var/ is larger than I'd normally have. I try to minimize snap use, but do have 1 that I absolutely need, so I can't just purge everything snap-related from the system. Sigh.

And I'm running is a fairly minimal setup without and DE and 95% of the normal GUI programs aren't installed.  To me, they are just bloat.  Because I don't dual boot, my EFI barely gets used. No bloated EFI crap from other OSes.

I keep media files on network storage, not in my HOME, so no HOME directories really need too much storage.  It wasn't always that way, but I've learned over the decades why keeping different types of files in different places and striving to have just 1 copy as the "master" is important.  Without a master copy, other copies expand exponentially and soon there will be 10 copies with no idea which is the latest and best.  Keeping the right number and in the right place, always, is part of storage management.

---

### Post by gipsyshadow on 2023-11-11
Well, I got a bit confused... definitely now what's the least (probably?) problematic way to get a new ubuntu 22.04lts root from 18.04lts: 2 consecutive automatic system lts upgrades or just one fresh installation by bootable usb? I'm a very newbie so the sense of "safest" in the title is "least problematic" for me.
If the answer was the 1st one then I'd want to know what kind of checks I'd do after the 1st upgrading (18.04->20.04) and before the 2nd one (20.04->22.04) to ensure my new root/system is still in "health".

---

### Post by TheFu on 2023-11-11
> **gipsyshadow said:**
> Well, I got a bit confused... definitely now what's the least (probably?) problematic way to get a new ubuntu 22.04lts root from 18.04lts: 2 consecutive automatic system lts upgrades or just one fresh installation by bootable usb? I'm a very newbie so the sense of "safest" in the title is "least problematic" for me.
If the answer was the 1st one then I'd want to know what kind of checks I'd do after the 1st upgrading (18.04->20.04) and before the 2nd one (20.04->22.04) to ensure my new root/system is still in "health".

Nothing is guaranteed.  The risks of upgrade failures increase the most complex the upgrade is.
Complications include:
[LIST]
[*]having hardware that isn't well-supported (did you have to do anything special previously to get it working?)
[*]more than one upgrade
[*]installing lots of non-default software
[*]installing software that is outside the core Ubuntu Repos
[*]installing PPAs and software outside APT
[*]Installing .deb files directly (this often breaks dependencies)
[*]using customized GUI addons
[/LIST]

I suspect what you think is a validation of a file system isn't what Linux thinks is a file system check.  I don't remember what the default period is for automatic fsck runs on each file system.  I have mine manually set to be every 30 days, but I think the default may be every 60 reboots.  In my world, 60 reboots could be 3+ yrs.  Here are the number of times I've power cycled some of my HDDs:
```
$ egrep Power_Cycle_Count  smart.2023-11-06.sd*
smart.2023-11-06.sda: 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       33
smart.2023-11-06.sdb: 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       81
smart.2023-11-06.sdc: 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       138
smart.2023-11-06.sdd: 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       12442
smart.2023-11-06.sde: 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       113
smart.2023-11-06.sdf: 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       187

```
All those drives are over a year old.
```
smart.2023-11-06.sda:  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       29656
smart.2023-11-06.sdb:  9 Power_On_Hours          0x0012   091   091   000    Old_age   Always       -       66721
smart.2023-11-06.sdc:  9 Power_On_Hours          0x0012   091   091   000    Old_age   Always       -       66894
smart.2023-11-06.sdd:  9 Power_On_Hours          0x0012   098   098   000    Old_age   Always       -       14422
smart.2023-11-06.sde:  9 Power_On_Hours          0x0032   038   038   000    Old_age   Always       -       45837
smart.2023-11-06.sdf:  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       104376
```
The youngest, sdd, is 1.6 yrs old.  The oldest, sdf, is 11.9 yrs, if you believe my data.

The least problematic answer is to backup your data and any settings you don't want to lose (keep for reference), then perform a fresh install.  Cleaning out OS cruft is a good thing.
Of course, only you know your true skill with all this stuff.  I've been doing Linux and linux administration nearly 30 yrs now and I practice what I'm suggesting.   

Fear of the unknown gets us all.  We don't know how great our backups are until we actually test them.  The way to reduce that risk is to realize that if your storage is 4+ yrs old, you can replace the OS and core storage for less than $50 to get a quality 500GB SSD, then do a fresh install onto that and keep your old HDD for reference to the more complex data and settings.  And when you are done, if you didn't have any backup storage, now you do with the older install.  Wipe it once you are 100% certain the new install has everything you need and setup a solid backup process that can actually be restored.  Having that is actually how I restore my data and settings after doing a fresh install whether it be for the same OS release or after a fresh install.

---

### Post by Dennis N on 2023-11-11
Do you get the "upgrade available" notice? What's to lose by attempting that? If it fails, plan B is do the new install, so be prepared and back up all your work files before starting. If it goes through, you save hours setting up a new install. I've done lots of upgrades using Software Updater, and I don't recall it ever failing. I never use PPAs, and my software is all from the Ubuntu repos or flathub. Flatpaks are left untouched after the process.

Note: turn off shell extensions before starting. Disable xscreensaver or screen lock if you use them. These could interrupt the process.

---

### Post by gipsyshadow on 2023-11-12
All right, I'll try 2 consecutive automatic lts system upgrades for first (crossing my fingers). If I got errors or instability I'd run a single fresh root install.
Anyway I still see "upgrade available" notice so I'm trustful about the automatic way.

 > **TheFu said:**
>  I suspect what you think is a validation of a file system isn't what Linux thinks is a file system check
I've just run fsck -f from a live usb 22.04 and I've got the following output about my home partition (sda5):
```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda5
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
Pass 1: Checking inodes, blocks, and sizes
Inode 7153 extent tree (at level 1) could be narrower.  Optimize<y>? no
Inode 134879 extent tree (at level 1) could be shorter.  Optimize<y>? no
Inode 136982 extent tree (at level 1) could be shorter.  Optimize<y>? no
Inode 155066 extent tree (at level 1) could be shorter.  Optimize<y>? no
Inode 268572 extent tree (at level 1) could be shorter.  Optimize<y>? no
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 100718/640848 files (10.8% non-contiguous), 1226445/2560000 blocks

```
What does this mean? Must I "Optimize" sda5 before resizing it and upgrading (or installing) new Ubuntu root partition?

> **TheFu said:**
> having hardware that isn't well-supported (did you have to do anything special previously to get it working?)
My main concern is about graphics: in the past Ubuntu got freezed quite often until I tried 4.18.0-25-generic kernel and it solved almost of those issues, then I tried the later kernels (5.*) but they were worse so I'm still using the 4.18. So it's important for me to know if it will be still possible to keep on using 4.18 kernel after an automatic upgrading.
After upgrading to 22.04lts and if everything will be ok then I'll try the latest stable kernel available, that I guess is 6.something but this is another story :)

> **Dennis N said:**
> turn off shell extensions before starting
How?

---

### Post by Dennis N on 2023-11-12
> How? [turn off shell extensions]

Ubuntu 18.04
Assuming you have Tweaks installed, there is a master switch at the top of the extensions dialog.
Tweaks > Extensions
See Screenshot, red arrow:

As to the kernel, you have to accept an upgrade. 4.18 is unsupported security-wise.

---

### Post by gipsyshadow on 2023-11-12
Thanks for the tip :)

> **Dennis N said:**
> As to the kernel, you have to accept an upgrade. 4.18 is unsupported security-wise. 
Really? I thought one of the best things about Ubuntu was I could have run old kernels in new releases. So is it definitely impossible to run 4.18 kernel with 20.04lts?

Anyway I've tried live 20.04 and I've got no issues, not outright...

---

### Post by Dennis N on 2023-11-12
> **gipsyshadow said:**
> Thanks for the tip :)


Really? I thought one of the best things about Ubuntu was I could have run old kernels in new releases. So is it definitely impossible to run 4.18 kernel with 20.04lts?

Anyway I've tried live 20.04 and I've got no issues, not outright...

When you install (or upgrade) to a new version, there is no option to select a kernel version to be used. Kernel 4.18 went EOL in Nov 2018, although Ubuntu would have independently maintained it as long as a supported release used it.

---

### Post by gipsyshadow on 2023-11-13
> **Dennis N said:**
> When you install (or upgrade) to a new version, there is no option to select a kernel version to be used.
Ok but at 1st new booting can I select what kernel I prefere to use from my grub list as I do right now with 18.04? Eg. Now I've got kernel 5.* in my grub list as well though I keep on choosing 4.18 at every boot.

---

### Post by TheFu on 2023-11-13
> **gipsyshadow said:**
> Ok but at 1st new booting can I select what kernel I prefere to use from my grub list as I do right now with 18.04? Eg. Now I've got kernel 5.* in my grub list as well though I keep on choosing 4.18 at every boot.

Just because something is possible, that doesn't make it a good idea.

---

### Post by Dennis N on 2023-11-13
> **gipsyshadow said:**
> Ok but at 1st new booting can I select what kernel I prefere to use from my grub list as I do right now with 18.04? Eg. Now I've got kernel 5.* in my grub list as well though I keep on choosing 4.18 at every boot.

For me, my 20.04 upgraded from 18.04 has kernels 5.4 and 4.15
The 4.15 is not being supported - last modification was in 2021 probably before the upgrade. Nevertheless, it's in the Advanced Options of the grub menu. I would not use it for security reasons.

My fresh install of 20.04 done at its initial release in April 2020, has kernel 5.4. Mine is still using it (last update Nov 7). Some users switch to a newer hwe kernel after some point release.

If you upgrade 18.04 using Software Updater now, 2 years after I did it, I can't tell you what new kernel will be installed. It could install the newer hwe kernel, since you will upgrade to the latest point release of 20.04.

P.S. - Suggest you test the upgrade with Software Updater to see if it can "calculate" the upgrade. If it can't it will tell you and exit.

---

### Post by SeijiSensei on 2023-11-13
Just make sure you back up /home to an external device like a USB stick before going forward.

---

### Post by gipsyshadow on 2023-11-13
> **Dennis N said:**
> For me, my 20.04 upgraded from 18.04 has kernels 5.4 and 4.15
P.S. - Suggest you test the upgrade with Software Updater to see if it can "calculate" the upgrade. If it can't it will tell you and exit.
I've just tried to make the very first step to see this "calculation" but I couldn't understand what you referred to. Let's refer to [this guide]("https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-upgrade-18-04-to-20-04-guide/"): 1st I clicked on upgrade and then suddenly "distribution upgrade" window appeared so I clicked on cancel as soon I could.
Is all this normal? Where's the "step" of "calculation"? Will this process automatically upgrade ONLY my root without modifying my home?
Sorry but it's my first automatic upgrade :)

---

### Post by oldfred on 2023-11-13
I do not use snaps and my install of Kubuntu is 16GB. I have seen some post snaps alone of 20GB, so make sure / is large enough.

You should have backup of /home, all data partition(s) that are not /home & any system wide settings you change in /etc. I only change grub, so make copy of that into /home so then normal backup includes it.
You can extract list of installed apps. New version may not have all the same apps, but most will be the same.
My rsync backup script file includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[https://ubuntuforums.org/showthread.php?t=1139264&p=7157175#post7157175](https://ubuntuforums.org/showthread.php?t=1139264&p=7157175#post7157175)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

Also if  you installed ppa as other sources you may want to list those. But often older ones either not maintained or not necessary.

---

### Post by TheFu on 2023-11-13
Due to snap packages, I have /var/ as a separate volume from /.  Just another option.  It is possible to move /var/ to a new volume/file system post-install and it isn't THAT hard for an intermediate-Linux admin.  I can see were a beginner would be better off either making / a little larger or creating a separate /var/ at install time, however.

---

### Post by Dennis N on 2023-11-13
> **gipsyshadow said:**
> I've just tried to make the very first step to see this "calculation" but I couldn't understand what you referred to. Let's refer to [this guide]("https://www.addictivetips.com/ubuntu-linux-tips/ubuntu-upgrade-18-04-to-20-04-guide/"): 1st I clicked on upgrade and then suddenly "distribution upgrade" window appeared so I clicked on cancel as soon I could.
Is all this normal? Where's the "step" of "calculation"? Will this process automatically upgrade ONLY my root without modifying my home?
Sorry but it's my first automatic upgrade :)

There is a description of the steps with images here:
[https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start](https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-before-you-start)
_Click on each step at the left and read about it_. I think you stopped at step #3. Let it continue, and after a bit you will see the "Do you want to upgrade?" window popup. It has "calculated" what has to be done. Click Start Upgrade to continue and finish.

Don't interrupt the process, especially when it's on "Installing the Updates".

It won't touch your home partition (or home folder) or the configuration files in it.

Let us know how it turns out.

---

### Post by gipsyshadow on 2023-11-14
> **TheFu said:**
>  Due to snap packages, I have /var/ as a separate volume from /
Wait... do you mean my new root will be the biggest ubuntu partition due to snaps? I thought home would be larger, anyway now my home is 10GB (only 5GB used) and my root is 50GB (only 20GB used). If only root will be larger due to snaps I guess 50GB will be still enough for me, consider I don't think I'll install new sw. What do you suggest to do for sizes?

---

### Post by oldfred on 2023-11-14
All data you download gets saved into /home, so generally /home is larger than / (root).
Before snaps & smaller Ubuntu, I would suggest 25 to 30GB for /, but now with snaps & snaps often saving old versions, snaps can grow a lot. 
If new user often better not to have /home as separate partition unless using a large drive. 

Every user will be a bit different on what data they have.

I use Kubuntu and remove all snaps. My / on an exteral SSD is 9GB, but my desktop will more installed is 16GB used. I now create 40 to 50GB partitions just for /. That is with no snaps.  And I have some smaller partitions for / that I have used for installs. Those test installs have little added.
I do not do games or have lots of data but have downloaded ISO each over 4GB into my data partition. I do keep /home (less than 2GB without any data) inside /, but have all data in other data partitions.

---

### Post by Dennis N on 2023-11-14
> **gipsyshadow said:**
> Wait... do you mean my new root will be the biggest ubuntu partition due to snaps? I thought home would be larger, anyway now my home is 10GB (only 5GB used) and my root is 50GB (only 20GB used). If only root will be larger due to snaps I guess 50GB will be still enough for me, consider I don't think I'll install new sw. What do you suggest to do for sizes?

If you are still planning to use Software Updater to upgrade, none of the partition sizes on your disk are going to change. The space used might slightly, but not much.

There were snaps in 18.04 too. Unless you install some snap applications, the size used by the snap system in 20.04 is less than 1.5G based on what I see.

---

### Post by TheFu on 2023-11-14
> **gipsyshadow said:**
> Wait... do you mean my new root will be the biggest ubuntu partition due to snaps? I thought home would be larger, anyway now my home is 10GB (only 5GB used) and my root is 50GB (only 20GB used). If only root will be larger due to snaps I guess 50GB will be still enough for me, consider I don't think I'll install new sw. What do you suggest to do for sizes?

See post #11 for what I actually do.

snap packages are stored in /var/snap/.  If /var is a separate volume, like I do, then it will need to be sized to hold the snaps you use.  If /var is part of /, then it will need to be sized larger to hold the snap packages. It is up to you.

It is really easy to put 1GB - 50TB+ of junk into your HOME, so the size is completely your call.  If you limit the types of files stored in your HOME - I don't put media files there at all - no music - no video - no photos - so my home is just settings, documents, and assorted other, small, junk.  I do some software development and those files are in my HOME too, but I could easily relocate them to another volume.

If you use LVM, there's no need to get the sizes exactly correct. Expanding the volume where and when needed is 5 seconds.  Didn't I say that previously?  Sorry if I didn't.  If you don't use LVM, you have to be a better guesser.  In my 3 decades as a Linux admin, I've never guessed correctly.

---

### Post by gipsyshadow on 2024-02-28
Hi all, I upgraded from 18.04lts to 20.04lts just using system automatic "advertisement" and it couldn't be easier for me because the system did all the job, I mean I didn't have to tell the system to keep my home and upgrade only my root, it knew what to do! It took just a bit of time but it was ok.

Now how to upgrade only my root from 20.04lts to 22.04lts? It'd be great if the system had the same super-automatic way to upgrade this time too but I can't find the same "advertisement" anywhere!

---

### Post by TheFu on 2024-02-28
> **gipsyshadow said:**
>  
Now how to upgrade only my root from 20.04lts to 22.04lts? It'd be great if the system had the same super-automatic way to upgrade this time too but I can't find the same "advertisement" anywhere!

As stated before, 2 LTS-to-LTS upgrades is pushing it. Anyway, do it the same way.

[LIST=1]
[*]sudo apt update
[*]sudo apt full-upgrade
[*]Backup any files you don't want to lose
[*]sudo do-release-upgrade
[*]Cross your fingers.
[/LIST]

Lots of core systems have been massively changed sine 18.04, so it will be lucky if this works.

If you skip the backup step, that seems to make it much more likely for big problems to happen.  OTOH, if you don't, then the chances seem to be less.  I'm a scientific person, but this is one area where I'm superstitious.  Make the backup.

Also, if your system has an nvidia GPU, expect issues in 22.04.  They've tried to make Wayland the default again and sometimes that fails with nVidia GPUs.  There are lots of troubleshooting threads here about nvidia and boot problems. Wouldn't hurt to read some and be prepared.  AMD and Intel iGPU support is built-in.  

I think 50G is far too large for / and wasteful.

---

### Post by gipsyshadow on 2024-02-28
I've got a (new) doubt.
I'm evaluating these 2 ways for upgrading 20.04lts -> 22.04lts:
- bootable usb with ubuntu 22.04lts in live session;
- above commands (sudo do-release-upgrade...) that TheFu told me.
Afaik those commands TheFu wrote (2^ case) will keep my sw in my root (if all will be all right), but what about the live session (1^ case)? Will that way erase my root and drive me to install all my sw from zero?

---

### Post by gipsyshadow on 2024-03-03
Up :)

---

