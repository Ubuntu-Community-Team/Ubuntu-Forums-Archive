---
title: "Hardy -&gt; Lucid upgrade from Live CD. Questions on what survives without reinstall."
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by col48 on 2011-02-14
I have Hardy 8.04 - no Windows or other OS on the machine.

I have never done an upgrade and someone else did the original install, so I'm a total beginner in this area.  But can't afford much down time if it goes awry.

The Live CD of Lucid 10.04.1 runs OK, although oddly I can see into folders on my second internal disk using Nautilus but not my true home folder on my first despite ownership and permissions being identical.  I'm not worried about this unless someone says I should be!

1. I keep my system up to date but I guess there will be plenty of updates to do.  Putting that to one side, would I have to reinstall anything I have at the moment?  Thunderbird, gambas, VirtualBox for instance?

2. I have a backup of my home folder, but presumably the home folder is left untouched by the upgrade?

3. What about the desktop - eg icons on panels and extra panels.
Will this survive the change?

4. About how long will the upgrade take?  I realise this is machine-dependent but are we talking minutes or hours?

Sorry if these questions have been asked before, but I've tried a forum search without success.

--------------------------
Later: re "Oddly..." in 3rd para.  This was a permissions issue. (Obviously!).  See note at the end of post #27.  You can't believe all you read on the forum even if I wrote it!

---

### Post by grahammechanical on 2011-02-14
Hi

First, Nautilus on the live CD should be showing both discs. The one with the 8.04 installation might be labeled as File System with an icon of a hard disc. Click on it and you should see a home folder. I am using 10.10. I cannot remember what 10.04 looks like. Sorry.

Second, you need to distinguish between an upgrade and re-install. If you install from the Live CD of 10.04 then you will lose everything in the home folder and all your installed programs. Especially if you tick the partition to be formatted. Unless your friend set up the home folder on its own partition. I do not think that this was done.

I am glad that you are taking control of your Ubuntu installation. Think about creating a partition for your home folder but for doing it in six months time. After you have gained some experience.

You can upgrade using the Update Manager program in the Administration menu. You will have to go in stages from 8.04 to 8.10 to 9.04 to 9.10 to 10.04 to 10.10 and then in a fews weeks to 11.04. I think that I am correct about this. Update Manager should right now be giving you an option to upgrade to 8.10. Does it? Upgrading this way should protect your home folder and your installed programs but you may have conflicts because those programs have also been updated in the last three years. I would suggest un-installing them and then re-installing. You are going to gain lots of experience.

How fast is your Internet connection? Let us hope that you do not live in one of those parts of England where BT cannot supply a telephone line that will accept broadband speeds. I live in London. My ISP is Plusnet in Yorkshire. I find the upgrades quite fast (minutes). I would not attempt an upgrade with dial up. Install from the CD if you are on dial up. I speak from experience.

Regards.

---

### Post by psusi on 2011-02-14
You can't upgrade using the livecd; you can only format and install the new version.

---

### Post by col48 on 2011-02-15
Thanks psusi and grahammechanical.

I did not know that the CD only offered a 'clean' install.  I think my first try would be upgrade via Synaptic [update manager].  This is offering me upgrade direct from 8.04 to 10.04 (both being LTS).

The broadband just under 1Mbps in practice.  The 10.04 CD took about 90 min to download about 683Mb.

There is almost nothing installed which did not come via Synaptic, so I guess that post-upgrade this will offer to update the programs as well.  I presume there should be no problem with drivers, or with running the programs even before updating them?

---

### Post by col48 on 2011-02-17
Given that download of live CD took just over 90min, how long is upgrade likely to take?

If it gets interrupted - power cut etc - can you start again?

---

### Post by col48 on 2011-02-19
Anyone got any idea?

---

### Post by psusi on 2011-02-19
Yes, you can start again.

---

### Post by col48 on 2011-02-20
Thanks psusi.

As you can see, I am very cautious when risking the functionality of the machine.

---

### Post by oldfred on 2011-02-20
I upgraded for years every 6 months, but have converted to clean installs.

You should have a good backup of /home. If you have manually configured any system related things, backup /etc but do not reinstall as many settings may change.

You can also backup a list of installed apps.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade


Even though upgrade should work without issue, you have the files required to do a new install, as a backup, without a lot of manually trying to reconfigure system.

---

### Post by kansasnoob on 2011-02-20
The good thing is you have until April to figure out what to do, so take your time :)

Since you've already run the Live CD you have some idea what the changes look like, but I'd absolutely browse the release notes:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Upgrading](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Upgrading)

It would also be interesting to see the output of these two commands so we could see what your current setup is like:

```
sudo fdisk -l
```

```
df -H
```

BTW that's a lower case L at the end of the first one, and intentionally a capital H at the end of the second. Please use code tags to post the output. That will show your partition layout and how much free space each used partition has.

My philosophy regarding distro upgrades is "always be prepared for the worst" just in case something goes very badly wrong, so having a re-installation plan is a good idea.

---

### Post by col48 on 2011-02-20
Output of fdisk...
```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfdaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2249

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```


and of df -H
```

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              487G    31G   432G   7% /
varrun                 1.8G   123k   1.8G   1% /var/run
varlock                1.8G      0   1.8G   0% /var/lock
udev                   1.8G    62k   1.8G   1% /dev
devshm                 1.8G    13k   1.8G   1% /dev/shm
lrm                    1.8G    41M   1.7G   3% /lib/modules/2.6.24-28-generic/volatile
gvfs-fuse-daemon       487G    31G   432G   7% /home/col48/.gvfs

```

There's plenty of free space: sdb is used almost entirely for hot backups.

---

### Post by kansasnoob on 2011-02-20
> **col48 said:**
> Output of fdisk...
```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfdaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2249

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```


and of df -H
```

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              487G    31G   432G   7% /
varrun                 1.8G   123k   1.8G   1% /var/run
varlock                1.8G      0   1.8G   0% /var/lock
udev                   1.8G    62k   1.8G   1% /dev
devshm                 1.8G    13k   1.8G   1% /dev/shm
lrm                    1.8G    41M   1.7G   3% /lib/modules/2.6.24-28-generic/volatile
gvfs-fuse-daemon       487G    31G   432G   7% /home/col48/.gvfs

```

There's plenty of free space: sdb is used almost entirely for hot backups.

I'm tired ATM but you'd be doing me a favor if you'd wait a bit for me to explain how to "dual/multi-boot" in the case of a failed upgrade :)

It really is something I've wanted to do for some time, but I'm nursing a very sick dog so it could take a while.

---

### Post by col48 on 2011-02-21
kansasnoob

Sorry about the dog.

