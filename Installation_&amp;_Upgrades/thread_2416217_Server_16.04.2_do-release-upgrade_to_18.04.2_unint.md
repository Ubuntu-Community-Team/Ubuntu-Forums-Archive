---
title: "Server 16.04.2 do-release-upgrade to 18.04.2 unintentional interrupt - how to solve"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by bob-swede on 2019-04-07
_**BACKGROUND:**_
I have an Ubuntu server 16.04.2 LTS (headless) used as webserver, OpenVPN server and Subversion server.
It is installed in an eMachine PC previously used for Windows7 and it has a 500 GB hard drive.

I always interface to it using SSH (PyTTY from my Windows 7 PC).
I regularly update it using:
```
sudo update
sudo upgrade
```
so no packages in need of upgrades are shown on the login screen.
Recently a message prompting to upgrade to 18.04.2 has appeared and today I decided to do it.
So I used
```
sudo do-release-upgrade
```
in my PuTTY terminal.

_**PROBLEM DESCRIPTION**_
But after a short while a message was shown regarding the SSH session being not recommended for an upgrade or something like that and telling me that I should be on the hardware terminal instead.
So I managed to find a monitor with VGA connector and a usb keyboard to connect to the box.
Then I started the upgrade using this setup.

Seemed to run OK for a while but then suddenly the rolling text on the screen disappeared and I was none the wiser.
I waited a few minutes and then, thinking it was all done I tried PuTTY to it and after login the greeting page came up showing that the OS was now Ubuntu 18.04.2.
It also mentioned that a _reboot was required_.

So I went ahead and issued sudo reboot in PuTTY and the box restarted.

Now text reappeared on my monitor, but it was a crash dump!
The last part of that said:
```
[FONT=Courier New][SIZE=2]not syncing: VFS:  unable to mount root fs on unknown-block(0.0)[/SIZE][/FONT]
```

Now it was also not possible to SSH to the server...

After googling I found old posts about this where I was advised to reboot and use the GRUB alternative "Advanced" command to select an older kernel to boot with.
And this worked to get off of the crash window.

In this new window I have verified that my data are still there and that the utilities I use are also there (apache2, openvpn, svn etc).
I also tested the df -h command to check the disk as described in the web pages I found.
Unfortunately this does not show a /boot mount at all as was mentioned.

But I can still access /boot using for example ls -l /boot and it shows grub and 11 more files.

_**QUESTION**_
What can I do now to rescue the server functions?
I must have interrupted the upgrade thinking it was all done when the SSH login showed the "need reboot" message.
Since I can see that the disk and it knows my login it seems like there could be a "simple" way to get the system fixed...
But how exactly?

_**EDIT**_
I have a virtual Mint 19 machine I use for software development.
To check differences I tested the df -h command on it and it returned basically the exact same as the command in the failed server.
So this is what the virtual machine looks like:
```
~/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            955M     0  955M   0% /dev
tmpfs           198M  1,3M  196M   1% /run
/dev/sda1        79G   12G   64G  16% /
tmpfs           986M     0  986M   0% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           986M     0  986M   0% /sys/fs/cgroup
tmpfs           198M   32K  197M   1% /run/user/1000
```
The same mounts and filesystems as on my problem machine (different sizes and usage percent of course), so this might not be a problem with /boot at all....

---

### Post by TheFu on 2019-04-07
1) did you make a full, know-you-can-restore, backup before beginning?  I hope so.  Changing out a release is like swapping out an engine in a car or having open heart surgery.  ALWAYS, ALWAYS, ALWAYS make a backup that you know 100% you can restore from before doing it.  PERIOD.

2) Ok, it probably isn't _that_ bad.  It might be just that grub didn't get properly updated/install and that is a relatively small fix.  But between 16.04 and 18.04, the way networking is handled was completely replaced.  I doubt your VPN will work.  Any 3rd party repositories were removed too - under /etc/apt/sources.d/ .... but those are issues to be handled after you can boot.

3) Not all systems have separate /boot partitions.  Did you have one before?  Do you remember why?  Was it EFI or LVM or something related to encryption?  I have lots of questions ... and the best way to provide clear, correct, answers is to generate lots of information about the system.  See #4 below

4) To answer all the questions, you'll need to boot from alternate media, a live CD or live-boot flash drive is what I'd use. Then install a tool called **boot-repair**.  Run it, but DO NOT HAVE IT attempt to repair anything.  At this stage it can do more harm than good. There is a button somewhere on the main screen that says to gather information. Press that and it will push the info to a URL.  Post that URL back here.  Please.

My signature has links, if you want more details.

BTW, if the system doesn't boot, ssh won't work.

