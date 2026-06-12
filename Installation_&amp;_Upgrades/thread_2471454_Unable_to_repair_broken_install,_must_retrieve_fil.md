---
title: "Unable to repair broken install, must retrieve files, login as user but from live USB"
date: 2022-01-31
forum: Installation &amp; Upgrades
---

### Post by couzin2000 on 2022-01-31
I just installed Ubuntu 20.04 LTS on my pc, to use it as a home server, which (in theory) will operate headless, and I will be tunneling into with Teamviewer. I've been doing this for years now on an old Compaq desktop that I was using as a home server, but it's been over used and my usages are now many more, so I need to operate on a RAID1 system.

SO - I installed Ubuntu. Everything so far has worked well. I was able to install certain software (Plex Media Server, Minecraft Bedrock server, etc), I was able to mount disks in the correct location. 

But Firefox (I usually use Chrome, but ...) just started to bug out and crash. Then it crashed some more. Then I had no choice but to reboot. 

But the system did not reboot properly.

Looks like there is some degree of corruption in the main system because I didn't know what I was doing and installed some "unattended updater" thing, which basically turned out to be a nightmare. It didnt break right away. But it certainly did break. (by now you can all tell I'm a *noob* at Linux)

I wan to reinstall, but I need to get into the PC and pull some files (that I copied over from the old server) out of my user account's /media/user folder. Which I tried to access from my Live USB stick use to install in the first place. But I remain incapable of accessing the files. Because I am not logged in as the owner of the folder, I cannot copy anything.

**How do I login as that user?**

---

### Post by MAFoElffen on 2022-01-31
You do not need to log in "as that user" to rescue/recover files from that computer... All you need is physical access to the installed system.

Does the system boot to a Grub Menu? If so, then you still have access to the Grub Boot Menu's "Advanced Options > Mount filesystem with networking (which will mount the filesystem and activate networking), then Drop to Root Prompt

If not, then get the Ubuntu Installation LiveCD that you installed from. Booting from that, you can use "Try" to access the files from the HDD., or use the instruction from Post #3 of my Graphics Resolution Sticky in my Signature Line, to mount the installed system, and chroot into it. Then you can do whatever you want to it, even try to repair, as if that system was working.

If you still have ZFS installed on it, I am the one that can talk you through mounting ZFS pools and chrooting into it to recover what you need...

---

### Post by Impavidus on 2022-01-31
You may have configured your system explicitly so, but normally /media/user is used to mount filesystems for which no mountpoint has been specified in /etc/fstab. Are your files on some additional hard drive? You can mount that directly in your live system.

---

