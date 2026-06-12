---
title: "computer froze during upgrade, won't run GUI."
date: 2021-02-07
forum: Installation &amp; Upgrades
---

### Post by ruby9 on 2021-02-07
I was in the middle of upgrading from Ubuntu 16.04 (been putting it off for a while) and the upgrade froze about halfway through, freezing my entire computer.  I had to manually  reboot it and now it loads to this screen [ATTACH=CONFIG]287919[/ATTACH](sorry for the quality best my camera can do)  honestly no idea what to do, 
Any help/suggestions are highly welcome!

---

### Post by TheFu on 2021-02-07
In the last month, I've been moving my 16.04 systems to 18.04 too.  Most of the migrations have had at least 1 issue, but none were the same issue on each.
So - you'll need to create an 18.04 Live-Installer and boot into the "Try Ubuntu" part.  Then you'll need to gather some facts, since there could be all sorts of issues and guessing isn't really much of an option.

The first thing to do from the "Try Ubuntu" environment is to provide a summary of your hardware.
**inxi -Fz**   and post that output here wrapped inside 'code tags'  - [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains code tags.
Next, check the most simple things, mount the internal storage on the system and run
**df -Th** - post that with code tags too.  An upgrade needs at least 5G free on / and 150MB on /boot/ to work. 

If you ran out of storage, mid-upgrade, then you'll need to restore from the backup you made prior to starting and either try again, or just do a fresh install of 18.04 (or 20.04?).  Then restore your HOME directory.

BTW, the first image is completely worthless. Please remove that link.  To access all those error messages as text (much preferred), boot from the internal disk and let it fail.  Then boot from the "Try ubuntu" environment and pull the file from /var/log/messages on the internal storage. You'll need to mount that storage somewhere else, so it won't be /var/log/ ... it will be _......something .... /var/log/_  Find the relevant parts and show 5-10 lines above the failures, plus the entire stack from the failure.

If this all sounds too hard and you don't want to wait, just to a fresh install, then restore your data from the backups already made.  That would be the fastest way to a working computer.

---

### Post by ruby9 on 2021-02-08
Thank you, sorry I should have mentioned that my computer's pretty old and can on occasion freeze so the fault might be on my comp instead of the software install (was in a panic since I forgot to backup before trying to upgrade). I booted from the 'try ubuntu' and still see all my files and folders am backing them up now, do you know if there's a way for me to back up firefox bookmarks as well? Only have the disk for 16.04 so will try to reinstall that before trying to upgrade again. You said you've been moving your system from 16.04 to 18.04, didn't know you could do it in parts, any tips on how to do this since where I'm at the internet and power can also go out sometimes and I'd rather not go through the risk again.

---

### Post by ActionParsnip on 2021-02-08
I suggest a UPS if power is unstable

---

### Post by Impavidus on 2021-02-08
> **ruby9 said:**
>  do you know if there's a way for me to back up firefox bookmarks as well?
Your Firefox bookmarks (and the rest of your Firefox profile) is in ~/.mozilla, which is a hidden directory in your home directory. You could just backup your entire home directory, which contains all your personal documents and settings.
> Only have the disk for 16.04 so will try to reinstall that before trying to upgrade again.
That's OK, but if you have a second computer available, it may be easier if you use it to create a 20.04 live disk.
> where I'm at the internet and power can also go out sometimes and I'd rather not go through the risk again.
If your internet connection drops, it's inconvenient, but won't ruin your system. It only starts installing the upgrade after it has finished downloading all packages. A few packages may download additional data during install, but those aren't critical. Power failures are a different matter. A power failure in the middle of an upgrade (and not just a release upgrade, but also the regular ones) can lead to an unbootable system.

---

### Post by ruby9 on 2021-02-09
> Your Firefox bookmarks (and the rest of your Firefox profile) is in ~/.mozilla, which is a hidden directory in your home directory. You could just backup your entire home directory, which contains all your personal documents and settings.

Thank you, I found it but it won't let me copy the folder saying I don't have permission to copy it. I actually do want to back up the whole home dictionary but get the same message when I try to drop the folder (I'm not very good at using the terminal) to the usb drive: [ATTACH=CONFIG]287935[/ATTACH]


> If your internet connection drops, it's inconvenient, but won't ruin your system. It only starts installing the upgrade after it has finished downloading all packages. A few packages may download additional data during install, but those aren't critical. Power failures are a different matter. A power failure in the middle of an upgrade (and not just a release upgrade, but also the regular ones) can lead to an unbootable system.

Had no idea about this :shock:  just realized how lucky I've been considering how many times the powers cut out mid update.

---

### Post by Impavidus on 2021-02-09
Just use sudo. People often overuse it, but this is one of those cases it was meant for. If you want to do it the neat way, you can use rsync to copy. Best if your usb drive has a Linux filesystem, as that will keep file permissions:```
sudo  rsync  -aXS  /media/path-to-internal-drive/home/username  /media/path-to-usb-drive
```
If you have no Linux filesystem on the usb drive and want to keep permissions anyway, you can pack your files in an archive.

A power failure during an upgrade can leave the package currently being upgraded in an inconsistent state, damaging the software in that package. If the package is critical for booting, the computer may become unbootable. There are actually some safeguards to make it less likely the computer becomes unbootable.

---

### Post by TheFu on 2021-02-09
Any power spike is dangerous for computers.  Never know what can happen. Using the BSR is the least-worse method. Just yanking the power cord is the worst. I've had a computer completely friend yanking the power cord - that was long ago - so hopefully current computers have spike protection built-in to some small degree. We didn't have that 20+ yrs ago.  Of course, lightning strikes nearby are bad for all electronic devices.

+1 for using rsync to a Linux file system.  There are a few files in our HOME directories which absolutely must have correct permissions to work. The ones I know about are for ssh and ssh-related uses.  If the target storage is FAT32 or exFAT, then you'll need to use tar first so owner, group, and permissions are captured.  I don't think any other common archive tool (arj, zip, gzip, bzip, .... ) capture that critical data.  Just stuff it all into a tar archive - I'd probably compress it with gzip at the same time - and copy that file over to the USB storage.  FAT32 can only hold a 4G file or smaller, so if you have more than that, you'll need to make multiple tar.gz files.

---

### Post by ruby9 on 2021-02-10
> Best if your usb drive has a Linux filesystem, as that will keep file permissions.

> If you have no Linux filesystem on the usb drive and want to keep  permissions anyway, you can pack your files in an archive.


Sorry I'm not sure what you mean? I'm ver un tech-savvy.


> :```
sudo  rsync  -aXS  /media/path-to-internal-drive/home/username  /media/path-to-usb-drive
```


I've tried this and must be doing something wrong (I've only used the terminal to update) since it's not working this is the file name I'm trying to copy [ATTACH=CONFIG]287940[/ATTACH] this is the usb I'm trying to copy it to and my attempts: [ATTACH=CONFIG]287941[/ATTACH]

---

### Post by ruby9 on 2021-02-10
> 

+1 for using rsync to a Linux file system.  There are a few files in our HOME directories which absolutely must have correct permissions to work. The ones I know about are for ssh and ssh-related uses.  If the target storage is FAT32 or exFAT, then you'll need to use tar first so owner, group, and permissions are captured.  I don't think any other common archive tool (arj, zip, gzip, bzip, .... ) capture that critical data.  Just stuff it all into a tar archive - I'd probably compress it with gzip at the same time - and copy that file over to the USB storage.  FAT32 can only hold a 4G file or smaller, so if you have more than that, you'll need to make multiple tar.gz files.

Don't know anything about file compression,  is any .tar ok to use?

---

### Post by TheFu on 2021-02-10
> **ruby9 said:**
> Don't know anything about file compression,  is any .tar ok to use?

tar has compression options ---> tgz or tar.gz.  Most things that aren't already compressed (video, images) will compress 50-70%.  So if your HOME directory holds 6G of stuff you want to keep, then using tar WITH compression will probably result in a 3G tgz file.  That is below the amount that FAT32 supports, so you won't need to change the file system on a flash-thumb-drive to a better file system for larger file support.  Pretty much any other file system supports huge files.

It should be said that tar really shouldn't be used for more than about 500MB of data. Tar was designed when tape drives were 80MB and the format has all sorts of flaws as the total size grows.  I've seen people attempt to create tar files with 100G of data.  Crazy.  But they don't know any better, I suppose.  As the total size grows, other tools become more and more useful - with 1 trade-off.  Tar and tgz files can be accessed from almost any system without installing anything extra.  Even ZIP can't say that.

---

### Post by Impavidus on 2021-02-10
The first command in your second screenshot is almost correct. The only problem is that there's a space in the path to your usb drive. Space is used to separate arguments, so this mean that you want to copy the part before the space to the location indicated by the part after the space.

The solution is to put a backslash before the space to escape it. Or put the path in quotes.

BTW, it's easier if you copy-paste the text from your terminal to your forum post, instead of posting a screenshot. It allows me to simply copy your command and fix it.

If a large part of your data consists of pictures or videos, compression won't help, as those are already compressed. But the permissions on those media files don't really matter; in 99% of the cases the default permissions are fine. If you're interested in using tar, read the manual:```
man tar
```Most commands have a manual that can be accessed like that.

---

### Post by ruby9 on 2021-02-11
thank you.

---

### Post by ruby9 on 2021-02-11
> **Impavidus said:**
> The first command in your second screenshot is almost correct. The only problem is that there's a space in the path to your usb drive. Space is used to separate arguments, so this mean that you want to copy the part before the space to the location indicated by the part after the space.

The solution is to put a backslash before the space to escape it. Or put the path in quotes.

 thank you I used ```
sudo rsync -aXS /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home '/media/ubuntu/Elements SE'

``` but it only copied some of the files, I waited a couple of hours to make sure it wasn't still copying but a lot of the folders are completely empty. Not sure if this helps, here's some screenshots of what's turning up for me. 
[ATTACH=CONFIG]287942[/ATTACH]This is the folder I'm trying to copy and the folder that got copied to the usb [ATTACH=CONFIG]287943[/ATTACH][ATTACH=CONFIG]287944[/ATTACH]

---

### Post by TheFu on 2021-02-11
rsync has lots of options which will provide feedback as things are copied.  --stats --progress  --verbose

I don't understand the point of screen shots, sorry.  Best to post text with the **ls -al** for the source and target directories AND clearly mark which is which - AND use code tags when posting so all the columns line up.

Please.

To mirror files where both storage appears local, I use:
```
sudo  rsync  -av --stats --progress  /media/path-to-internal-drive/home  /media/path-to-usb-drive/
```
Note the options and trailing '/' characters. Those have a specific meaning in rsync.

The -X and -S are only needed if you use xattrs or sparse files. FAT32 and exFAT won't support either, so it doesn't matter if those file systems are used. Probably just get warnings, but you will get warnings with sudo since the owner, group, and permissions won't work either.

Spaces should be avoided in all directory and filenames, though the single-quotes will make that fine. Double-quotes would work too and are more flexible if you want to use script variables. That's a whole different thread.

---

### Post by ruby9 on 2021-02-12
>  
I don't understand the point of screen shots, sorry.  Best to post text with the **ls -al** for the source and target directories AND clearly mark which is which - AND use code tags when posting so all the columns line up.


Ok thanks, will start doing that for any future problems (I usually use screenshots since I'm not sure what might be important or to include).


>  
Spaces should be avoided in all directory and filenames, though the  single-quotes will make that fine. Double-quotes would work too and are  more flexible if you want to use script variables. That's a whole  different thread.

The usb had the space already in its name, not sure how to change it.

>  
To mirror files where both storage appears local, I use:
```
sudo  rsync  -av --stats --progress  /media/path-to-internal-drive/home  /media/path-to-usb-drive/
```
Note the options and trailing '/' characters. Those have a specific meaning in rsync.


Thank you! This worked and copied all the files over to the usb! Going to reinstall ubuntu now :) (fingers crossed it all goes well this time)

---

### Post by TheFu on 2021-02-12
> **ruby9 said:**
>  The usb had the space already in its name, not sure how to change it.

It is probably the LABEL. Change that for the partition. How would depend on the file system involved, I think.
I really hope the target file system is a native, Linux, file system, or the owner, group, permissions, and some other file metadata is lost. You never posted which file system the target storage had.

---

### Post by ruby9 on 2021-02-12
> **TheFu said:**
> It is probably the LABEL. Change that for the partition. How would depend on the file system involved, I think. 
I tried googleing how to do that, it looks a little too complicated for me, going to leave it since I don't want to mess anything up.
 
> I really hope the target file system is a native, Linux, file system, or the owner, group, permissions, and some other file metadata is lost. You never posted which file system the target storage had.

I'm not sure what type of file system it is, I checked under disks and it said

Partitioning: GUID Partition Table

Device: /dev/sdc1  

Partition type: Basic Data  

Contents: NTFS

Didn't end up having enough time to reinstall ubuntu last night is the storage I'm using ok?

---

### Post by TheFu on 2021-02-13
**NTFS is NOT a native Linux file system.**  

That is an MS-Windows file system and doesn't support POSIX stuff without lots of help. 

We cannot control permissions except using complex mount options which apply to all files or all directories in the file system. It is quite the hack. Most importantly, that file system is only useful for pure data. You can't put any part of the Linux OS there, no programs, no HOME directory.  Many backup tools will not work correctly using NTFS either - due to the POSIX problems.

But for pure data files, like videos, music, photos, the lack of POSIX permissions may or may not be important.  It is only important if you want to prevent access by others.

---

### Post by ruby9 on 2021-02-14
> **TheFu said:**
> **NTFS is NOT a native Linux file system.**  

That is an MS-Windows file system and doesn't support POSIX stuff without lots of help. 

We cannot control permissions except using complex mount options which apply to all files or all directories in the file system. It is quite the hack. Most importantly, that file system is only useful for pure data. You can't put any part of the Linux OS there, no programs, no HOME directory.  Many backup tools will not work correctly using NTFS either - due to the POSIX problems.

But for pure data files, like videos, music, photos, the lack of POSIX permissions may or may not be important.  It is only important if you want to prevent access by others.

Thank you, luckily I don't have any programs I can't reinstall easily. I did want to keep the bookmarks I had in my previous firefox browser, is that possible somehow? Can see the .mozilla file but it has an x on it and tells me I don't have permission to view it, used 

```
sudo xdg-open /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/.mozilla

```

am able to click on it now but can't actually run or open firefox to get the bookmarks from it.

---

### Post by TheFu on 2021-02-14
I don't know what "it has an x on it" means.  Maybe if you posted the actual permissions for the directory and files, I could help?  Use a terminal. Run commands like **ls -la** on the directories and files.  Permissions are very important on Unix systems. There's no way around learning them.

---

### Post by ruby9 on 2021-02-14
> **TheFu said:**
> I don't know what "it has an x on it" means.  Maybe if you posted the actual permissions for the directory and files, I could help?  Use a terminal. Run commands like **ls -la** on the directories and files.  Permissions are very important on Unix systems. There's no way around learning them. 

Thank you for all the help, sorry I'm not very tech-savvy so I hope I've done this right:

```
 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ ls -la
total 552
drwxr-xr-x 40 1000 1000   4096 Feb  7 03:19 .
drwxr-xr-x  4 root root   4096 Dec  4  2019 ..
drwx------  3 1000 1000   4096 Apr 25  2017 .adobe
-rw-rw-r--  1 1000 1000    101 Jan 15  2020 .apport-ignore.xml
drwxrwxr-x  4 1000 1000   4096 Oct 16 08:56 .audacity-data
-rw-------  1 1000 1000   3482 Jan 21 05:17 .bash_history
-rw-r--r--  1 1000 1000    220 Apr 23  2017 .bash_logout
-rw-r--r--  1 1000 1000   3771 Apr 23  2017 .bashrc
drwx------ 40 1000 1000   4096 Jan  6 08:37 .cache
drwx------  3 1000 1000   4096 Apr 23  2017 .compiz
drwx------ 36 1000 1000   4096 Jan 24 11:49 .config
drwx------  3 root root   4096 Jul 27  2019 .dbus
drwxr-xr-x 16 1000 1000  20480 Feb  2 05:46 Desktop
-rw-r--r--  1 1000 1000     25 Apr 23  2017 .dmrc
drwxr-xr-x  3 1000 1000   4096 Aug 12  2020 Documents
drwxr-xr-x  2 1000 1000  20480 Feb  5 09:10 Downloads
drwxrwxr-x  3 1000 1000   4096 Feb 16  2020 .eteks
drwx------  3 1000 1000   4096 Jan 27 07:59 .gconf
drwxr-xr-x 24 1000 1000   4096 Feb  4 11:56 .gimp-2.8
drwx------  3 1000 1000   4096 Oct 26 16:54 .gnome
drwx------  3 1000 1000   4096 Aug 26  2017 .gnome2
drwx------  3 1000 1000   4096 Feb  7 03:19 .gnupg
drwx------  2 1000 1000   4096 Dec 24  2018 .gphoto
drwxr-xr-x  2 1000 1000   4096 Sep  5  2017 .hplip
-rw-------  1 1000 1000 310620 Feb  7 03:19 .ICEauthority
drwxrwxr-x  4 1000 1000   4096 Apr 28  2018 .java
drwxrwxr-x  7 1000 1000   4096 Jan  6 08:40 kdenlive
drwx------  3 1000 1000   4096 Apr 23  2017 .local
drwx------  3 1000 1000   4096 Apr 25  2017 .macromedia
drwx------  5 1000 1000   4096 Nov 18  2017 .mozilla
drwxr-xr-x  2 1000 1000   4096 May  3  2020 Music
drwxr-x---  6 1000 1000   4096 Jan 15  2020 .openshot
drwxr-xr-x 27 1000 1000  12288 Feb  2 05:34 Pictures
drwx------  3 1000 1000   4096 Sep 25  2017 .pki
-rw-r--r--  1 1000 1000    655 Apr 23  2017 .profile
drwxr-xr-x  2 1000 1000   4096 Apr 23  2017 Public
-rw-------  1 1000 1000    256 Jun  9  2019 .pulse-cookie
drwxrwxr-x  5 1000 1000   4096 Nov 19  2019 .rednotebook
drwxr-xr-x 12 1000 1000   4096 Feb  1 06:18 snap
drwxrwxr-x  2 1000 1000   4096 Mar 18  2020 .steam
lrwxrwxrwx  1 1000 1000     28 Mar 18  2020 .steampath -> /home/mia/.steam/sdk32/steam
lrwxrwxrwx  1 1000 1000     26 Mar 18  2020 .steampid -> /home/mia/.steam/steam.pid
-rw-r--r--  1 1000 1000      0 Nov  9  2017 .sudo_as_admin_successful
drwxrwxr-x  9 1000 1000   4096 Sep  1  2019 synthv-editor
drwxr-xr-x  2 1000 1000   4096 Apr 23  2017 Templates
drwx------  3 1000 1000   4096 Aug 26  2017 .thumbnails
drwx------  5 1000 1000   4096 Jun  5  2020 .thunderbird
drwxr-xr-x  7 1000 1000   4096 Dec  7 07:57 Videos
drwxrwxr-x  2 1000 1000   4096 Jun  2  2020 vlc
drwxrwxr-x  3 1000 1000   4096 Nov 14  2019 .vscode
-rw-rw-r--  1 1000 1000     80 Jan 29 08:16 wholistic.com
-rw-------  1 1000 1000    186 Feb  7 03:18 .Xauthority
-rw-------  1 1000 1000     82 Feb  7 03:18 .xsession-errors
-rw-------  1 1000 1000   1210 Feb  6 15:24 .xsession-errors.old
drwx------  7 1000 1000   4096 Nov  9 06:52 .zoom
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$
```

---

### Post by TheFu on 2021-02-14
Well ..... 
```
drwx------  3 1000 1000   4096 Apr 23  2017 .local
```
Says that on the current system, the normal installation userid and group for that user doesn't exist, so it can only show the owner and group using numbers (uid/gid).
BTW, only the owner (1000) can enter that directory. That is a common permission for any dotfiles (files/directories that begin with a period).   The .mozilla/ directory has the same issue. Yep:
```
drwx------  5 1000 1000   4096 Nov 18  2017 .mozilla
```

In short, someone appears to have removed the first username from the password and group files.  That isn't good.

For someone _not very tech-savvy_ that is:
[LIST]
[*]impressive
[*]bad
[*]probably best fixed by doing a fresh install.
[/LIST]

Last time I saw something like that was in the early 1990s ... when I was a noob on the internet and someone hacked my box, deleted my account and changed the root password.

Are you running in a "Try Ubuntu" environment now?

---

### Post by Impavidus on 2021-02-14
> **TheFu said:**
> 
Are you running in a "Try Ubuntu" environment now?

Username and hostname are ubuntu, so this appears to be a live session. It's expected that there is no user 1000. At least, I think that the user is a live session has a different ID.

The easiest way of keeping your Firefox data is storing it in an archive.```
cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/
sudo tar -cf /media/your-usb-drive/firefox-profile.tar .mozilla
```
After the fresh install, you can restore your Firefox profile from the archive. Best to do this before the first time you run Firefox, or you'll get a second profile (not too hard to get rid of).```
cd
tar -xf /media/your-usb-drive/firefox-profile.tar
```With some extra options you can make it a compressed archive, but I don't see any benefit in that.

---

### Post by TheFu on 2021-02-14
> **Impavidus said:**
>  With some extra options you can make it a compressed archive, but I don't see any benefit in that.

cjf
 and
xjf
are the options for b2zip compres/decompress.  30-50% size savings.

---

### Post by ruby9 on 2021-02-15
> **TheFu said:**
> Well ..... 
```
drwx------  3 1000 1000   4096 Apr 23  2017 .local
```
Says that on the current system, the normal installation userid and group for that user doesn't exist, so it can only show the owner and group using numbers (uid/gid).
BTW, only the owner (1000) can enter that directory. That is a common permission for any dotfiles (files/directories that begin with a period).   The .mozilla/ directory has the same issue. Yep:
```
drwx------  5 1000 1000   4096 Nov 18  2017 .mozilla
```

In short, someone appears to have removed the first username from the password and group files.  That isn't good.

For someone _not very tech-savvy_ that is:
[LIST]
[*]impressive
[*]bad
[*]probably best fixed by doing a fresh install.
[/LIST]

Literally only clicked on like two buttons after software updater finished and asked if I wanted to upgrade since 18.04 was available. Upgrade and yes :(


> Last time I saw something like that was in the early 1990s ... when I was a noob on the internet and someone hacked my box, deleted my account and changed the root password.

I think electronics in general just don't like me, I've lost count of devices that suddenly freeze, glitch or break for no explanatory reason.


> Are you running in a "Try Ubuntu" environment now?

Yes I'm using try ubuntu from a disk.

---

### Post by ruby9 on 2021-02-15
> **Impavidus said:**
> 

The easiest way of keeping your Firefox data is storing it in an archive.```
cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/
sudo tar -cf /media/your-usb-drive/firefox-profile.tar .mozilla
```



I must be doing something wrong here,  remembered what you said about spaces in the name but the backslash/quote marks but still can't get it to work

```
 
ubuntu@ubuntu:~$ cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar -cf /media/Elements SE/firefox-profile.tar .mozilla
tar: SE/firefox-profile.tar: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar -cf /media/Elements\SE/firefox-profile.tar .mozilla
tar: /media/ElementsSE/firefox-profile.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar -cf '/media/Elements SE/firefox-profile.tar .mozilla'
tar: Cowardly refusing to create an empty archive
Try 'tar --help' or 'tar --usage' for more information.

```

---

### Post by Impavidus on 2021-02-15
> **TheFu said:**
>  30-50% size savings.Yes, a few tens of megabytes maybe.

> **ruby9 said:**
> I must be doing something wrong here,  remembered what you said about spaces in the name but the backslash/quote marks but still can't get it to work

Try```
sudo tar -cf /media/Elements\ SE/firefox-profile.tar .mozilla
```
or```
sudo tar -cf '/media/Elements SE/firefox-profile.tar' .mozilla
```
In your first try, you forgot to treat space specially. In your second try, you replaced the space with a backslash instead of prepending the backslash. In your third try, you correctly quoted the first space, but you quoted the next space too.

---

### Post by TheFu on 2021-02-15
When, how and what to quote can be confusing at first. There are 3 ways to handle filenames with non-standard characters.
[LIST]
[*]escape each non-standard character - "\ " (quote added only to clearly show the space)
[*]double quote the entire directory/file entry - this is handy if variables are used and need to be expanded
[*]single-quote the entire  directory/file entry - this is handy if you DO NOT want variables expanded
[/LIST]

If the directory/file entry has an apostrophe inside, then using double quotes would be easiest of the quoting methods.
eg: "/there's/a/path/here"

If the directory/file entry has double-quotes inside, then using single quotes would be easiest of the quoting methods.
eg: '/he/exclaimed/"YES!"'

Or you like like to escape, then both can be handled like this:
eg: /there\'s/a/path/here
eg: /he/exclaimed/\"YES\!\"

See how I escaped the ! too?  That's because most shells (the program) will expand that. It has special meaning which may or may not matter based on history.  The \ is the normal escape character in most Unix-like OSes.  Some commands allow using another, on-the-fly.

BTW, the last argument of the command is the input location. I'd specify it more exactly - don't assume a PWD.
```
sudo tar czf    '/media/Elements SE/firefox-profile.tgz'    ~/.mozilla
```
or 
```
sudo tar cjf    /media/Elements\ SE/firefox-profile.tar.bz   ~/.mozilla
```
or 
```
cd  /media/Elements\ SE/; sudo tar cjf  firefox-profile.tar.bz   ~/.mozilla
```

~/ is the same as $HOME.  Both expand using the password entry of the HOME directory for the current username. Very convenient.  Plus, by chdir'ing to the backup location, the tar create-compressed-file command doesn't need a path/filename, just a filename, since the PWD would be where you wanted the output.

Long ago, the tar command removed the need for a switch character, -.  When they first changed it, errors would happen if you added it. I suppose GNU tar which is what all Linuxen use, support both. Appears so.

My ~/.mozilla/  compressed file is about 300MB.  Uncompressed it is about 600MB.  j = bzip; z = gzip for compression in tar commands.  tgz is an extremely common extension, often used. Every archive tool on every platform should support it.

---

### Post by ruby9 on 2021-02-15
> **Impavidus said:**
> 
Try```
sudo tar -cf /media/Elements\ SE/firefox-profile.tar .mozilla
```
or```
sudo tar -cf '/media/Elements SE/firefox-profile.tar' .mozilla
```

It's telling me there's no such dictionary?
```

ubuntu@ubuntu:~$ cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar -cf /media/Elements\ SE/firefox-profile.tar .mozilla
tar: /media/Elements SE/firefox-profile.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar -cf '/media/Elements SE/firefox-profile.tar' .mozilla
tar: /media/Elements SE/firefox-profile.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ 

```

> 
In your first try, you forgot to treat space specially. In your second try, you replaced the space with a backslash instead of prepending the backslash. In your third try, you correctly quoted the first space, but you quoted the next space too.

Thank you for taking the time out to explain how I made the errors, was really unsure about the quotes but and didn't realise the backslash needed a space.

---

### Post by ruby9 on 2021-02-15
> **TheFu said:**
> When, how and what to quote can be confusing at first. There are 3 ways to handle filenames with non-standard characters.
[LIST]
[*]escape each non-standard character - "\ " (quote added only to clearly show the space) 
[*]double quote the entire directory/file entry - this is handy if variables are used and need to be expanded 
[*]single-quote the entire  directory/file entry - this is handy if you DO NOT want variables expanded 
[/LIST]

If the directory/file entry has an apostrophe inside, then using double quotes would be easiest of the quoting methods.
eg: "/there's/a/path/here"

If the directory/file entry has double-quotes inside, then using single quotes would be easiest of the quoting methods.
eg: '/he/exclaimed/"YES!"'

Or you like like to escape, then both can be handled like this:
eg: /there\'s/a/path/here
eg: /he/exclaimed/\"YES\!\"

See how I escaped the ! too?  That's because most shells (the program) will expand that. It has special meaning which may or may not matter based on history.  The \ is the normal escape character in most Unix-like OSes.  Some commands allow using another, on-the-fly.

Thank you for taking the time to explain how to deal with the nonstandard characters, this is really easy for me to understand.


> 
BTW, the last argument of the command is the input location. I'd specify it more exactly - don't assume a PWD.


I'm not sure what you mean of a PWD,  location/name of the file?


> 
```
sudo tar czf    '/media/Elements SE/firefox-profile.tgz'    ~/.mozilla
```
or 
```
sudo tar cjf    /media/Elements\ SE/firefox-profile.tar.bz   ~/.mozilla
```
or 
```
cd  /media/Elements\ SE/; sudo tar cjf  firefox-profile.tar.bz   ~/.mozilla
```

~/ is the same as $HOME.  Both expand using the password entry of the HOME directory for the current username. Very convenient.  Plus, by chdir'ing to the backup location, the tar create-compressed-file command doesn't need a path/filename, just a filename, since the PWD would be where you wanted the output.

Long ago, the tar command removed the need for a switch character, -.  When they first changed it, errors would happen if you added it. I suppose GNU tar which is what all Linuxen use, support both. Appears so.

My ~/.mozilla/  compressed file is about 300MB.  Uncompressed it is about 600MB.  j = bzip; z = gzip for compression in tar commands.  tgz is an extremely common extension, often used. Every archive tool on every platform should support it.

I tried these but it's coming up as not such file or dictionary?

```

ubuntu@ubuntu:~$ cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar czf    '/media/Elements SE/firefox-profile.tgz'    ~/.mozilla
tar: Removing leading `/' from member names
tar: /home/ubuntu/.mozilla: Cannot stat: No such file or directory
tar (child): /media/Elements SE/firefox-profile.tgz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ sudo tar cjf    /media/Elements\ SE/firefox-profile.tar.bz   ~/.mozilla
tar: Removing leading `/' from member names
tar: /home/ubuntu/.mozilla: Cannot stattar (child): /media/Elements SE/firefox-profile.tar.bz: Cannot open: No such file or directory
: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ cd  /media/Elements\ SE/; sudo tar cjf  firefox-profile.tar.bz   ~/.mozilla
bash: cd: /media/Elements SE/: No such file or directory
tar: Removing leading `/' from member names
tar: /home/ubuntu/.mozilla: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
ubuntu@ubuntu:/media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia$ 

```

---

### Post by Impavidus on 2021-02-16
> **ruby9 said:**
> 
I'm not sure what you mean of a PWD,  location/name of the file?
PWD = present working directory
Every process has a present working directory and your shell is no exception. It's the directory where you currently are. Relative paths are interpreted relative to the present working directory. It is displayed as the final part of your prompt (unless you changed what your prompt looks like). For example, when your prompt looks like```
ubuntu@ubuntu:~/Documents$
```your present working directory is ~/Documents.

> I tried these but it's coming up as not such file or dictionary?
A few things went wrong in your command.
- You used ~/.mozilla. However, you're using a live session, so the ~/.mozilla refers to the .mozilla directory of the user of the live session, not of your ordinary user.
- ~/.mozilla is an absolute path. tar will strip the leading / (invisible, but ~ is short for /home/username) and store the rest of the path in the archive. This is a bit of a problem when you unpack the file later, as the full path will be used during unpacking, so you only get the desired result if you unpack at the root of your filesystem and (worse) the place were you want to unpack the files is mounted at the same mountpoint as where your directory was mounted when you created the backup. It's easier to change your PWD to the directory where .mozilla is located and run tar from there using a relative path.
- There one element missing from the path to your usb drive.
We don't do this stuff every day either.

Now try to understand the commands I give below (and fix any typos I might have made):
```
cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/
sudo tar -czf '/media/ubuntu/Elements SE/firefox-profile.tgz' .mozilla
```
And to unpack when restoring your files after the fresh install (assuming your username is mia):```
cd
tar -xzf '/media/mia/Elements SE/firefox-profile.tgz'
```

---

### Post by ruby9 on 2021-02-17
> **Impavidus said:**
> PWD = present working directory
Every process has a present working directory and your shell is no exception. It's the directory where you currently are. Relative paths are interpreted relative to the present working directory. It is displayed as the final part of your prompt (unless you changed what your prompt looks like). For example, when your prompt looks like```
ubuntu@ubuntu:~/Documents$
```your present working directory is ~/Documents.

Thank you for the example, got it now.

> 
A few things went wrong in your command.
- You used ~/.mozilla. However, you're using a live session, so the ~/.mozilla refers to the .mozilla directory of the user of the live session, not of your ordinary user.
- ~/.mozilla is an absolute path. tar will strip the leading / (invisible, but ~ is short for /home/username) and store the rest of the path in the archive. This is a bit of a problem when you unpack the file later, as the full path will be used during unpacking, so you only get the desired result if you unpack at the root of your filesystem and (worse) the place were you want to unpack the files is mounted at the same mountpoint as where your directory was mounted when you created the backup. It's easier to change your PWD to the directory where .mozilla is located and run tar from there using a relative path.
- There one element missing from the path to your usb drive.
We don't do this stuff every day either.

Now try to understand the commands I give below (and fix any typos I might have made):
```
cd /media/ubuntu/247e0742-bd31-4214-8039-03d2c2c1c6ff/home/mia/
sudo tar -czf '/media/ubuntu/Elements SE/firefox-profile.tgz' .mozilla
```
And to unpack when restoring your files after the fresh install (assuming your username is mia):```
cd
tar -xzf '/media/mia/Elements SE/firefox-profile.tgz'
```



Thank you so much for this, it worked! I did a reinstall and got my bookmarks back :)
Might try upgrading at a later date though.
Thank you both so much Impavidus and TheFu for taking the time out to help me with this.

---

