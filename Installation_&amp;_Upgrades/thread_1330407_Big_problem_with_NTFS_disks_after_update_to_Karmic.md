---
title: "Big problem with NTFS disks after update to Karmic"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2009-11-18
There seems to be a big problem with Karmic regarding mounting of NTFS disks.  I think I have part of the answer, but not all of it.  Suggestions very welcome, since I haven't solved my own problem yet.

After updating to Karmic, nonprivileged users suddenly could not access any NTFS disks.  The update apparently removed an entry from file /etc/fstab, probably because that entry no longer works.  I added the following line to "fstab":
/dev/sdb1       /media/UserDisk   ntfs-3g  rw,user,noauto  0       0 .

When I tried to mount the disk by clicking in the Places menu, I got the following error message:

"Error mounting:  mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE library.  Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root.  Please see more information at http://ntfs-3g.org/support.html#unprivileged."

The NTFS-3G Web site tells how to repair the ntfs-3g driver so the "user" option will work, but cautions against a privilege escalation as a result.  They claim it's a problem with mount.

I don't know the status of this, but there seem to be a lot of threads about this.

---

### Post by VanillaMozilla on 2009-11-18
I don't claim to understand this fully.  According to [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/162863](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/162863) comment 2, the problem I described (as a result of the "user" option) should have occured in Jaunty, but my problem did not exist until I updated from Jaunty.

Could it be that there is some other way for a nonprivileged user to mount this disk?  Or is there a new bug here?

See also [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/482163](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/482163) .  There is a large number of possibly related bug reports (some are for ntfs, not ntfs-3g).

---

### Post by VanillaMozilla on 2009-11-20
FIXED!
The solution is simple but maybe easy to miss.  I installed ntfs-config, and that helped me to configure the disk to mount on startup.  That's all most users will need.

Ntfs-config added the following line to file fstab:

/dev/dsb1 /media/User\040disk ntfs-3g defaults, local=en_US.UTF-8 0 0

The syntax is:
<disk> /<mountpoint> ntfs-3g defaults 0 0
(I have omitted the "local" option).


Notes:
1. \040 (without quotes) is Linux for "space".

2. The mountpoint directory is arbitrary.  However, if it changes, that may affect applications that need to access the disk.  Often the directory name is the same as the NTFS disk name.  For some disk mounting methods this directory must already exist.

3. Because of recent software changes, I don't know how to make NTFS disks mountable by nonprivileged users.  As noted above, the "user" option no longer works in "fstab" and associated disk mount software.

---

### Post by FokkerCharlie on 2009-11-22
Hello!

I've just started seeing this problem on my Karmic setup.  However, running ntfs-config doesn't present a dialog offering devices and/or partitions, just two checkboxes- offering to enable write support for internal / external device respectively.

Any ideas?

Charlie

---

### Post by oldfred on 2009-11-22
I tried a entry with ntfs but it wanted to make every txt file executable. I ended up with this as my fstab entry and it seems to work:

UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults,rw,noexec,nosuid,locale=en_US.UTF-8,fmask=0111,dmask=0000          0  0

---

### Post by VanillaMozilla on 2009-11-22
OldFred,
Yes, I think I saw exactly the same thing.  I think the noexec option takes care of that.  Good point.

I think the defaults option covers some of the others automatically.

I'm thinking of changing the name of the mount point, though.  A space in a name is just too much to deal with, especially in Linux.


Fokker,
Just check it if that's what you want.  That's part of the dialog, I think.

---

### Post by coffeecat on 2009-11-22
> **VanillaMozilla said:**
> The syntax is:
<disk> /<mountpoint> ntfs-3g defaults 0 0
(I have omitted the "local" option).

Agreed. I have been using...

```
device     mountpoint     ntfs     defaults     0  0
```

... since Hardy in my fstab, and it works just fine - including in Karmic. You can use 'ntfs' in the third field - it still uses the ntfs-3g driver.

I found that if you use the line:

```
device     mountpoint     ntfs    defaults,nls=utf8,umask=007,gid=46    0  0
```

... that the Ubuntu installer sets up in the 'Manual' option, it works OK except if you do a drag and drop copy from your ext3/4 root partition to the mounted NTFS partition, when the date/time stamp gets changed to current. This is BAD. If you use the simpler 'defaults' line you don't get this problem - nothing short of data corruption in my view.

---

### Post by VanillaMozilla on 2009-11-22
Coffeecat, are you sure it's the ntfs-3g driver?  How can you tell?  And is there a bug report about the reset date?