### Post by couzin2000 on 2022-01-31
Actually the files are in my personal user files in /home/couzin2000/minecraftbe. And from the loaded Live USB, I clicked on "Try" and then sudoed into root ([FONT=Courier New]sudo -i[/FONT]), but that transformed into root@c97&$2)(1(?/ have NO idea what that was. That didnt give access into the drive, it gave me access to the Live USB instead!

So I basically reconnected my old server, Teamviewered in, connected a USB drive and was able to extract the files. 

But for the sake of finish what I started, how WOULD I get into it fro the live drive? You mentioned CHROOT... how does that work?

---

### Post by TheFu on 2022-01-31
No need to chroot and as someone new, I wouldn't suggest that, since the idea of what a chroot actually is really isn't intuitive for people mis-trained by MSFT.

The first userid on an installed Ubuntu system is 1000.
The Live Boot/Install "Try Ubuntu" userid is 999.

This means they are different users and you'll want to use sudo to copy files off before you do a fresh install.

To get everything from your HOME directory, you'll want an external drive, large enough to hold all the data, formatted as ext4 or any other Linux file system (not NTFS, exFAT or FAT32), connected to the system. Then use 
```
sudo rsync -avz /home/couzin2000 /mnt/backup/
```
That command will get everything in your HOME and retain the owner, group, permissions, ACLs and xattrs.  
Now to a fresh install on the computer if the Ubuntu OS you want, then do the reverse to put all the files back post install. Do it relatively early after the install and first reboot.
```
sudo rsync -avz  /mnt/backup/couz* /home/couzin2000
```
Notice where I put slashes and where I didn't.
If you want more output while the rsync works, add **--stats --progress** just after the **rsync**, before the -avz.
/mnt/backup/ is assumed to be where you mount that ext4 partition to hold all the backup data.

If you want a little better backup/restore process, you can get all the system settings and list of packages installed too BEFORE doing the rsync.  Let me see if I can find my post about doing that.  [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) doesn't use rsync. It uses rdiff-backup, which is a better, versioned, backup tool. It really isn't too hard.  But these all assume you are running from the real OS, not from a *Try Ubuntu* flash drive.  The real difference is that $HOME in those links won't be set to the place you need. It will be set to the 'ubuntu' userid (999) instead.

Good backups of personal data aren't hard.
Single User's HOME:
  [Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979)

# an simple, single-user, rdiff-backup script w/ 90days of
# versioned backups (if run daily):
```
 /usr/bin/rdiff-backup --exclude-special-files  $HOME /mnt/backup/
/usr/bin/rdiff-backup --remove-older-than 90d --force /mnt/backup/
```
To run this from a Try Ubuntu, you'll need to 
Step 1: install rdiff-backup,
$ sudo apt install rdiff-backup
Step 2: mount the backup partition somewhere,  /mnt/backup/ is assumed:

Step 3,4 : Run the command with sudo and change the $HOME to be the real directory location for the userid:
```
/usr/bin/sudo   /usr/bin/rdiff-backup --exclude-special-files  /home/couzin2000  /mnt/backup/
/usr/bin/sudo   /usr/bin/rdiff-backup --remove-older-than 90d --force /mnt/backup/
```

Good enough?
If you put those 2 lines into a file - called a script - then chmod +x on the filename, you can run it daily and have versioned backups for everything in your HOME directory.

To restore the last backup using rdiff-backup, use this:
```
/usr/bin/sudo   /usr/bin/rdiff-backup --restore-as-of now   /mnt/backup/couzin*  /home/couzin2000
```

Both rsync and rdiff-backup are network aware, so we can backup from 1 computer to another or 'pull' the backups from a remote computer back to our local one.  This networking makes the remote connection a little more complex, since system backups have to run as root and remote root is a huge security issue.  Probably not useful to discuss it here, beyond saying that ssh is used and normal ssh security techniques are very important for the security of the solution.

---

### Post by MAFoElffen on 2022-01-31
What that means is that you boot from the LiveCD, mounted the installed partitions of the installed system, chroot into the system using the kernel of the running LiveCD Environment. That will give you a console session into the installed system, as if it was running without the GUI.

That will give you a chance to diagnose and/or make changes to the installed system, just as if it booted and was running. How is does that, is too change the root directory, as the root directory of the mounts. That is exactly what my Ama-Gi Project Ubuntu Support LiveCD is based on and for... A LiveCD Environment for Users to be able to diagnose and repair their Installed systems. It's in the middle of being updated right now, so is not yet ready for public consumption. 

That is also how the boot-repair disk is able to make Grub changes to repair an installed system for booting problems.

---

### Post by couzin2000 on 2022-02-01
> **TheFu said:**
> No need to chroot and as someone new, I wouldn't suggest that, since the idea of what a chroot actually is really isn't intuitive for people mis-trained by MSFT. <...> and normal ssh security techniques are very important for the security of the solution.

Whew, that's  quite impressive knowledge there. Thank you for all that. I wish there was a way for me to learn faster about Linux command-line stuff... I'm still trying to figure out what [FONT=Courier New][SIZE=3]fstab[/SIZE][/FONT] is and how it works!

I'm certainly keeping all this as a reference. Thank you so much!

Perhaps you can try answering my other thread. I'd appreciate the input about that!
[https://ubuntuforums.org/showthread.php?t=2471512](https://ubuntuforums.org/showthread.php?t=2471512)

---

### Post by couzin2000 on 2022-02-01
> **MAFoElffen said:**
> What that means is that you boot from the LiveCD, mounted the installed partitions of the installed system, chroot into the system using the kernel of the running LiveCD Environment. That will give you a console session into the installed system, as if it was running without the GUI.

That will give you a chance to [COLOR="#FF0000"]**diagnose **[/COLOR]and/or make changes to the installed system, just as if it booted and was running. How is does that, is too change the root directory, as the root directory of the mounts. That is exactly what my Ama-Gi Project Ubuntu Support LiveCD is based on and for... A LiveCD Environment for Users to be able to diagnose and repair their Installed systems. It's in the middle of being updated right now, so is not yet ready for public consumption. 

That is also how the boot-repair disk is able to make Grub changes to repair an installed system for booting problems.

If I only COULD diagnose. So much happens when you follow online instructions that aren't truly appropriate for your system because you've already done a few things to it. 
The reason why my system got all messed up was because I followed some page I found about how to enter into unattended updates. Somehow the system decided to absorb updates that weren't supposed to be there, and all of a sudden, I can't boot into the system anymore. 

I am trying to make a near-zero-maintenance homeserver. I run Plex, I run a Minecraft personal server, I use Samba to shoot stuff into the server, and that is IT.  So my venture into this didn't start well. And since I have limited knowledge, I usually end up not understanding what the code output means. A lot of it is technical, so it gets really hard without a GUI.

---

### Post by TheFu on 2022-02-01
> **couzin2000 said:**
> If I only COULD diagnose. So much happens when you follow online instructions that aren't truly appropriate for your system because you've already done a few things to it. 
The reason why my system got all messed up was because I followed some page I found about how to enter into unattended updates. Somehow the system decided to absorb updates that weren't supposed to be there, and all of a sudden, I can't boot into the system anymore. 

I am trying to make a near-zero-maintenance homeserver. I run Plex, I run a Minecraft personal server, I use Samba to shoot stuff into the server, and that is IT.  So my venture into this didn't start well. And since I have limited knowledge, I usually end up not understanding what the code output means. A lot of it is technical, so it gets really hard without a GUI.

Allowing automatic updates is asking for problems, I'm sorry to say. I think everyone has been burned with a bad update over the years.  Just make it a habit for every Saturday morning to manually run the updates AND LOOK AT THE PACKAGE LISTS.  If something seems scary in the list - stop it - go look up what that package does. 99.99% of the time, it isn't bad.  But 1 bad package with incorrect dependencies every 3 yrs can make for a really bad day.  Learn to use versioned backups AND know how to restore them, so when something bad happens - which will about once every 2 yrs, randomly, you'll have the versioned backups and be able to restore to the point prior to the problem.

There's no such thing as a hands off system. Sorry.  Either you do it or you pay someone else to do it.  Payment can be $ or privacy.  Based on using Plex, I see that privacy isn't a huge concern. That's fine.  Plex is really hard on storage devices.  When I was running Plex, it broke 2 HDDs where all the plex metadata was stored just a month or so after the HDD warranty period was up. Perhaps I just got 2 bad HDDs in 3 yrs? The last replacement HDD, I bought a WD-Gold which is a data center HDD designed for extra vibration and heavy duty cycles.  So far, no issues. That model of HDD has a 5 yr warranty and I expect to get 10 yrs of life from it - if not more.  I have a few WD-Black drives in some other systems here - those have 5 yr warranties and are well passed that period. I think was was bought in 2008. No issues at all in any of the SMART data for it.

GUIs just hide the most important information and only allow about 20% of that the system can actually do. When it comes to servers, the GUI isn't your friend.
fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  I did a web search for "ubuntu fstab". 
When searching for answers, use the "ubuntu {release} {topic}" method and prefer information from webdomains with "ubuntu" in their DNS part.  Those tend to be reputable.  When someone is really new, it is hard to know when the specific version of Ubuntu matters or not, so it is best to always include the 20.04 or 22.04 in the search parameters.  For example, almost every release, samba changes some defaults and it often breaks things. MSFT is also changing their network shared storage defaults and when MSFT and SAMBA don't align their releases and their defaults to work together, we end-users have problems.  MSFT changed how they help different systems "location" network services on the LAN the last few years, so the entire "browse network" stuff seems not to work. I don't recall if it is Linux -to- Windows that gets confused or Windows -to- Linux that does. One of those directions is a pain and really needs a well-managed network for everything to "just work."  Most home users don't have a well-managed network, I'm sorry to say.

BTW, I looked at that thread yesterday and just don't have the knowledge to be helpful. 
I don't have 20.04 installed on any physical hardware either. Just inside virtual machines.
I've never used DisplayPort and don't use GUI stuff much at all. Sorry.  I use VGA video connections with a secondary HDMI to a second monitor.  I have a KVM switch that connects to 4 computers with PS2 and VGA connectors. Not really very interested in replacing that hardware, since now the newer solutions cost $300+.  As you can see, I have no relevant knowledge.

---

### Post by couzin2000 on 2022-02-01
> **TheFu said:**
> Allowing automatic updates is asking for problems, I'm sorry to say. I think everyone has been burned with a bad update over the years.  Just make it a habit for every Saturday morning to manually run the updates AND LOOK AT THE PACKAGE LISTS.  If something seems scary in the list - stop it - go look up what that package does. 99.99% of the time, it isn't bad.  But 1 bad package with incorrect dependencies every 3 yrs can make for a really bad day.  Learn to use versioned backups AND know how to restore them, so when something bad happens - which will about once every 2 yrs, randomly, you'll have the versioned backups and be able to restore to the point prior to the problem.

I learned the hard way. But I agree with the statement. I'm setting up (again) 18.04 and making sure nothing is automatic - only notifications. It's just making more sense to me now that I re-read your words... so thanks for that.

> **TheFu said:**
> There's no such thing as a hands off system. Sorry.  Either you do it or you pay someone else to do it.  Payment can be $ or privacy.  Based on using Plex, I see that privacy isn't a huge concern. That's fine.  Plex is really hard on storage devices.  When I was running Plex, it broke 2 HDDs where all the plex metadata was stored just a month or so after the HDD warranty period was up. Perhaps I just got 2 bad HDDs in 3 yrs? The last replacement HDD, I bought a WD-Gold which is a data center HDD designed for extra vibration and heavy duty cycles.  So far, no issues. That model of HDD has a 5 yr warranty and I expect to get 10 yrs of life from it - if not more.  I have a few WD-Black drives in some other systems here - those have 5 yr warranties and are well passed that period. I think was was bought in 2008. No issues at all in any of the SMART data for it.

Myself I have a Seagate Barracuda and an HGST drive in there, so far they have been reliable and have seen SOME mileage on them. And to make matters worse, I had both these drives in an outboard box connected through USB3, which was improperly vented and very dusty, which I cleaned frequently. Because of the USB3 connection, it's impossible to get S.M.A.R.T. reporting. So I'm waiting on getting my Plex up and running again to check on drive status... life expectancy especially.

> **TheFu said:**
> GUIs just hide the most important information and only allow about 20% of that the system can actually do. When it comes to servers, the GUI isn't your friend.
fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  I did a web search for "ubuntu fstab". 
When searching for answers, use the "ubuntu {release} {topic}" method and prefer information from webdomains with "ubuntu" in their DNS part.  Those tend to be reputable.  When someone is really new, it is hard to know when the specific version of Ubuntu matters or not, so it is best to always include the 20.04 or 22.04 in the search parameters.  For example, almost every release, samba changes some defaults and it often breaks things. MSFT is also changing their network shared storage defaults and when MSFT and SAMBA don't align their releases and their defaults to work together, we end-users have problems.  MSFT changed how they help different systems "location" network services on the LAN the last few years, so the entire "browse network" stuff seems not to work. I don't recall if it is Linux -to- Windows that gets confused or Windows -to- Linux that does. One of those directions is a pain and really needs a well-managed network for everything to "just work."  Most home users don't have a well-managed network, I'm sorry to say.

Yeah, THAT I'm keen on already. I usually don't go for the Reddits of this world which any 13-year-old will bombard with stupidities about gaming and hacking. 
I do have to check back on a thread I started and you answered a while back, about Samba, just to make sure everything runs smooth. I really enjoy your thorough replies, thank you for that!

> **TheFu said:**
> BTW, I looked at that thread yesterday and just don't have the knowledge to be helpful. 
I don't have 20.04 installed on any physical hardware either. Just inside virtual machines.
I've never used DisplayPort and don't use GUI stuff much at all. Sorry.  I use VGA video connections with a secondary HDMI to a second monitor.  I have a KVM switch that connects to 4 computers with PS2 and VGA connectors. Not really very interested in replacing that hardware, since now the newer solutions cost $300+.  As you can see, I have no relevant knowledge.

That's quite alright. Actually, as mentioned earlier I'm re-installing 18.04 because somehow RAID arrays are not all that well-supported on Focal. I ran into an issue on 1st install, and reinstalling the same when Grub came on all I got was a blank screen. SO - back to the tried and true. Besides, it's a 6-year old computer. I was running Beaver on a 10 year-old Compag Proliant desktopand Beaver worked. So I'll stick to 8.04 for now and we'll see what's what later. 
Than ks for your help. Truly the man. I mean... The Fu :p

---