Dual boot would have to be with the existing 8.04 as I have no Windows license later than W95 - which does not understand USB!

PS:  April is solid with other things.... I have in mind doing it w/b 28 Feb.

---

### Post by kansasnoob on 2011-02-21
> **col48 said:**
> kansasnoob

Sorry about the dog.

Dual boot would have to be with the existing 8.04 as I have no Windows license later than W95 - which does not understand USB!

PS:  April is solid with other things.... I have in mind doing it w/b 28 Feb.

No Windows is needed. I multi-boot a lot performing various iso and upgrade testing:

[ATTACH]184025[/ATTACH]

Of course that's major overkill but with over 400GB of free space it would be simple to install 10.04 "alongside" 8.04 in a new partition. That way you could easily copy parts and pieces of 8.04's /home to the new install at your leisure.

I have some errands to run this AM but I'll hopefully be able to provide some more detailed instructions by the end of the day. One thing, 10.04 is now bumped to 10.04.2 so you'd have less updates to install if you began with 10.04.2 rather than 10.04.1, if that matters to you.

Do you still have the 10.04.1 iso saved on your machine? If so we could use zsync to update the iso in a fraction of the time it would take for a full download :)

---

### Post by col48 on 2011-02-21
I realise no Windows would be needed, but most cases on the forums seem to have a version of Windows in one or more partitions and I wanted to make it clear that is not a factor for me.  Often the interaction seems to cause problems!

I have no experience with partitions, although I understand the concept.

I've still got the iso on disk as well as on CD.  Are you talking of updating the iso from 10.04.1 to 10.04.2 before doing the upgrade, and then using that to do it rather than the broadband?  Sounds like a good plan to me.  Based on one statistic an upgrade over the wire could take at least 8 hours.  The elves who polish the phone lines round here need reinforcements!

I've looked at some of your other posts on forums so I reckon my needs should be very straightforward for you.

Side issue: I'm slightly puzzled that booting the live CD, I can't see inside my usual home folder - as if I don't have permission - even though I can see everything on my second drive which has the same permissions set.  Don't comment on this if it is irrelevant to the upgrade and would need investigation.

---

### Post by kansasnoob on 2011-02-21
> I realise no Windows would be needed, but most cases on the forums seem to have a version of Windows in one or more partitions and I wanted to make it clear that is not a factor for me. Often the interaction seems to cause problems!

Most of the problems we see regarding dual-boots with Windows are the result of operator error, certainly not all, especially regarding the new ubiquity (aka: live-installer) in Maverick/10.10 which I made some notes about here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

**[COLOR="Red"]But none of that applies to you ATM[/COLOR]** since you're using Lucid. BTW I applaud your choice, IMHO Maverick provided few improvements over Lucid although both Lucid and Maverick run well on my hardware.

In my personal experience the two biggest "glitches" with Lucid dist-upgrades are the "grub thing":

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

NOTE: If you decide to perform the upgrade you definitely want to "install the package maintainers version" :) You may have to tweak a few things afterward if you've edited the menu.lst but that's preferable to not being able to boot.

And problems with Xserver/Xorg which boil down to specific graphics chips. If you want to check for known problems regarding your GPU please post the output of:

```
lspci | grep VGA
```