---

### Post by bob-swede on 2019-04-07
Thanks for your response, I thought that I would receive an email when someone posted a reply but apparently not. So that is why it took until now for me to find this...
> **TheFu said:**
> 1) did you make a full, know-you-can-restore, backup before beginning?  I hope so.  Changing out a release is like swapping out an engine in a car or having open heart surgery.  ALWAYS, ALWAYS, ALWAYS make a backup that you know 100% you can restore from before doing it.  PERIOD.

I am not really a Linux user, I just use different Linux boxes and follow cook-book instructions to install stuff I need.
That said I have tried to find out HOW a backup can be created on Linux, but so far in vain. There are many places where you are told to back up before, but they fail to mention how... All I have found is instructions on how to use tar to collect files together, but I still don't know _which_ files to tar and so forth...
> 
2) Ok, it probably isn't _that_ bad.  It might be just that grub didn't get properly updated/install and that is a relatively small fix.  But between 16.04 and 18.04, the way networking is handled was completely replaced.  I doubt your VPN will work.  Any 3rd party repositories were removed too - under /etc/apt/sources.d/ .... but those are issues to be handled after you can boot.
I think I caused the problem (or rather either Ubuntu or my monitor) when the display went blank. That was some screensaver I believe. I have seen it after the fact when I am looking over the rubble using the alternate kernel option in GRUB to get something going. After 10 minutes of no keyboard activity the screen goes blank. I did not know that so I thought it was all done or had crashed. I waited a while for a reboot but then connected by Putty and rebooted manually, probably half way through the upgrade...
In any case now that I have a console I have verified:
A) the file system can be written
B) All of my data files that I have checked still exist
C) I have now tar-ed all of the /etc dir (where I think most configurations live) and all of the SVN repositories and some folders in my home dir.
D) I also managed to connect an 8GB USB thumb drive to the box and transfer those tgz files over to the thumb and then to my NAS.
E) Both svn and openvpn can supply a version when called with the --version argument.
F) Concerning the 3rd party repositories I have listed /etc/apt/sources.list.d/ and found two files:
openvpn-aptrepo.list
openvpn-aptrepo.list.distUpgrade
In the first file the content has been commented out due to the upgrade and in the second one it states xenial in the active line (bionic in the previous file)
> 
3) Not all systems have separate /boot partitions.  Did you have one before?  Do you remember why?  Was it EFI or LVM or something related to encryption?  I have lots of questions ... and the best way to provide clear, correct, answers is to generate lots of information about the system.  See #4 below
I don't think the /boot dir is in a separate partition. When I ls -l / then it appears as /boot and it contains a lot of files too.> 
4) To answer all the questions, you'll need to boot from alternate media, a live CD or live-boot flash drive is what I'd use. Then install a tool called **boot-repair**.  Run it, but DO NOT HAVE IT attempt to repair anything.  At this stage it can do more harm than good. There is a button somewhere on the main screen that says to gather information. Press that and it will push the info to a URL.  Post that URL back here.  Please.

My signature has links, if you want more details.

BTW, if the system doesn't boot, ssh won't work.
OK, you are talking of a live DVD with a GUI interface, right?
Since this is a server with no GUI I downloaded the **Server** 18.04.2LTS live ISO, but when I booted off of that (after burning the DVD) it offered to _install_ after defining the keyboard type, and I did not dare continue because I had not yet found out how to tar up the important files....
Could not risk formatting the drive....
I don't know what the live DVD will do but if it modifies the disk drive I could be in a worse situation than I am now, or maybe I am incorrect?

Now that you mention networking changes with 18.04.2 then I think I will be more at ease if I can just get back to 16.04.2 or whatever I had before this happened. I have a lot of networking stuff that must work, for example the customized IPTABLES used by openvpn.

Should I download the 16.04.2 ISO and use that even though it is a GUI type disk?
What happens if I install boot-repair, will it then be part of the now damaged system?

Thanks for your help!

---

### Post by bob-swede on 2019-04-07
I downloaded the **desktop** version of Ubuntu 16.04.6 and used it as the boot drive on my PC.
It took a while before it came up but then finally (after finding a way to change the keyboard to the Swedish layout so I could find the - key) I could use it to analyze my system.
I googled how to install boot-repair and used it to collect the data you requested:

Boot-repair info URL:
[URL="http://paste.ubuntu.com/p/FhfbTKMCwc/"]http://paste.ubuntu.com/p/FhfbTKMCwc/