I think my problem was that the update to Karmic deleted a line from fstab, and it did not keep the original file.  I'm thinking filing a bug report about that.

---

### Post by coffeecat on 2009-11-22
> **VanillaMozilla said:**
> Coffeecat, are you sure it's the ntfs-3g driver?

As sure as I can be. Three or more years ago, 'ntfs' in fstab would have invoked a read-only kernel driver - which as far as I know is now deprecated in Ubuntu. I was involved in a thread about a year or so ago, and someone in that stated that 'ntfs' is aliased to 'ntfs-3g', and that both invoke the ntfs-3g driver. Well - that was what someone said, but they seemed to know what they were talking about. All I can say is that I've tried both 'ntfs' and 'ntfs-3g' and it doesn't seem to make any difference.

> **VanillaMozilla said:**
>  And is there a bug report about the reset date?

As far as I remember I added a report to that effect to a relevant open bug, and it was ignored. Ah well - you win some and you lose some. So I've contented myself with pointing this out on threads on this forum on the rare occasions I get moved enough to do so. :wink:

Would you kindly have a go yourself with the two lines I posted? It would be good to have this independently confirmed - although it's been true of every machine I've tried it on. If you get the same I might be moved to start my own Launchpad bug report. :p

> **VanillaMozilla said:**
> I think my problem was that the update to Karmic deleted a line from fstab, and it did not keep the original file.  I'm thinking filing a bug report about that.

Possibly - I don't know. I did try a Jaunty > Karmic upgrade when Karmic first came out with an installation that had a ntfs-mounting line in fstab - my 'defaults' only one. From what I can remember the line didn't get rubbed out, but I can't be 100% sure because I replaced that 32-bit installation with a fresh 64-bit one.

---

### Post by oldfred on 2009-11-22
I just copied a file to my FAT32 and the date did not change, but when I copied a file to my NTFS partition the date did change. ouch

copy & paste with Nautius

---

### Post by VanillaMozilla on 2009-11-23
I can't duplicate the date problem.  I copied some files with the file browser from ext3 to an NTFS disk, and the date was always maintained.

I can only guess what the problem could be, although I have a hunch it could be using ntfs instead of ntfs-3g.  I could not figure out how to verify which is in use (except that fstab specifies ntfs-3g).  I can say I believe I once had some problems writing to an NTFS file system using ntfs--but I'm not really sure.  I would suggest trying ntfs-3g in fstab.  See if that solves the problem.

Thanks, Coffeecat, I'll have to try those options later.

---

### Post by coffeecat on 2009-11-23
> **VanillaMozilla said:**
> I can't duplicate the date problem.  I copied some files with the file browser from ext3 to an NTFS disk, and the date was always maintained.

I can only guess what the problem could be, although I have a hunch it could be using ntfs instead of ntfs-3g.

I've done a series of experiments with fstab. Let's make sure we are on the same wavelength. I have two ntfs partitions, sda2 and sdb1. Here are two fstab lines:

```
/dev/sda2        /media/DataA    ntfs    defaults    0 0
/dev/sdb1        /media/DataB    ntfs    defaults,nls=utf8,umask=007,gid=46    0 0
```With the two partitions mounted with these lines, if I do a drag and drop copy from my ext4 partition to sda2, the date/time is preserved. But if I do the same to sdb1, the date/time is changed to current. Apart from using '/dev/sdb1' instead of the UUID, the sdb1 line is as set up by the Ubuntu installer. Which is unfortunate.

But now it gets really interesting. If, instead of Nautilus, I use 'cp -a picture.jpg /media/DataA/' from the terminal, the file gets copied, there is no error message and the date is preserved. But if I use the same command but to /media/DataB, I get this error:

