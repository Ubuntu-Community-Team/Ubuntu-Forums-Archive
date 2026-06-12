---
title: "Can I delete old /usr files? I think I have two...."
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by ahalin on 2010-07-21
[SIZE="2"]I have recently done a clean install of Ubuntu 10.04 [and it is all going very nicely unlike some others] on my dual boot Dell Dimension 5100.

After seeing some advice about advanced partitioning I decided to expand my partition table during the 10.04 install process from swap, / and /home (where I keep My Documents)  to swap, /, /home, /var, /tmp and /usr, all of which was achieved without problem.

I am now getting "Low Disk Space" messages on my home partition (488 MB remaining!!!) I have emptied the trash and cleaned up any obviously large but surplus files. (I did find two that concern me but they aren't HUGE and I am unsure of what they do: file-meta.db and file-index.db in /home/john/.cache/tracker/ which are 290 MB and 108 MB respectively, last modified five months ago and something to do with SQLite3.)

Anyway, am I right in saying that my new /var, /tmp and particularly /usr partitions now contain some of what was previously held on / and /home, leaving old files that can be removed? If so, what is now surplus and how do I delete it safely? I had a bit of a dig but, as the properties in Nautilus of, for example, /usr do not indicate what partition it is on, I can't safely tell what is current and what is old.

John[/SIZE]

---

### Post by ahalin on 2010-07-21
Sorry, partition table attached

---

### Post by oldfred on 2010-07-21
Advanced partitioning is really only for servers or we did it ten years ago as that was the standard since most systems were originally set up for servers. I do not recommend any extra system partitions except /home and for old system with BIOS limit /boot. You have to know what each system partition is used for and what your requirements will be.

I see your /tmp is small. If you ever want to write a DVD backup it will try to store the 4+gb of data in /tmp before writing. So you do not have enough room.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by ahalin on 2010-07-21
Thanks OldFred,

The impression I gained from reading about advanced partitioning was that just using / and /home (which is retained as you upgrade, reinstall or use different flavours of Linux (for a while there I had Windows XP and three different Linus distros, all with the same /home)) results in conflicts between applications or user setting. For example (hypothetically for a relative newbie like me), Firefox 3.0 settings from an earlier distro may conflict with Firefox 3.6 settings in Ubuntu 10.04, or the Ubuntu settings stored in /home may conflict with those of Fedora.

If this is not true please let me know.

Either way, having now created a new /usr folder on a separate partition, am I duplicating something? If so, how do I fix it? 

I dont want to reinstall Ubuntu 10.04, having just finished adding all my tweaks to it (Digikam, non-free codecs, non-standard printer driver, etc etc). Having tried lots of flavours I also think I will stick with 10.04 LTS for a good while, so wont upgrade or switch distro any time soon.

Thanks again for your time.

---

### Post by oldfred on 2010-07-22
I believe you can move any system partition just like you would move /home. I moved my /boot just by copying it and adding an entry to fstab. Then I did not want it so I copied it back and deleted the entry in fstab. 

I do not share /home but created a /data with all my data including lots of data that is in the hidden folders. All my firefox & thunderbird data is in a NTFS partition to share with windows. I also have moved gnucash & kmymoney to folders in /data. I am trying to wean myself off Quicken as that is my last windows app.

Moving /home (should be same procedure for others) Maintaining permissions & root ownership are most important for partitions other than /home
To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I was linking in my data to both my desktop & portable and then several different installs of Ubuntu so I tried to do everything on command line & copied history to a bash script to let me automatically link everything on a new install.

---

### Post by ahalin on 2010-07-26
Thanks again. I guess it would be wiser to ask these sort of questions before I got adventurous!

Anyway, I think I could do your suggested move, although I would probably put /usr, /tmp and /var BACK into /home rather than the other way around if that is possible. Maybe I'll just point Ubuntu BACK at the old folders (something I have had to do a few time for /home) then delete the separate partitions.

But my big problem remains: I think I have two sets of /usr, /tmp and /var; the old ones in /home and the new ones in their own partitions, and I am very worried about deleting or merging or whatever.

And my /home is running out of space even though I didn't change its size during my recent adventures in partitioning. Indeed /home should be less likely to fill up because I created new and separate /usr, /tmp and /var partitions 

Worst case: Reinstall Ubuntu 10.04, deleting the separate /usr, /tmp and /var partitions and pointing the distro at the existing /home partition as I go  As I said, I don't want to do this because I have just finished tweaking Ubuntu to my liking.

---

### Post by oldfred on 2010-07-26
I do not think the system uses system folders in /home.

if you run this it should show mounted partitions. Mine has a lot of data patitions but only / & /home as system partitions.

df

fred@fred-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc5            100790004   6957316  88712776   8% /
udev                   2028592       344   2028248   1% /dev
none                   2028592       272   2028320   1% /dev/shm
none                   2028592       292   2028300   1% /var/run
none                   2028592         0   2028592   0% /var/lock
none                   2028592         0   2028592   0% /lib/init/rw
/dev/sda1             57665280  36255008  21410272  63% /media/cdrive
/dev/sdc8             51174096  23343408  27830688  46% /media/gdrive
/dev/sda4             20472848  19377968   1094880  95% /media/share
/dev/sda2             76912416  44268116  28737296  61% /media/backup
/dev/sdc6            100790004  54647648  41022444  58% /usr/local/fred/data
/dev/sdc9             28588924   1337484  25799168   5% /home
/dev/sdc2            104446596  22278064  82168532  22% /home/fred/shared
/dev/sdd1              1972496    179456   1793040  10% /media/WIN7 Repair
/dev/sr0                145228    145228         0 100% /media/cdrom0
fred@fred-desktop:~$

---

### Post by ahalin on 2010-07-28
So assume /var etc should go back onto /

Here are the results. Sadly everything looks quite full except tmp and /:

john@House2ubuntu104:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda6               970584    318664    602616  35% /
none                    505572       332    505240   1% /dev
none                    512440       388    512052   1% /dev/shm
none                    512440        88    512352   1% /var/run
none                    512440         0    512440   0% /var/lock
none                    512440         0    512440   0% /lib/init/rw
/dev/sda8                93207      8323     80072  10% /tmp
/dev/sda2             31047996  26247800   3223016  90% /home
/dev/sda7               970584    774008    147272  85% /var
/dev/sda9              4270488   3690188    363368  92% /usr
john@House2ubuntu104:~$

---

### Post by oldfred on 2010-07-28
Your root does not look exactly generous. Are partitions in a location that the ones you now are not using can be added to /? If not I might just reinstall after backing up any user data. I typically recommend 10-20GB for /, 2GB or size of RAM if you want to hibernate for swap and the rest as /home. I have not paid attention to sizes for other system partitions since I installed Redhat 5 many years ago.

---

### Post by ahalin on 2010-08-12
Sorry Old Fred, I have been away.

I fixed the /var problem:

[INDENT]After hitting "analyse" on the error message (obvious isn't it!!) I could see /var/cache/apt/archives/ was full as a boot with .deb packages. So I moved them to a CD-RW. This caused a bit of a problem initially when trying to install new packages, I think because the /partial folder was missing and I guess Synaptic, Ubuntu Software Centre, apt-get, etc need it for the download/install process. So I just copied that back to /archives/ and all was well.[/INDENT]

Anyway, back to the original problem. I am buying another hard-drive and will move /home to there and enlarge / before moving /usr, /tmp and /var BACK to /. Sounds risky but I'll back it all up and learn something in the process.

On a related issue, I was right about the pitfalls of a /home that gets shared by several distributions on the same machine. It's great to have all your settings and documents there when you boot into the new distro, but it a. looks the same and b. retains some of the settings, icons and menu items of the other distros even though they are not relevant to the currently loaded system, eg I can see my Ubuntu OpenOffice icons in Xubuntu (which doesn't come with OOo). If I delete them in a rush of tidiness, they aren't there when I go back to Ubuntu!

So I tried something new this week and loaded Ubuntu 10.04 Netbook Remix on the old box I use at work. I did NOT point it at the existing /home partition where I keep all my files but let it create it's own, THEN pointed the file browser at the folders and files on the other partition (let's just call it "My Documents"). After a bit of fiddling with auto mounting that partition at boot and permissions I now have a very clean Ubuntu 10.04 but with access to all my files. This might sound a bit Mickey Mouse to you but I was very happy with myself: :KS :KS

I have just read your suggested link Painless Linux Multi-boot Setup:

[INDENT][SIZE="1"]http://blog.linuxtoday.com/blog/2009/08/painless-linux.html[/SIZE][/INDENT]

and can see that is what I have achieved but in a somewhat messy way. Hey, it's all about learning!

Re your /data partition can you select what application settings are shared in there or is it all or nothing? Your idea for Firefox settings which you want to share with all your distros and Windows is a good one.

---

### Post by oldfred on 2010-08-12
In my data partition I have separate folders for all the standard data folders from /home plus additional ones where I have added or moved data from hidden folders in /home like firefox & thunderbird profiles.

I assume you can set permissions separately, I just set permissions & ownership for everything.

I saved these links, but have not done this:

Two users to share music folder - ***** & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set ***** ID). That means any files in the directory automatically will inherit the ***** of the folder, as opposed to the ***** of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

***** File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManaging*****s.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManaging*****s.html)

Thunderbird profiles, Firefox is similar:
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

