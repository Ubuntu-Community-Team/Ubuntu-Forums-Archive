---
title: "Ubuntu 21.10. Switching from ext4 to btrfs. Issues?"
date: 2022-04-08
forum: Installation &amp; Upgrades
---

### Post by Advait on 2022-04-08
[COLOR=#000000][FONT=Arial]AMD Ryzen 7 laptop. I may soon wipe out my Ubuntu 21.10 ext4 and do a fresh install of Ubuntu 21.10 btrfs. I&#8217;ve got a full Clonezilla clone of my system drive (including all my user data files). I&#8217;ve backed up all my user data to 2 different drives (one with FreeFileSync and one with Restic).[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I&#8217;m somewhat new to Linux. What should I watch out for and be aware of when making this change from ext4 to btrfs? What subtle or not-so-subtle problems could arise when I make this change?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I mainly use Ubuntu to do simple stuff; web browsing, email, documents, spreadsheets. Nothing fancy. I&#8217;m not a coder or dev or admin.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I&#8217;ve been using Ubuntu ext4 for about 9 months; been working great. Main reason I&#8217;m switching is so I can take advantage of all the snapshot goodness offered by btrfs.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Some apps I use regularly are Syncthing (sync to my Android), Cloudberry Backup (B2) and VirtualBox with guest Windows 10 for some Windows-only apps (HDSentinel and CloudBerry Explorer). I&#8217;ve backed up a .vdi and .ova file of my Windows 10 guest (I&#8217;m assuming I can import them into my new VirtualBox on the new btrfs system).[/FONT][/COLOR]

---

### Post by TheFu on 2022-04-08
Clonezilla is a disk imaging tool, so you won't be able to restore files from that into BTRFS.  Clonezilla will capture the prior file system too, ext4.
You've got to use a file-based backup method and need to ensure the method selected captures not just the data, but the owner, group, permissions, ACLs, and xattrs too.  Additionally, the backup storage will likely need to be a native Linux file system, so don't expect NTFS/FAT-whatever to work correctly.  Sure, they will get the data (within file size and filename length/character limits), but that is NOT sufficient for a backup.

Forget about any MS-Windows tools. Sorry.

If the only things you backup are in the 1 user's HOME directly, then you don't need to worry nearly as much, unless you use tools like ssh or any ssh-based tools. The ~/.ssh/ directory has some mandatory owner, and permissions which must be correct or ssh will refuse to work.

BTRFS has some issues on multi-disk systems, but for a single drive laptop, it should be fine.
You can get snapshots by using LVM2, which is a checkbox during most Ubuntu installations.  LVM2 has been enterprise ready (and used for over 20 yrs).

Some light reading on BTRFS: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)
Beware.  Also, btrfs lies to both du and df commands and any any tools based on those, so you'll need to only use the btrfs methods for determining storage available and used.

For a single disk system, btrfs should be fine. Not a bad choice.  Just don't expand it with more permanent storage without carefully understanding the liabilities that can introduce.  Data loss sucks.

---

### Post by Advait on 2022-04-08
"*Clonezilla is a disk imaging tool, so you won't be able to restore files from that into BTRFS." *I'm using Clonezilla to daily make full clones, not images. I like clones cuz they're bootable and I can easily restore it in case something goes wrong.

*"You've got to use a file-based backup method"* I'm using FreeFileSync and Restic for multiple daily backups of just my user data files. All my backup drives are ext4.

I've never used ssh tools and I don't know what ssh is.

Correct, no multi-disk systems, only my laptop.

*"Some light reading on BTRFS: [https://arstechnica.com/gadgets/2021...ed-filesystem/]("https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/")"* Hmmm... This was a bit scary. I'm not using any raid so I skipped all that. But it still seems that unresolved btrfs bugs could bite me even on my single disk laptop. That sound fair? I was definitely planning on taking system snapshots cuz I want to easily rollback if a system update creates problems. But if there's issues with btrfs snapshots, then I would be on shaky ground.

Hmmmm... Maybe I'll wait until btrfs gets some more polishing and bug fixes. Sound like a good plan?

My other option is ZFS and to hire a good Linux admin who can remote in and guide me to install and configure ZFS correctly. So I'll research if there's any problems using ZFS on my super simple setup.

Can OpenZFS be installed on top of Ubuntu ext4? By "on top of" I mean the installation would remove ext4 and replace it with ZFS?
 
 Thanks for the insights. Very helpful.

---

### Post by The Cog on 2022-04-09
I used btrfs for a year or more. I eventually gave up and went back to ext4, because btrfs was getting slower and slower - boot times were getting longer and longer. 

I've been trying Linux Mint for a week now - I think I might prefer it to my Xubuntu I've been using for some years. But anyway, just a few minutes ago I used Timeshift to restore and fix a failed attempt to tinker with my DNS settings. I read that timeshift has the brains to fix up the bootloader after a system restore too which is neat. Timeshift can be configured to make regular backups  in addition to on-demand. Seems good to me. It is NOT a substitute for periodic external backups though, and by default only backs up the system files. 

I'm not advocating using mint, but I read that timeshift is also available on Ubuntu though not installed by default. You may want to look at timeshift on Ubuntu. 
Oh, timeshift has the option to use either btrfs snapshots or rsync.

---

### Post by Advait on 2022-04-09
*"I used btrfs for a year or more. I eventually gave up and went back to  ext4, because btrfs was getting slower and slower - boot times were  getting longer and longer."*  Thanks for the info. Now I'm even more nervous about trying btrfs. I'll wait a few years and see if it improves.

I've been using TimeShift since I switched to Linux Ubuntu about 9 months ago. It's great. I've successfully used it twice to rollback from problems.

---

### Post by Advait on 2022-04-09
Thread solved. I'll stick with ext4 for now. Btrfs is immature and switching to ZFS is probably too complicated for a noob like me.

---