> cp: preserving times for `/media/DataB/picture.jpg': Operation not permittedThe file gets copied, but again the date is changed. I was using 'cp -a' because it's quicker than 'cp --preserve=all'. See man cp.

That's not the end of the story. :) If, instead, I mount the two partitions with:

```
/dev/sda2        /media/DataA    ntfs-3g    defaults    0 0
/dev/sdb1        /media/DataB    ntfs-3g    defaults,nls=utf8,umask=007,gid=46    0 0
```... I get...... wait for it...      :p

..... exactly the same as above. So choosing ntfs or ntfs-3g make no difference in this scenario. Which makes me think that what I was told, that 'ntfs' refers to the ntfs-3g driver, was correct.

Over to you. :wink:

---

### Post by VanillaMozilla on 2009-11-23
So the problem is one of the options.  I don't know what they're supposed to do.  I'll have to look them up later.

---

### Post by coffeecat on 2009-11-23
> **VanillaMozilla said:**
> So the problem is one of the options.  I don't know what they're supposed to do.  I'll have to look them up later.

I think the problem is not in the options per se, but one of the options is uncovering a bug. nls=utf8 is for character encoding, but I haven't yet encountered a problem leaving this out. umask=007 gives an ordinary user read, write and execute permissions, and gid=46 assigns ownership to the plugdev group, of which you'll be a member.

What's interesting is that leaving out the umask and gid options doesn't lead to any ownership or permissions problems. Because NTFS doesn't support Linux ownership and permissions, they have to be defined by the mount options. At least that's the theory, rather let down by the fact that a simple 'defaults' works fine.

It's getting to be a bit beyond me. :(

---

### Post by VanillaMozilla on 2009-11-23
I haven't verified it, but I think you're right that it is a bug.  If I were you, I'd search for bug reports and file one if necessary.

---

### Post by VanillaMozilla on 2009-11-23
Confirmed.  The problem occurs with the gid=46 option.  Sure seems like a bug to me.

---

### Post by coffeecat on 2009-11-24
> **VanillaMozilla said:**
> The problem occurs with the gid=46 option.  Sure seems like a bug to me.

I take my hat off to you. :) I was so exhausted doing all the variations I reported that I didn't have the energy to try the options one at a time.

Thanks.

---

### Post by VanillaMozilla on 2009-11-24
To test it quickly, you can dismount the disk, edit fstab, then remount with the mount -a command.

You gonna file a bug report?  If you do, be sure to write an accurate, descriptive bug summary.  There are an awful lot of vague bug reports that escape attention.

---

### Post by coffeecat on 2009-11-24
> **VanillaMozilla said:**
> To test it quickly, you can dismount the disk, edit fstab, then remount with the mount -a command.

Yes, that's what I was doing. Still took some time though, what with all those 'cp -a's. :)

> **VanillaMozilla said:**
> You gonna file a bug report?

I'm sure I added a post describing this on an existing thread, but you're right. It needs more detail - particularly concerning gid=46. I'll see if I can find my post and what that actual bug was. This might deserve a new bug report.

---

### Post by VanillaMozilla on 2009-11-24
A comment in an existing bug report will never get a bug fix.  It may prompt someone to file a bug report, or it may prompt a suggestion to file a bug report, but it won't do anything by itself.

The bug report should be brief, accurate and stick to the facts.  It should present all the relevant facts concisely but not too concisely.  Ideally, anyone should be able to see immediately that there is a bug and be able to reproduce it.  The report should state the minimum steps needed to reproduce the bug.  Make sure you select the right component so the right people will see it.

The summary is what will get the attention, so this should be simple and informative.  It should tell what the problem is (file dates reset) and the most important information about how the problem happens.  I suggest something like "File dates reset on copying to NTFS disk".  "File dates reset on copying to NTFS disk mounted with gid=46 option" might be too long to fit.

I probably don't need to tell you all that, because you seem like the concise, accurate type.  Still, I look at all the thousands of useless bug reports in Launchpad that won't even get triaged because they read more like desperate support requests.

---

### Post by VanillaMozilla on 2009-11-25
You still there, coffeecat?  Is this too much?

---

### Post by coffeecat on 2009-11-25
Still here. Been rather busy.

---

### Post by VanillaMozilla on 2009-12-01
I searched Launchpad and didn't find anything, although it would be easy to miss a bug report.

Do you want me to file a bug report?  I'd hate for this to go unreported.

---

### Post by coffeecat on 2009-12-02
> **VanillaMozilla said:**
> I searched Launchpad and didn't find anything, although it would be easy to miss a bug report.

Do you want me to file a bug report?  I'd hate for this to go unreported.


Here you go:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314860](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/314860)

As you see, completely and utterly ignored by the triagers (as far as I can see) and still unassigned. What can one do? :confused:

---

### Post by VanillaMozilla on 2009-12-02
It's filed under the wrong package, and people are not convinced that it's important enough to bother with finding the right package.  We need to find the right package, and Launchpad is VERY unhelpful about that.

There's some information here:
[https://wiki.ubuntu.com/Bugs/FindRightPackage#Find%20the%20binary%20package](https://wiki.ubuntu.com/Bugs/FindRightPackage#Find%20the%20binary%20package)
and here:
[https://wiki.ubuntu.com/Bugs/FindRightPackage#Find%20the%20source%20package](https://wiki.ubuntu.com/Bugs/FindRightPackage#Find%20the%20source%20package)
and here:
[http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)

I can also confirm the bug and add some information and explain why it's important when we locate the right package.  Let's see if we can move it along.

---

### Post by VanillaMozilla on 2009-12-02
Welcome to the world of Linux.  Bug reporting is not so simple.  Dumping data here until I figure out what to do with it.

OK, a Google search quickly found this:
[https://bugs.launchpad.net/debian/+source/libgphoto2/+bug/49906](https://bugs.launchpad.net/debian/+source/libgphoto2/+bug/49906) , especially comment 20
this:
[http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html](http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html)
[http://adventuresinswitching.blogspot.com/2008/03/why-havent-i-heard-of-ubuntu-backports.html](http://adventuresinswitching.blogspot.com/2008/03/why-havent-i-heard-of-ubuntu-backports.html)
this:
[http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html](http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html) (problem fixed in recent ntfs-3g?)
this:
[http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html](http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html)
And this may be close to the root of it:
[http://tuxera.com/forum/viewtopic.php?f=2&t=593&hilit=time+stamp&sid=38f77771938679f7047efcce57216236](http://tuxera.com/forum/viewtopic.php?f=2&t=593&hilit=time+stamp&sid=38f77771938679f7047efcce57216236) (I started a new thread on this here: [http://tuxera.com/forum/viewtopic.php?f=2&t=2405&p=7358&sid=514fc9470a945552ef9b690650267962#p7358](http://tuxera.com/forum/viewtopic.php?f=2&t=2405&p=7358&sid=514fc9470a945552ef9b690650267962#p7358) .)

Hints on package name:
[http://packages.ubuntu.com/hardy/ntfs-3g](http://packages.ubuntu.com/hardy/ntfs-3g)

---

### Post by coffeecat on 2009-12-03
Good luck with your researches. If you want to go ahead with a Launchpad bug report, please do. I'm really too busy at the moment to attend to the sort of detail that this deserves. If you do start a Lauchpad thread, post the link and I'll do a "me too" post.

By the way, I haven't had a chance to read your links in detail, but I notice one from 2008. Beware - there was an entirely unrelated bug affecting Nautilus for one particular release number of gnome - it might even have affected Hardy, but I'm going on memory here. It was worse than this ntfs-3g one. The date/time stamp was changed if you did a copy from any filesystem to any filesystem. As you can imagine, it caused quite a stir. Relevant link:

[https://bugzilla.gnome.org/show_bug.cgi?id=515777](https://bugzilla.gnome.org/show_bug.cgi?id=515777)

Not only was the bug destructive of data, but the developer in the gnome team needed to fix this had disappeared on paternity leave, and this seemed to paralyse the whole bug-fixing process upstream. :roll: Iirc there were some passionate exchanges in Launchpad and the Ubuntu devs had to issue their own patch rather than wait for the glacial speed at which the gnome lot were progressing - or rather un-progressing. It was hardly gnome's finest moment. I relied on gnome-commander or Konqueror to manage all my file operations while that debacle continued. A KDE file-manager to cope with a destructive gnome bug! Tch!

Also - two or three years ago, there was another date/time corruption issue that affected mounted FAT32 partitions depending on what mount options you were using. Sounds familiar? Anyway, my point is that this problem has a habit of rearing its ugly head - but each time it's a different bug. One needs to be vigilant if one wants to weed out the red-herrings.

Best of luck! :)

---

### Post by VanillaMozilla on 2009-12-03
The latest is that one of the ntfs-3g guys thinks it's a permission issue.  If permission affects the time stamp, there's something wrong.  Discussion here:  [http://tuxera.com/forum/viewtopic.ph...7efcce57216236](http://tuxera.com/forum/viewtopic.ph...7efcce57216236) (I started a new thread on this here: [http://tuxera.com/forum/viewtopic.ph...50267962#p7358](http://tuxera.com/forum/viewtopic.ph...50267962#p7358) .

Two other questions.
1. You said this was the line in fstab was written by the Ubuntu installer with the 'Manual' option.  Installer or updater?  And what do you mean by the manual option?  Do you remember what the option controls and when it is presented?  It's been a while since I have installed or updated, and I can't just reproduce this event casually.  ;)

2. Why should the -a switch be necessary with cp?  (Shouldn't cp ALWAYS preserve the time stamp?  And it actually does with the right mount options.)

This stuff is just way too frickin complicated.  It was a sick mind that wrote all these OS options.


EDIT:  This problem keeps coming up again?  I wonder how many time stamps I've lost on my pictures?  Arghh.

---

### Post by coffeecat on 2009-12-03
> **VanillaMozilla said:**
> 1. You said this was the line in fstab was written by the Ubuntu installer with the 'Manual' option.  Installer or updater?  And what do you mean by the manual option?  Do you remember what the option controls and when it is presented?  It's been a while since I have installed or updated, and I can't just reproduce this event casually.  ;)

The 'manual' option is the last (advanced) option at the partitioning stage of the GUI installer on the live CD - i.e. none of the guided options. I can't remember whether I've tried it with the alternate CD, but I wouldn't be surprised if the problem is there as well. With the manual option the installer presents you with all the partitions present on the hard disc(s) and asks you what you want to do with them. With all my machines I've set them up so that I have Windows (if present) on a primary partition, a shared NTFS partition on another primary partition on sda and/or occuying the whole of sdb, and then an extended containing a number of logicals. One logical is set up as a swap partition, and the others I can reformat to put whatever distro or Ubuntu version I'm installing at that moment. So, say I want to put Karmic on sda7 and the NTFS shared is sdb1, at the manual stage I tell the installer to reformat sda7 as ext4 and set the mountpoint as root; - and with sdb1, set the mounpoint as /media/data but not to reformat it. Obviously!

And **every** time I've done that since Hardy, the installer has written the fstab line I've already quoted. So I go in and edit it before any damage is done.

It's interesting that the NTFS options in [this Community howto]("https://help.ubuntu.com/community/Fstab") do not include the problematic uid=46 one.

> **VanillaMozilla said:**
> 2. Why should the -a switch be necessary with cp?  (Shouldn't cp ALWAYS preserve the time stamp?  And it actually does with the right mount options.)

Have a look at man cp:

> -a, --archive
              same as -dR --preserve=allI'm just in the habit of using -a because I've used 'cp -a' for archives, but it's the ' --preserve=all' that's important here. The cp command with no options doesn't preserve the timestamp. Try this:

```
cp ~/folder1/filename ~/folder2/
```Worrying, isn't it? Now try it with cp -a. Actually, be carefully with 'cp -a'. You get a recursive copy if there are subfolders present and you are careless with the * wildcard.

---

### Post by VanillaMozilla on 2009-12-08
OK, I think there are at least three bugs here, maybe four, of which one or two may be fixed and the other two are hopeless.

The cp man page says
> Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.
But that's not all it does.  By default it also resets the time stamp (and maybe some other attributes--who knows?).

That's two bugs right there.  First, that's a huge design error, in my opinion (the default does cause data loss, after all).  Second, there's the documentation error.  Only if you scrutinize the switches do you discover that they promise to stop beating you over the head, which they never told you they were going to do.

This is a fool's errand.  Even if Linus Torvalds tried to fix it, there would be howls of protest from people who actually prefer pain.  So I'm not going to bother with it.

The third bug is that some component or other -- probably ntfs-3g, I think -- *requires* privilege to honor the -a switch and preserve the time stamp.  This is apparently fixed in the latest version of ntfs-3g, which is available now, and will presumably make its way into Ubuntu.

A workaround is just not to use those complicated options with their complicated interactions.  The gid=46 option is what causes the problem, so it's best avoided.  That option requires root access to *not* reset the time stamp, but it doesn't restrict write access to the disk.  Go figure.  More details here:  [http://tuxera.com/forum/viewtopic.php?f=2&t=2405&p=7358](http://tuxera.com/forum/viewtopic.php?f=2&t=2405&p=7358), especially the last message.

---

### Post by coffeecat on 2009-12-09
I salute you for your dedication, but...

> **VanillaMozilla said:**
> This is a fool's errand. Even if Linus Torvalds tried to fix it, there would be howls of protest from people who actually prefer pain. So I'm not going to bother with it.

... I'm glad you've come around to my way of thinking. :wink: Now you know why I was so apparently laid-back about it.

Seriously though - there is one issue that should be attended to. However many bugs there are underlying this and whether or not they are fixable, the installer is still setting fstab options in the manual partitioning stage that cause data loss. This is unacceptable, partly because it is so easily fixed. What is interesting is that [this community documentation page]("https://help.ubuntu.com/community/Fstab") recommends this:

> **ntfs**

This example is perfect for a Windows partition.

/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0Touch of left hand and right hand? But pity about the /hda2.

Anyway, once the Alpha1 is released tomorrow I'll get myself involved in Lucid testing and one of the first things I'll look for is this. If it's still there I'll try to see if we can't get the attention of the Lucid devs somehow.

Watch this space!

---

### Post by VanillaMozilla on 2009-12-09
You knew what you were doing, didn't you?  :)  Yes, that's the fourth bug.  If it were my release, I would fix it in Karmic.  Just from experience, bugs I report are fixed either instantly or never, and it has little to do with their importance.

The problem may be solved just by updating ntfs-3g in Lucid.  Even so, I don't understand the reason for gid=46.  If that kind of security is needed, the user should at least be presented with the option.  (Actually, the interactions of those options across several components are far too complicated, so the fewer options the better, if you ask me.)

---

### Post by coffeecat on 2009-12-09
> **VanillaMozilla said:**
> If it were my release, I would fix it in Karmic.

I agree. In fact if I were the benign dictator of Ubuntu I'd fix it in Hardy, Intrepid and Jaunty too because people somewhere are still downloading those ISOs for whatever reason and are in danger of being hit by this bug. But that's not going to happen, so I'll focus what little influence I can muster on Lucid, if only because it's going to be an LTS release.

> **VanillaMozilla said:**
>   Even so, I don't understand the reason for gid=46.

There's an irony here - at least if I'm remembering the details correctly. Two or three years ago - before read/write of NTFS became routinely reliable - if you got the options wrong when mounting vfat drives, the - wait for it :roll: - date/time got changed when doing a copy. At the time (this was well pre-Hardy) when playing around with mount options, I noticed that the Ubuntu installer always added gid=46 and this seemed to solved the issue.

I wonder if there was a bit of lazy thinking and inadequate testing at the time the ntfs mount options were seemingly cast in concrete in the installer and some of the mount options were simply copied and pasted from the vfat selection.

---

### Post by VanillaMozilla on 2009-12-09
This stuff is too complicated.  There's too much interaction between all these complicated switches and multiple components.  Oh, well.

And there's one more bug that I almost forgot.  The upgrade overwrote fstab without keeping a backup.  Do you know if there's a log on this so I've got proof?  I've looked, and there are an awful lot of logs to look through (and bug reports, too, for that matter).

EDIT:  Never mind.  It must be in /var/log/dist-update/

---

### Post by VanillaMozilla on 2009-12-10
The official ntfs-3g manual is here:  [ntfs-3g-manual.]("http://www.tuxera.com/community/ntfs-3g-manual/")  There is also more explanation here:  [ownership-and-permissions]("http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/") and here:  [advanced/extended-attributes.]("http://www.tuxera.com/community/ntfs-3g-advanced/extended-attributes/")

This information appears to be more clearer than most of the Ubuntu manuals and literature.  Plus, it's up to date, the relevant fixes having been released only on Oct. 14, 2009.

---

### Post by coffeecat on 2009-12-10
Posting from a fresh install of Lucid Alpha 1 on my Acer laptop with a shared data NTFS partition on sda5. Guess what the installer did...

```
# /media/Data was on /dev/sda5 during installation
UUID=22C4BB0E2BD6BBE8 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```And, yes, the date/time still gets changed on a copy from the root ext4 partition. :sigh: Ho hum.

I'll sit on this for a few days and think about it. I'm too weary to go leaping into Launchpad at the moment. But thanks for those links. I'll have a look.

---

### Post by VanillaMozilla on 2009-12-10
Well, don't delay until you've forgotten exactly what you did.  Here's my suggestion.  Write the bug report right now.  You don't have to file it.  Just get the steps to reproduce down on paper.  You can deal with Launchpad later.  :)

I don't think there's much doubt that this is a bug.  The only question, I think, is whether it has been reported.

---

### Post by coffeecat on 2009-12-10
> **VanillaMozilla said:**
> Well, don't delay until you've forgotten exactly what you did.

I won't forget. The exact steps are engraved on my soul. :( Don't forget I've been seeing this since Hardy and because I've done several fresh installations with each release then and since, I could reproduce this with my eyes shut.

---

### Post by VanillaMozilla on 2010-01-14
How's the bug report coming?  :-)

---