[/URL]Would it be possible to install Ubuntu **Server** 16.04.6 on top of the existing updated version of Ubuntu 16.04.xx (I actually think xx=6 since all upgrades had been applied before I tried the dist upgrade command)?
I mean this would presumably replace all of the files used by Ubuntu 16 with their correct versions even if Ubuntu 18 upgrade had replaced them?
It would be a repair install in that case.

Otherwise, can a dual boot be created where the 16.04 is the primary one and both use the same disks so my data files can be used in place?

---

### Post by bob-swede on 2019-04-08
OK, so I was able to fix the problem using the procedure described in [this document]("https://www.ostechnix.com/how-to-fix-broken-ubuntu-os-without-reinstalling-it/")!
Before I dared go this path I backed up all of the accessible files on the system using multiple tar commands.
The resulting tgz files were placed on a USB drive I attached to the box and then they were transferred to my NAS too.

I then booted up _from the install DVD_ for Ubuntu Server 16.04.6 and selected to reinstall GRUB followed by the Rescue broken system where I started a command prompt and executed the commands described in the document linked to above:

```
$ sudo rm /var/lib/apt/lists/lock
$ sudo rm /var/lib/dpkg/lock
$ sudo rm /var/lib/dpkg/lock-frontend
$ sudo dpkg --configure -a
$ sudo apt clean
$ sudo apt update --fix-missing
$ sudo apt install -f
$ sudo dpkg --configure -a
$ sudo apt upgrade
$ sudo apt dist-upgrade
```

Since the command I used originally to go to 18.04.2
```
sudo do-release-upgrade
```
had already modified a lot this procedure did not use any file resources from the DVD (it was the 16.04.6 server DVD), instead it accepted that it was on a broken 18.04 system...

After the commands above I exited the shell and was back on the main install page where I commanded a reboot.

And lo-and-behold! It worked without any problems like those I had yesterday!!! :p

I have now checked that SVN, OpenVPN server and the Apache webserver all work as before the upgrade.

And it is running Ubuntu Server 18.04.2 now!

---

### Post by TheFu on 2019-04-08
Happy you solved it.

A few comments ... I've been managing Unix systems since about 1993, so many of these things I've learned through experience and from discussions with other long-time Unix admins of the decades.

> HOW a backup can be created on Linux, but so far in vain.
Unix/Linux is all about flexibility.  That means each admin has to choose the best method for him/her to solve any issue.  That includes backups AND restores.  I've used 10 different tools over the years and I still use some of the backup tools from the 1990s, just for non-backup reasons.  

For example, tar files are useful like ZIP files.  Would you try to backup an entire 100G+ OS using ZIP?  No.  The same applies to tar.  It is good for moving 1-2 small projects between systems over sneaker-net.  So if I needed to use a non-Linux FAT32/NTFS storage device, and didn't have network access between the systems, AND the files are smaller than 1GB in total, then I'd use tar.  I would never use tar for backups since around 2000.

rsync is another popular backup tool, but it fails on a few different levels and requires Unix file systems so the permissions, owner, and group are stored with the data.  Backups that ignore permissions, ownership and groups are almost worthless.  That is different from Windows backups.  rsync is useful when we want to mirror or update files from A --> B.  I use rsync all the time, but only for mirroring and only where that is the best solution.  Of all the inventions around computing software, rsync is in my top 5 GREATEST list.  But for backing up an OS, it has many faults.  There are better answers.

I mentioned flexibility.  That is a gift and a curse.  It means every Unix system can be a little different, customized.  My Linux servers are different from yours, so what I need to backup is different from what you need to backup.  In the last 2-3 weeks in the these forums, I've posted a few lists of areas on the file system that I backup, but that is due to the way that I perform backups.  There are many, many, different techniques for backups, each with trade-offs.  I need daily, automatic, versioned, encrypted, networked, "pulled" backups, so to accomplish that, a mix of a few different tools are necessary.  I've selected rdiff-backup, but there are pre-backup and post-backup steps necessary to get a consistent backup.  I also want zero downtime, so some storage management techniques are used to ensure backup consistency too.  All of this would be overwhelming for someone new to Linux. Alone, each step is not complex, but putting them all together for a total solution and the storage part has to be decided, correctly, during the OS install. It cannot be added on later.

In short, there are lots of topics in these forums about backups with links on how to accomplish them.  Bit-for-bit backups are useful sometimes, but require downtime almost always.  They are huge and slow, which makes them unacceptable to me.  

Duplicity/Deja Dup/Duplicati all use the same underlying backup tool. These are backups like we did in 1970 with weekly "full" backups and daily incrementals.  To restore a system to what it looked like on a Fridday, we'd need to restore Sunday (full), then 5 incremental backups. Retaining 60-180 days of backups uses 8-25x the storage of the original.  Not very efficient. OTOH, these 3 tools check off every box in the list of what you want in a backup tool, except storage efficiency.  However, I would encourage you so search for problems that people report using each BEFORE selecting any of these tools. I've seen a bunch in these forums where people report backup corruption and all their efforts have been wasted.  A backup that cannot be required it useless.