But I just performed 10.04.2 upgrade testing and it went off very well for me (I'm Lance there):

[http://iso.qa.ubuntu.com/qatracker/result/5008/46](http://iso.qa.ubuntu.com/qatracker/result/5008/46)

So I think there's a very good chance of an upgrade working for you, but **[COLOR="Red"]time[/COLOR]** is an issue, actually time and the reliability of your connection. You mentioned in post #5:

> Given that download of live CD took just over 90min, how long is upgrade likely to take?

Well, I can usually download an Ubuntu Live CD in about 18 to 20 minutes, but downloading the needed packages for a dist-upgrade typically takes about 30 minutes. I don't know why. A full dist-upgrade generally takes at least an hour and a half.

If you care to parse the attached log you'll see that I began my Hardy to Lucid upgrade:

> 2011-02-14 10:50:21,794 INFO Using config files '['./DistUpgrade.cfg.hardy']'

And it completed:

> 2011-02-14 12:56:18,074 DEBUG enabling apt cron job

[ATTACH]184050[/ATTACH]

So that's a bit over two hours. Given the fact that I can DL a full live CD in 20 minutes and it takes you 90 minutes, if 1/3 of that time is downloading I think you could be looking at as much as three hours of just downloading, and interrupted dist-upgrades can be difficult to deal with.

Anyway, the major benefit to dual/multi-booting is that if the new OS has problems you can still boot into the old OS to get your work done. Worst case scenario the new grub may not let you boot but the old grub can always be put back in charge temporarily, but I'll not go down that road right now because it's very doubtful that will happen.

Regardless, I'll next show you how to use zsync to upgrade your .iso. You will need to burn a new disc but since 10.04.2 was just officially released on the 17th there will be very few updates to install so I think it's worth the price of a CD.

Also, just so you know, I'm not doing this just for you. I'm working on a couple of other projects. One I already mentioned, regarding the 10.10 live-installer, and I need some screenshots of the 10.04 installation process so I can be prepared to argue with the design team.

The other is kind of "wonky":

[http://ubuntuforums.org/showthread.php?t=1676235](http://ubuntuforums.org/showthread.php?t=1676235)

Basically I need to do some more testing related to that with an installed Hardy because the server version of Hardy is still supported until April 2013.

So, in the long run, you're doing me a favor by letting me combine three tasks into one. I just need a little time to do it right so I can take screenshots, make notes, etc :)

---

### Post by kansasnoob on 2011-02-21
> Side issue: I'm slightly puzzled that booting the live CD, I can't see inside my usual home folder - as if I don't have permission - even though I can see everything on my second drive which has the same permissions set. Don't comment on this if it is irrelevant to the upgrade and would need investigation.

This is a quick one for me because I'm equally confused. I brought something similar up several times, just one example:

[http://ubuntuforums.org/showthread.php?t=1401995](http://ubuntuforums.org/showthread.php?t=1401995)

I do think that the Live CD should at least be able to "read" the files on all drives (with the possible exception of XFS) but I'm still a bit "dumb" when it comes to that.

What I'm going to show you is how to "copy" things from your old OS to a newly installed OS. One thing is to use the same username and password for the new install :)

It'll take a while because I need to install two operating systems and take screenshots while doing the second install so thanks for being patient.

---

### Post by kansasnoob on 2011-02-21
In order to explain the zsync thing I need to know where you have 10.04.1 saved on your OS. Maybe in /home or Desktop?

It's well worth the tiny bit of time it'll take to learn this trick :)

I'm going to begin my test installs right now but I'll be back.

---

### Post by oldfred on 2011-02-21
Once you get zsync set up it is real easy. I saved a copy of the commands in a file, but I usually am running it often enough that I can just scroll up in my history on the terminal and find it. I have created a folder in /home called ISO where all my ISO downloads go. I did that because I do not back up that folder. This is for my update to Natty. Yours will have to be for the version and location you want.

From /home I change to folder with ISO file and run command:
```

 290  cd ISO
  291  zsync http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64.iso.zsync

```

---

### Post by col48 on 2011-02-21
@kansasnoob
ref post 16
I don't think I've done anything knowingly to menu.lst.
It appears to have loads of comment lines plus
```

default		0
timeout		3
hiddenmenu

```
..... and then this at the bottom
```

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-28-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-25-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-25-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-25-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4bea4053-53d8-4620-9230-c02706c0aa0c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Output from lspci....
```

01:08.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

```

My disks are all ext3 - just so you know; it shouldn't make any difference.  Immediately before I do any upgrade activity I must remember to do a backup of /home.  I put this here to remind myself, not you - I'm retired, too!

I think Lucid will use Grub2 and Hardy Grub.

I'd take a different view on what the Live CD should be able to do: I don't think it should be able to see anything on my disks unless I supply my password, either for it to pretend to be me or to assume root privileges.  But it should at least be consistent.  Anyway, that's a digression.

I'm happy that my needs coincide with what you want to do right now; it means I can be much more confident of a smoother transition, and I might even be better prepared for the next LTS.  By the way, I have a granddaughter staying for a few days from Wed so will not be able to respond as quickly then (but maybe you don't think this is quickly!). 

ref post 17
At the moment the 10.04.1 iso is at 
```

/home/col48/AllMine/Technical/2011-02-14-ubuntu-10.04.1-desktop-i386.iso

```
I'm happy to move it wherever is most convenient.

---

### Post by kansasnoob on 2011-02-22
Sorry to take so horribly long. I got sidetracked a few times with unrelated issues. Like I somewhat wasted several hours trying to sort out what appeared to be a brasero bug in Maverick and then found out it was due to a conflict with gthumb. I guess no time is truly wasted but I certainly accomplished nothing other than learning of the conflict :(

Anyway, one thing at a time. Regarding your GPU I Googled "Radeon 9200 PRO ubuntu lucid" and the first thing to pop up was this:

[http://ubuntuforums.org/showthread.php?t=1558258](http://ubuntuforums.org/showthread.php?t=1558258)

Hardly helpful because it's marked solved but with no comment. Rather than list a bunch of my search results I'd suggest you do the same. The only thing I see in the release notes regarding ATI is this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Window%20corruption%20with%20older%20ATI%20graphics%20cards](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Window%20corruption%20with%20older%20ATI%20graphics%20cards)

Regardless that's one of the main reasons I prefer a dual/multi-boot. If a new OS gives me some trouble I needn't fiddle around past the point of frustration. I can just boot into the old OS and go back to sorting out the new one at my leisure.

About the zsync thing, I'm not that smart, and I'm also visually impaired, so I try to keep things "dumbed down" for my own sake :D 

First install the package "zsync" using your preferred method.

I see you have the 10.04.1 iso in:

> AllMine/Technical/2011-02-14-ubuntu-10.04.1-desktop-i386.iso

But I'm foggy as to your method of file/folder management so the simplest way to do this is to copy the old iso (2011-02-14-ubuntu-10.04.1-desktop-i386.iso) to your home folder and then rename it to match the new iso as listed here:

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

ie: 

```
ubuntu-10.04.2-desktop-i386.iso
```

The name MUST match that of the file you're downloading EXACTLY! Then look for the link on that page, **[COLOR="Red"]ubuntu-10.04.2-desktop-i386.iso.zsync[/COLOR]**, right click the link and select "Copy Link Location", then open the terminal and type:

```
zsync
```

Hit the space bar and then right click again and select paste. Things should look like this:

```
lance@lance-desktop:~$ zsync http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso.zsync
#################### 100.0% 275.3 kBps DONE     

reading seed file ubuntu-10.04.2-desktop-i386.iso: *********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read ubuntu-10.04.2-desktop-i386.iso. Target 68.9% complete.      
downloading from http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso:
#################### 100.0% 570.5 kBps DONE      

verifying download...checksum matches OK
used 496021504 local, fetched 224689483

```

If the existing file is named improperly you'd see this:

[ATTACH]184147[/ATTACH]

In that case just hit Ctrl + C to kill the process and recheck the file name ;)

I did get Hardy installed and I'll soon be back with more instructions regarding partitioning, installing, etc.

Do let me know if anything I've posted so far is confusing, and thanks for being patient.

---

### Post by kansasnoob on 2011-02-22
Brief note, while performing the repartitioning I remembered you saying this:

> My disks are all ext3 - just so you know; it shouldn't make any difference.

I'm still using ext3 for anything important due to this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance%20regressions%20with%20ext4%20under%20certain%20workloads](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance%20regressions%20with%20ext4%20under%20certain%20workloads)

Therefore I still use ext3 for anything of importance! I experienced a minor loss of data when I first played with ext4 and I'm now holding out for btrfs :)

I prefer stability to a few milliseconds of speed. I'm the slowest part of my computer anyway.

---

### Post by col48 on 2011-02-22
kansasnoob

Certainly agree with your comment about stability.

Issues with Video had not occurred to me.  It seemed OK with 15 minutes fiddling on the live CD.  Hardy only offers me 2 resolutions but the Lucid Live CD offered about 10 and 4 of the 5 I tried worked.

I move files around with drag/drop in Nautilus - no chance of a typo.  I have a large number of folders which are logically named (well, it works for me).

So far, so good.  

zsync has completed (35 min to download) and reports checksum is OK.

---

### Post by kansasnoob on 2011-02-23
Sorry for the long delay again, I guess I have too many irons in the fire. Anyway the next thing to do is look at partitioning and installation options but first of all I want to be sure you understand Ubuntu's device designations. Looking back at post #11 I can see that fdisk -l shows this:

```
Disk **[COLOR="Red"]/dev/sda: 500.1 GB[/COLOR]**, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfdaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59572   478512058+  83  Linux
/dev/sda2           59573       60801     9871942+   5  Extended
/dev/sda5           59573       60801     9871911   82  Linux swap / Solaris

Disk **[COLOR="Red"]/dev/sdb: 500.1 GB[/COLOR]**, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2249

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
```

Clearly both drives are 500GB, but sda has three partitions (one of which is just an extended partition which amounts to a "shell" that can contain many logical partitions), and sdb has only one partition. It's important to know what each device "looks like" so you know for sure that you're partitioning the correct device.

Regarding device designations, eg: /dev/sda1, the "/" marks are simply "dividers", dev = device, sd = hard drive, and the first character (letter) following "sd" indicates the drive number, so:

/dev/sda = drive #1
/dev/sdb = drive #2, etc. 

The character (number) following that letter indicates the partition number so: 

/dev/sda1 = drive #1 partition #1 
/dev/sda2 = drive #1 partition #2
/dev/sdb1 = drive #2 partition #1, etc.

Clear as mud so far? It's just a good idea to have a clear mental picture of what your drives should look like :)

NOTE: If /dev/sdb (the drive with only one partition that you use for "hot backups") is a USB drive it might be simplest to disconnect it, but that's not necessary.

**IMPORTANT NOTE: In most of the examples I'm providing I used my /dev/sdb which is an 80GB internal drive, so take into consideration that the drive designation is different than yours and partition sizes are "in scale".**

So, onto using Gparted. First rule: if anything seems the least bit confusing, STOP and ask questions! If you boot your new Lucid Live CD choosing "Try Ubuntu", once you get the live desktop running go to System > Administration > Gparted (aka: Partition Editor). If you want to learn a lot about Gparted you could check their own documentation:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Or this is a great, and somewhat more simplified, guide (particularly the "real life examples" section):

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

But for what you're doing lets keep it basic. You first just want to look and make sure things look like you expect them to. In the upper right hand corner you'll notice that you can "toggle" to select each device. I'd expect your /dev/sda to look similar to this (remember, in MY example it's sdb):

[ATTACH]184268[/ATTACH]

If so the next step is to right-click on YOUR /dev/sda1 and select Resize/Move as shown here:

[ATTACH]184269[/ATTACH]

Then simply "hover" the mouse pointer over the right end of that partition diagram (the pointer will turn to a double-ended arrow) and drag the right-end to the left as far as you choose, similar this:

[ATTACH]184270[/ATTACH]

Then click on the green arrow/Apply, to apply the resize. I'd expect that to take anywhere from 15 to 45 minutes to complete depending on your machines specs. When complete you should see something similar to this:

[ATTACH]184271[/ATTACH]

Now, you could quit here and use the "Use largest continuous free space" option from the Lucid live-installer, but that will by default create an ext4 file system and it will also create a second SWAP partition which is not harmful but totally unnecessary.

I prefer creating my own new partition and then using the "Specify partitions manually (advanced)" option. It's really not that "advanced" and IMHO it's well worth learning.

Due to the 5 screenshot limit per post I'll have to continue with that in the next post :D

**Remember, if any of this is confusing just ask** :D

---

### Post by kansasnoob on 2011-02-23
> **col48 said:**
> kansasnoob

Certainly agree with your comment about stability.

Issues with Video had not occurred to me.  It seemed OK with 15 minutes fiddling on the live CD.  Hardy only offers me 2 resolutions but the Lucid Live CD offered about 10 and 4 of the 5 I tried worked.

I move files around with drag/drop in Nautilus - no chance of a typo.  I have a large number of folders which are logically named (well, it works for me).

So far, so good.  

zsync has completed (35 min to download) and reports checksum is OK.

If not for "drag-n-drop" and "copy-n-paste" I'd long ago have been in the loony bin :lolflag:

I tend to look for the simplest way to do things.

Once Lucid is installed in a dual-boot with Hardy we won't quite use "drag-n-drop" but it's almost as simple. It's certainly all GUI, no CLI needed :)

---

### Post by kansasnoob on 2011-02-23
OK, if you got through post #24 alright and ended up with the desired amount of free space then we could move forward creating a new partition and installing Lucid. You'll actually wonder why anyone considers it advanced when we're done.

Once again we're booted into the Lucid live desktop (just in case you've rebooted since then to get some work done) and we're in Gparted.

At this point you'd only need to right-click on the newly created free space (aka: unallocated space) and select "New", then "Add". You can then just accept the defaults (even though it'll be ext2) because we'll deal with that during installation. And once again you'll need to click on the green arrow/Apply to apply the change. This one goes fast, maybe a minute or two. If all went as planned you'll see a screen similar to this:

[ATTACH]184284[/ATTACH]

**Reminder**: I'm using only a representative drive!

Now, at this point it's very important to make a note of the designation of the newly created partition! I'm **guessing** that it'll be /dev/sda3 :confused: I must depend on YOU understanding the importance of identifying and selecting the proper device during installation!

The installation process is fairly simple and I think the first three screens are self explanatory:

[ATTACH]184285[/ATTACH]

The next requires a choice, and after choosing "Specify partitions manually (advanced)" you'll see a screen where you need to select the proper device:

[ATTACH]184286[/ATTACH]

After selecting the proper device click on "Change" and you'll see this:

[ATTACH]184287[/ATTACH]

That presents four choices:
(1) New partition size
(2) Use as
(3) Format the partition
(4) Mount point

Well, we already created the partition size using Gparted so no change is needed there.

The "Use as" is where you select the file-system. I'd recommend ext3, but ext4 may be fine. I already commented on that.

Obviously this is going to be a new root partition so we must check the box next to "Format the partition".

And the "mount point" must be set to "**/**"!

Once you're satisfied that you've completed those four fields properly just click on OK. Again I think the rest is self-explanatory:

[ATTACH]184290[/ATTACH]

If any of this is even slightly confusing please ask questions!

It's break time here :)

Edit: Something I wished I remembered to mention:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#I/O%20error%20after%20CD%20is%20ejected%20at%20end%20of%20install)

> I/O error after CD is ejected at end of install

In some cases, ejecting the CD at the end of installation will leave errors on the screen such as:

end_request: I/O error, dev sr0, sector 437628

these error messages indicate that the system is still trying to access some files on the CD, and are harmless except that they obscure the message asking the user to press Enter to reboot. You can safely remove the CD from the tray and press Enter at this point to reboot to your new Ubuntu system.

So when the installation is complete and you select restart, if the screen is filled with I/O errors just ignore it, remove the CD, close the tray, and press Enter. It's purely an aesthetic problem.

---

### Post by col48 on 2011-02-23
Kansasnoob

I've read post #24 and I reckon I understand it.  Your instructions are very clear - a bit simpler than I need, but I am content with that.  A couple of questions or three while I am backing up /home to an external device....

1. Would it make sense to create another new partition (at the same time) for /home, to be shared between the two OS?  I've seen this recommended elsewhere, but only to simplify backups and to isolate the user data from the system on a single Ubuntu system.  I think it could simplify matters or it could complicate them.  What do you think?

2. I don't really understand why I have sda2 and sda5 - I've just accepted it as a fact of life; someone else installed Hardy in the first place and this is how it ended up.  In Windows days the swap file was just a file like any other.  Also, whatever happened to sda3 and sda4?  Symptoms of prior failed attempts at partitioning?

3. I assume I will end up with a Hardy system which will treat everything in the Lucid partition(s) as data alongside a Lucid system which will treat everything in the Hardy partition(s) as data.  Both would see the second internal hard disk (sdb) as data.  Of course, the computer will not be running Hardy and Lucid simultaneously; this is a choice made on boot-up.

As it's already 21:30 here I won't get to partitioning tonight; I may have time tomorrow - it depends on what the granddaughter wants to do!

But I will copy the Lucid 10.04.2 iso to CD.  It looks like that's appropriate!

Now copied (burned) CD and checked it works as a Live CD.  Also SOLVED the side issue (lack of access to normal home folder from live CD).  Turns out to be permissions problem - the folder's had been set to 700 so user 'ubuntu' from on the Live CD could not read it.

---

### Post by kansasnoob on 2011-02-24
> Your instructions are very clear - a bit simpler than I need

Hopefully I'm writing this so anyone can understand it, remember I said I'm not doing it just for you. That way I can bookmark this and refer others to it so I can type less in the future :)

> 1. Would it make sense to create another new partition (at the same time) for /home, to be shared between the two OS? I've seen this recommended elsewhere, but only to simplify backups and to isolate the user data from the system on a single Ubuntu system. I think it could simplify matters or it could complicate them. What do you think?


I generally don't recommend sharing a /home because it contains so many desktop related settings that conflicts tend to result. I used to use a separate /home with each installation but I've now grown away from that.

> 2. I don't really understand why I have sda2 and sda5 - I've just accepted it as a fact of life; someone else installed Hardy in the first place and this is how it ended up. In Windows days the swap file was just a file like any other. Also, whatever happened to sda3 and sda4? Symptoms of prior failed attempts at partitioning?

Generally there's a 4 primary partition limit, but using an extended partition allows the use of many more logical partitions within the extended partition. So primary and extended partitions will generally always be 1,2,3, and 4. And logical partitions will begin with 5 even if less than 4 primary/extended partitions exist.

In fact you'll notice that I created another primary partition for the new Lucid and it ended up being sdb3 (will likely be sda3 for you). Now, I could have recommended first resizing/shrinking sda1, then resizing/growing sda2 (the extended partition), and then creating a new logical partition within it for Lucid. In that case the new logical partition would likely be sda6.

Ubuntu can use a SWAP file rather than a SWAP partition, but I've only done so once on a Netbook with a tiny SSD drive.

> 3. I assume I will end up with a Hardy system which will treat everything in the Lucid partition(s) as data alongside a Lucid system which will treat everything in the Hardy partition(s) as data. Both would see the second internal hard disk (sdb) as data. Of course, the computer will not be running Hardy and Lucid simultaneously; this is a choice made on boot-up.

After reviewing my last post (I was getting pretty tired so I need to check for errors) I'm going to type up something simple about copying files/folders from your Hardy to your new Lucid, but you seem to have a fairly good idea what to look for. Right now I'm in Maverick but this is what my Places > Removable Media looks like:

[ATTACH]184358[/ATTACH]

Since my new Hardy and Lucid partitions are very nearly the same size they both show up as 38GB Filesystem. You'll notice that most of my partitions are "labeled". That's easily done using Gparted following installation. Just right click on the proper device/partition and select Label. Then you can name it whatever you like for easy identification :)

---

### Post by col48 on 2011-02-24
Thanks for your patience and your willingness to answer questions.

> I generally don't recommend sharing a /home 

I see the sense in what you say.

Thanks for your explanation of sda1-2-5.  Most interesting.

Another digression - please ignore it if you're busy ...
I know that defrag is not needed in Linux - (or is it the filesystem which has that attribute?) but as I understand it to create a new partition in Windows you would first have to defrag the partition to be shrunk in order to gather the files together and create the empty space for the new partition.  How does Linux avoid fragmentation?


[FONT="Arial Black"][SIZE="3"]Progress Report.
[/SIZE][/FONT]
Gparted took 30 min to shrink sda1.
As you guessed, the new partition is sda3.
I've labelled sda1 as PHardy and sda3 as PLucid.  They are the same size and as I guess the file structure will be very similar at first glance it seemed prudent to give them both names at the outset.

Now for the installation.

At the moment it is a mystery to me how Lucid will acquire Thunderbird and Firefox capability when only Hardy has access to the Internet.  And whether emails received under one OS would be visible to the other without (at least) switching folders.  No doubt all will become apparent in due course!

---

### Post by psusi on 2011-02-24
> **col48 said:**
> 
Another digression - please ignore it if you're busy ...
I know that defrag is not needed in Linux - (or is it the filesystem which has that attribute?) but as I understand it to create a new partition in Windows you would first have to defrag the partition to be shrunk in order to gather the files together and create the empty space for the new partition.  How does Linux avoid fragmentation?


It is an attribute of how the kernel uses the filesystem.  There are a number of techniques that the ext[234] filesystem driver uses to minimize fragmentation.  One is simply not to start a new file at a block where the following block ( or several ) is already allocated to another file and therefore, this file would have to be fragmented to grow.  Another is to reserve a number of blocks for room to grow and not let other files be put there.  A new one added to ext4 is called delayed allocation.  Rather than allocate blocks to hold the file as data is written into the cache, it delays the allocation until the cache is flushed to disk, at which point often the whole file has already been written and so its full size is known and contiguous space large enough to hold it can be allocated.

---

### Post by col48 on 2011-02-24
Thanks psusi.  It's all very clever - and (as is true of all the cleverest ideas) obvious with hindsight.

**Kansasnoob:**

Thank you first of all for all your guidance so far.  I would not have had the confidence to attempt it unaided.  I feel we're (I/m) nearly there now.  I hope some of my questions on this thread will help others on the same quest.

The Firefox question is answered: This is from the Lucid OS.

So, should I now use 

```
List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

```
from post #9 by oldfred to get back the old set of applications, or will that upset what has been loaded by default?  [I did the first dpkg before we embarked on the whole process]

---

### Post by kansasnoob on 2011-02-24
> **col48 said:**
> Thanks for your patience and your willingness to answer questions.


I see the sense in what you say.

Thanks for your explanation of sda1-2-5.  Most interesting.

Another digression - please ignore it if you're busy ...
I know that defrag is not needed in Linux - (or is it the filesystem which has that attribute?) but as I understand it to create a new partition in Windows you would first have to defrag the partition to be shrunk in order to gather the files together and create the empty space for the new partition.  How does Linux avoid fragmentation?


[FONT="Arial Black"][SIZE="3"]Progress Report.
[/SIZE][/FONT]
Gparted took 30 min to shrink sda1.
As you guessed, the new partition is sda3.
I've labelled sda1 as PHardy and sda3 as PLucid.  They are the same size and as I guess the file structure will be very similar at first glance it seemed prudent to give them both names at the outset.

Now for the installation.

At the moment it is a mystery to me how Lucid will acquire Thunderbird and Firefox capability when only Hardy has access to the Internet.  And whether emails received under one OS would be visible to the other without (at least) switching folders.  No doubt all will become apparent in due course!

It looks like it'll be late tonight or early tomorrow before I can explain how to safely copy files/folders from the old OS to the new OS. One thing I will say now is you must be booted into the new OS when you do so! If you're booted into the old OS and copy it's files to the new OS the programs that "auto-run" will be broken!

I don't use thunderbird so you'd be doing me a favor if you'd boot into your installed Hardy and posted the output of:

```
ls -a
```

```
ls ~/.mozilla
```

Adding: Never "move" files/folders but rather "copy" them so the original stays put!
And:

---

### Post by kansasnoob on 2011-02-24
> **col48 said:**
> Thanks psusi.  It's all very clever - and (as is true of all the cleverest ideas) obvious with hindsight.

**Kansasnoob:**

Thank you first of all for all your guidance so far.  I would not have had the confidence to attempt it unaided.  I feel we're (I/m) nearly there now.  I hope some of my questions on this thread will help others on the same quest.

The Firefox question is answered: This is from the Lucid OS.

So, should I now use 

```
List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

```
from post #9 by oldfred to get back the old set of applications, or will that upset what has been loaded by default?  [I did the first dpkg before we embarked on the whole process]

I don't know :confused:

Package dependencies change from version to version and I don't do it like that, but oldfred is very dependable. He's helped me many times.

I absolutely must get some other stuff done but I will be back ASAP, sadly that'll be several hours :(

---

### Post by col48 on 2011-02-24
ref post #32

ls -a
```
.		.gnome2_private       .nvidia-settings-rc
..		.gnupg		      .odbc.ini
.adobe		.gstreamer-0.10       .openoffice.org2
AllMine		.gtk-bookmarks	      PDF
Backup details	.gtk-bookmarks~       .pdfedit
.bash_history	.gtk-custom-papers    Photos
.bash_logout	.gvfs		      Pictures etc
.bashrc		.hardinfo	      .profile
.cache		.hplip		      .pulse
Carver		.ICEauthority	      .pulse-cookie
.config		.icons		      .qt
.cups		.inkscape	      .recently-used
.dbus		.isomaster	      .recently-used.xbel
Desktop		.java		      .sane
.dmrc		.kchmviewer	      .ssh
download	.kde		      .sudo_as_admin_successful
.emacs		.lesshst	      .themes
.emacs.d	.local		      .thumbnails
.esd_auth	.macromedia	      ubuntu-10.04.2-desktop-i386.iso
.evolution	.mcop		      ubuntu-10.04.2-desktop-i386.iso.zs-old
Examples	.mcoprc		      .update-manager-core
.fontconfig	.metacity	      .update-notifier
fromOldPC	.mozilla	      .VirtualBox
.gconf		.mozilla-thunderbird  .wapi
.gconfd		.mysqlgui	      .wine
.gimp-2.4	.mysql_history	      .wvdial.conf
.gksu.lock	.mysqlnavigator.rc    .Xauthority
.gnome2		.nautilus	      .xsession-errors

```
and
ls ~/.mozilla
```
appreg	extensions  firefox

```
and (you didn't ask but I think it may be relevant)
ls ~/.mozilla-thunderbird
```
.  ..  cpmuhmdv.default  profiles.ini

```
the cpmuhmdv.default folder is where the address books live and where the Mail folder (containing the mail "folders" which thunderbird uses) lives.

Your point about move v copy is a good one.  Personally I don't expect to move anything in these circumstances.  I haven't yet tried it, but I expect nautilus' drag/drop default between partitions would be copy just as it is between [partitions on] different disks.

Now that 10.04 is working (albeit without all the functionality by way of applications I want) there isn't the same urgency; the risks associated with doing major system changes have gone, so the back-up requirement reverts to normal.  I can do my normal things on 8.04 until 10.04 is capable of doing them and I think that can be piecemeal.

Anyway, most of the next 12 hours I plan to be asleep!

---

### Post by oldfred on 2011-02-24
I run the dpkg to reinstall everything with each new version update, as I do clean installs. Once beta is out I run it with beta, and RC & final release, partially to test my reinstall script and to make sure it installs everything correctly.  It then installs the newer version if a newer version of the software has been included. If a package has been obsoleted it will not download those. And if already installed it will not reinstall them.

I have Firefox and Thunderbird profiles still my my shared NTFS partition as I originally was dual booting with XP. I found it easy to just modify profile.ini to make the links in each new install of Ubuntu. The rest of my data is in a /data partition which I now use for all the Ubuntu folders in /home. I delete the standard folders, and link in the same folder from my /data. Only one or two apps have noticed the links as opposed to a file folder. One was boot info script. New verison of boot script now has also corrected that.

---

### Post by kansasnoob on 2011-02-25
Sorry for the long absence again. I see now from post #34 that thunderbird must be "**.mozilla-thunderbird**". I didn't know if it shared ".mozilla" with Firefox or not, but now I know :)

One other thing I notice is that you've created a "download" folder. Is that correct? It's not a problem but Lucid by default has a "Downloads" folder. I just wanted to point that out to you to prevent confusion.

Just FYI the "ls" command will list common folders/files in home, but "ls -a" will list "all" folders/files including "hidden folders/files". Not that you really need to parse the differences, but it was just handy for me :D

Like here's the output of both in my new Hardy:

```
lance@lance-desktop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos

lance@lance-desktop:~$ ls -a
.              Documents        .gvfs          .pulse
..             .esd_auth        .ICEauthority  .pulse-cookie
.adobe         Examples         .local         .recently-used.xbel
.aptitude      .fontconfig      .macromedia    .ssh
.bash_history  .gconf           .metacity      .sudo_as_admin_successful
.bash_logout   .gconfd          .mozilla       Templates
.bashrc        .gksu.lock       Music          .thumbnails
.cache         .gnome2          .nautilus      .update-manager-core
.compiz        .gnome2_private  .opera         .update-notifier
.config        .gnupg           Pictures       Videos
Desktop        .gstreamer-0.10  .profile       .Xauthority
.dmrc          .gtk-bookmarks   Public         .xsession-errors
```

And here's the output in my new Lucid:

```
lance@lance-desktop:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates

lance@lance-desktop:~$ ls -a
.              Documents         .gvfs          .pulse-cookie
..             Downloads         .ICEauthority  .recently-used.xbel
.bash_history  .esd_auth         .local         .sudo_as_admin_successful
.bash_logout   examples.desktop  .mozilla       Templates
.bashrc        .gconf            Music          .thumbnails
.cache         .gconfd           .nautilus      .update-notifier
.compiz        .gksu.lock        .opera         Videos
.config        .gnome2           Pictures       .xsession-errors
.dbus          .gnome2_private   .profile       .xsession-errors.old
Desktop        .gstreamer-0.10   Public
.dmrc          .gtk-bookmarks    .pulse
```

So before I begin I'm going to repeat three important warnings:

(1) **[COLOR="Red"]You must be booted into the OS you are transferring files to![/COLOR]** So in your case you want to be booted into your new Lucid. If you copy files/folders FROM a running OS to a non-running OS certain things like Evolution will be broken! When you reboot the "imported" changes should take effect. 

(2) The new version of Nautilus includes the options "Copy to" and "Move to". **[COLOR="Red"]Be sure to use "Copy to"[/COLOR]** so the existing file/folder remains in tact in the old OS. You'll see what I mean in the following example. Using "Move to" will hose the old OS and one of the main reasons for doing this is to retain the viability of the existing OS.

(3) Even though you're working with a fresh install think about backing up any folder/file you're "replacing" by simply right-clicking on the existing file/folder and selecting "Rename", then add something like "_OLD" to the end. Just one example, I have a bunch of screenshots, etc saved to my Lucid's /Desktop:

```
lance@lance-desktop:~$ ls ~/Desktop
diff_ls.txt               Screenshot-Appearance Preferences.png
File_transfer_1.png       Screenshot-Hardy sdb1 - File Browser.png
File_transfer_2.png       Screenshot-home - File Browser.png
File_transfer_comp.png    Screenshot-lance - File Browser-1.png
Hardy_ls                  Screenshot-lance - File Browser.png
Lucid_ls                  Screenshot.png
Post_transfer_error.png   Screenshot-Untitled Window-1.png
Post_transfer_errors.png  Screenshot-Untitled Window.png

```

If I were to "import" my Hardy /Desktop w/o backing that up I would lose those screenshots. This is also particularly true regarding "hidden folders/files" like .gconf, etc. So I could simply go to Places > Home Folder, then right-click on Desktop, select Rename, and change the name to Desktop_OLD. Maybe this screenshot will be helpful:

[ATTACH]184460[/ATTACH]

Now I'm going to post some actual screenshots of transferring my Hardy ".mozilla" to my new Lucid. I think it should be fairly self-explanatory. Everything should be read left to right. I began by going to Places > Removable Media > Hardy sdb1 and then double-clicking. Next I double-click on home which will display each user folder, so I double click on that and all common folders will be shown:

[ATTACH]184461[/ATTACH]

Next you'll see that I go to View > Show Hidden Files and it displays much more, including ".mozilla" which I right-click and then click on "Copy to" > Home folder. The next two shots show what you'll see if it's replacing an existing file/folder. If you know you don't want to save the existing file/folder, either because you created a backup, or because you just know you're right, then click on "Merge all" and/or "Replace all":

[ATTACH]184462[/ATTACH]

I also wanted to show a couple of common errors due to importing certain desktop folders:

[ATTACH]184463[/ATTACH]

That's just from .gconf and .gnome2. Believe me, if you imported an entire /home/username from Hardy to Lucid the conflicts would make you crazy :lolflag:

The coolest thing about learning how to do this is the fact that you can keep a stable OS running while piddling with a new OS at your leisure. I'm going to include two more posts, even if you're no longer reading, to explain two very basic but IMO necessary things:

(1) How to recover both Hardy's or Lucid's GRUB bootloader.
(2) My own pet peeves with Lucid and how to fix them.

Many thanks for being so patient :)

As always please let me know if any of this is confusing. I hope to use this in the future as a sort of HowTo, so you've helped me as much as I've helped you.

---

### Post by kansasnoob on 2011-02-25
One thing I left out :(

What should you copy? Well, I'd definitely try copying .mozilla, then reboot. Next copy .mozilla-thunderbird and reboot again.

You'll have to decide about Documents, Pictures, etc. You can import whole folders. Just be sure to verify things before you think about trashing the old OS.

In fact don't trash the old OS until you know how to recover grub for each OS. Actually, now that you know how to dual/multi-boot you may decide you want to try a different distro! Just always do some research first because the designers sometimes do bad things like this:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

It's lunch time here and then probably nap time, but I'll be back.

---

### Post by col48 on 2011-02-25
responding briefly to the last 3 posts - I've got a printer/scanner problem and a granddaughter staying and it's already bedtime!

My download folder probably does what Lucid's Downloads will do, but I prefer to keep "standard" folders like that empty (like the mail 'inbox' and 'sent' folders) in order to retain control of what is where.  That doesn't apply to 'system' folders, of course.  So Photos is empty except while I am going through what has just been put there - all the stuff I want to keep is in Pictures etc.

I'll work my way through these posts tomorrow or after the weekend.

Thanks for all your time and effort, kansasnoob - and your patience.  I realise it was not just for me, but I appreciate it all the same.  And there may yet be questions!

---

### Post by col48 on 2011-02-26
In .mozilla/firefox there is a folder called xxxxx.default

In Hardy, xxxxx is lvy065hm
In Lucid, xxxxx is vkuuxfit

In each case there is a file .mozilla/firefox/profile.ini which refers internally to this folder.  The folder itself has a lot of stuff in it including (for Hardy) stuff clearly relating to Firefox add-ons.

1. Does it matter if (when logged into Lucid) I overwrite the Lucid one - after backing up the original - with the Hardy one despite the different xxxxx?

2. Does copying this folder give me the add-ons in Lucid, or would there be loose ends?

---

### Post by oldfred on 2011-02-26
I have my profile in a windows shared NTFS partition. I just load Thunderbird and Firefox once to create defaults and then edit profile to use my common one in the shared. I also copy the entire profile to my laptop when traveling and copy back. I have upgraded in place and new installs and just update profile.ini. For short times I had slightly different versions in windows & Ubuntu and they still worked.

The only issue is some add-ins in windows do not work in Ubuntu & vice-versa. But everything else works just fine. I would expect everything to work for you.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by col48 on 2011-02-26
Thanks oldfred, that's reassuring.

---

### Post by kansasnoob on 2011-02-27
> **col48 said:**
> In .mozilla/firefox there is a folder called xxxxx.default

In Hardy, xxxxx is lvy065hm
In Lucid, xxxxx is vkuuxfit

In each case there is a file .mozilla/firefox/profile.ini which refers internally to this folder.  The folder itself has a lot of stuff in it including (for Hardy) stuff clearly relating to Firefox add-ons.

1. Does it matter if (when logged into Lucid) I overwrite the Lucid one - after backing up the original - with the Hardy one despite the different xxxxx?

2. Does copying this folder give me the add-ons in Lucid, or would there be loose ends?

As oldfred said, it shouldn't be a problem. When I did my two test installs of Hardy and Lucid to perform this and take notes, I had actually launched Firefox in Lucid first so the "file/folder" copying would cause the "replace all" and "merge all" dialog windows to pop up.

After completing a fresh install no .mozilla exists until Firefox is launched the first time. So as long as you're copying from the "shutdown" Hardy to the "running" Lucid you should be OK. And remember as long as you're "copying" from, rather than "moving" from, the old OS the files/folders in the old OS will still remain unaltered.

I've used this same general method many times when someone has hosed their Ubuntu OS and I can no longer get it to run. Of course there must be ample disc space but otherwise I've found it to be a real time saver as compared to transferring data to an external device, and then transferring the data back to the new install.

Did you get the printer/scanner running in Lucid?

---

### Post by kansasnoob on 2011-02-27
At the end of post #36 I said:

> I'm going to include two more posts, even if you're no longer reading, to explain two very basic but IMO necessary things:

(1) How to recover both Hardy's or Lucid's GRUB bootloader.
(2) My own pet peeves with Lucid and how to fix them.


I'm having second thoughts about that :P

Why drive you crazy with stuff you don't need to know? Regarding grub (the bootloader) I'll just say this, Lucid uses grub 2 whereas Hardy used legacy grub. So you must be sure you're following grub 2 procedures for Lucid. I doubt you'll have any problems unless you choose to remove Hardy altogether in which case please ask ahead of time here at the forums.

Regarding pet peeves, why would you care about mine? I think it's more appropriate to ask if there's anything about Lucid that you don't like, or that you wish were more like Hardy? If so just shout.

---

### Post by col48 on 2011-02-28
Kansasnoob:

Can I encourage you to put in something about Grub/Grub2?  For instance..
1. How do you know which you are running?
2. What procedures are you talking about in the previous post?
3. Maybe pointers to the recovery processes - someone must have written it down.  I can see that detailed instructions in this thread may be a bit much for most folk who read this thread, but pointers to elsewhere would be a friendly gesture.

I have decided not to blindly try to install everything on Lucid which I had on Hardy; it is an opportunity to do a bit of housekeeping.  So I have compared the output of dpkg --get-selections on my Hardy system with that on the fresh Lucid system and am going through the 600 which were on Hardy but not Lucid with the help of Synaptic to see what I really want.  About 800 were common to both.  Many of the 600 are recognisably previous versions of what is there on Lucid.  This is slow but I think it is worthwhile.

Things I don't like about Lucid?  I would be cautious at the moment, because there are a few things (so far) which seem to be done differently which I have not figured out yet; if I can't figure them out eventually you can be sure I'll shout!  But I remember when I started with Hardy after using Windows95 (bless it!) there were quite a few niggles simply because I needed to retrain my habits - it wasn't that one was better than the other in those respects.  I do like the fact that in Linux there are often several ways of doing the same thing (eg a GUI or a Terminal, or a different choice of software) when in Windows there might be only one.

As for the printer - I've tried printing and scanning and they both work out of the box.  I have not had to fiddle around with anything, which has been a very pleasant surprise.  I will probably install xsane, though - SimpleScan (which Lucid installed) seems slow and does not offer ocr - although maybe that's because I haven't taken any steps to install any.  Thanks for asking.

At the moment I feel I am still setting up Lucid but I am sure it will be my primary OS within a week or so - everything else in life stops it being sooner.

---

### Post by kansasnoob on 2011-03-03
Sorry to disappear for so long. I've been embroiled in Natty Alpha 3 iso and upgrade testing. Give me just a bit and I'll answer your questions.

---

### Post by col48 on 2011-03-03
Hi kansasnoob

I'm struggling to get thunderbird up and running (separate thread on that).

Lucid seems rather slow - except the boot, which is noticeably faster than Hardy.  Maybe it is the applications (OpenOffice, Thunderbird as far as I can get it to go...) which are slow.

Also (very minor point, I suppose) trying to drag a window from one workspace to another doesn't have any effect.  It goes through the motions just like Hardy but nothing gets moved.  I haven't searched for a solution yet - Thunderbird is more important.

Otherwise, Lucid is very nice.  There's many a package which I don't have on Lucid and which I can't see why it was there for me in Hardy!

---

### Post by kansasnoob on 2011-03-05
Sorry again to disappear for so long. I rather dedicated myself to fixing [[COLOR="Red"]problems with the live-installer[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1622388") that began with Maverick, and combined with [[COLOR="Red"]Boot Info Script issues[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1676235"), I've kept quite busy.

I'm glad to see you seem to have gotten [[COLOR="Red"]Thunderbird straightened out[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1699262"). I'm not sure about the drag-n-drop changes in Nautilus. Give me just a bit to look at that.

Regarding grub I've not forgotten you. A long time ago I started a "thing" regarding that but I always got myself stumped. Knowing how to do things and knowing how to explain things are two totally different things.

I really do think it's best not to concern yourself with that ATM. Just don't do any repartitioning w/o detailed instruction. Right now I need some fresh air really bad ;)

---

### Post by col48 on 2011-03-06
Fresh air is good!

As you saw in the other thread, Thunderbird is running sweetly now - and (maybe strangely) other apps appear to be up to speed as well.

Re partitions.... I can't see me having a need for more partitions since the advantage of having more for purely data storage is minimal and I do not propose to run more than two OS at a time.  Thanks to your detailed help I have got two partitions up and my plan is eventually to replace Hardy with a later (not yet released, probably LTS) version of Ubuntu.

Having one working OS (through which help can be found if needed, and required work continue) while upgrading or replacing or otherwise fundamentally changing the other looks like a good way to always have a working system (subject to hardware failure, of course!).

I don't anticipate the grub stuff will be something I need (although I am curious) but it may be that others using this thread may well be looking for that as well.

---

### Post by col48 on 2011-03-06
I've marked this thread as solved because there are no more outstanding problems as such, although there may be more posts added.

I've given this post a title which is more descriptive of how the thread developed.

---