rdiff-backup doesn't check every box like duplicity does, but it is highly efficient in time, storage, and it is trivial to see that a backup isn't corrupted, since the last backup version appears just like an rsync mirror.  90% of the time you need to restore something, it is the most recent backup.  Though I have needed to restore a database in the last few weeks that was over 2 weeks old.  It was excellent to tell rdiff-backup that I wanted the DB files from 3/14/19, get them and see that everything worked perfectly.

What needs to be backed up?  That's harder to answer. Your system is different from mine.  I backup /root, /etc, /home, a list of all manually installed packages, and data that isn't in the places already listed, so that might be /opt/ or /var/www/, just depends on the server. If there are manual ufw firewall configurations, those are placed in /lib/ufw/, so that would be included.  Any DBMS?  Then you can either shutdown the DB, then backup those files or dump the DBs to text and back them up.  If you did setup LVM and left room to make snapshots, then you can freeze the file system that holds the DBs and backup the snapshot area while the DB keeps running. I also use a few commands to capture system configuration data that _might_ be useful later when restoring to completely different hardware.  That includes lists of installed rubygems, perl modules, LVM setups, RAID setups, general storage information and connected hardware.  These are all relatively tiny, take seconds to gather, so I do.   And last, I capture any crontabs that are stored in /var/spool/cron*.  I use automatic tasks all the time.

That's enough about backups.  Don't use tar.  Use a real backup tool.  Only use bit-for-bit when you are migrating systems, TODAY, not as backups.  Whatever you choose, test the restore BEFORE you need it.

Onto the next item.  16.04 server and 16.04 desktop all use the same core programs and settings.  It wasn't always this way, but that changed about a decade ago. There is no difference between the desktop kernel and the server kernel.  Some of the runtime settings are tweaked to be different, but that doesn't matter for recovery needs.  So it is completely safe to use a desktop live-boot on a server install for recovery.  Just be certain it is the same release for best effect, but whether that is critical completely depends on the fix needed.  For dealing with storage only issues or fixing config files manually, pretty much any version should work just fine.  For doing chroot and updating grub on an installed system, closer is better.  Claro? Si?

Next, ....  openvpn-aptrepo.list.distUpgrade is like commenting out the file.  The only active files in source.d/ must end in .list and the contents cannot be commented out. It is handy to have the old files there after a release upgrade so you can check which packages you previously used from a PPA to see of the new distro includes those or newer versions.  Perhaps there isn't any need for the PPA anymore.  Limiting the use of PPAs reduces risks for all sorts of things.

/boot is usually separate for LVM installs or installs with full disk encryption.  I'm unsure about UEFI installs, but I do know that /boot/efi has to be fat32, which would be a different file system and a different partition.

Thanks for the boot-repair - since I didn't see this until after you SOLVED it, I'm not looking it over.  But if you are running a live-boot from flash or optical media, anything installed is temporary, unless you setup a chroot and mount the HDD/SSD file systems inside it. This isn't automatic or accidental. There are at least 5 manual steps to accomplish it.
You can setup dual-boot, but that will require new partitions. The OS would need to be separate, so separate apache configs, separate DBs, separate php, if that is what the box does.  Different versions of different programs can easily have incompatible data structures inside the data files.  The 18.04 programs would likely modify any schema to be good, but that would likely break 16.04 access.  This applies to webapps with DBs, apache config files and personal settings if you use a GUI.

About those commands ... now way to know which were unnecessary or useful. Running both 
```
$ sudo apt upgrade
$ sudo apt dist-upgrade
```
is unnecessary.  dist-upgrade does everything that plain "upgrade" does and more.  It does no harm to run both, other than installing unneeded packages which could be remove in the dist-upgrade command.  You can check the apt-get manpage for the specifics for each of the options.  

I'm not surprised that SVN worked.  I am surprised that ovpn and apache did.  Every LTS-to-LTS migration I've done since 8.06 required manual apache changes.  You really need to read the release notes for the specific version of both openvpn and apache installed on the 18.04 box.

iptables hasn't changed to my knowledge.  I have thousands of subnet blocks in some public servers, so I use ipset to feed rules into iptables. ipset has been around a long time too, so it probably hasn't changed either.

I hope you really have a properly upgraded system.  I'm not positive, however.  But the do-release-upgrade tool probably just automates some of the manual steps that debian requires, so it most likely is fine.

---

