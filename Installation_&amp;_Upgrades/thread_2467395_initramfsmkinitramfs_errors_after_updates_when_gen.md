---
title: "initramfs/mkinitramfs errors after updates when generating kernels"
date: 2021-09-25
forum: Installation &amp; Upgrades
---

### Post by slaytanicprion on 2021-09-25
I brought this up in an old thread but nobody was paying attention anymore, well I got what I should have screengrabbed the first time this problem happened. I only lack one (or two, but they relate to the same thing) pieces of evidence, the first time the following error happened when upgrading linux-firmware (the only package I had to update at the time), I was running kernel 5.4.0-79 and had installed 0-80 but hadn't rebooted into it yet. I got a CLI-like message about a file that I can change a setting to from "no" to "yes", relating to initramfs...I've explained everything below and have included screengrabs when almost the same thing (the first time, it tried several times over and over to get those "Permission Denied" "Generating...." initramfs/kernel lines and when it gave up it told me I could simply change a file's config line from no to yes in the future), as you can see, it didn't happen this time, but everything else behaved the same. ](*,)


I was up to 90+ needed updates so I decided to reboot. I have  screengrabs of the same exact thing happening, so you all can finally  see exactly what is happening with initramfs and mkinitramfs and the  kernels after doing important updates, mostly kernel updates it looks  like, I went from 5.4.0-81-generic to 5.4.0-86-generic (uname -r  output).
The first time it happened it told me to change some file's setting  regarding initramfs and change a line's value from "yes" from "no". Now a  message I see when booting after the initial Ubuntu Mate logo screen, I  get for a few seconds a line about this very same subject showing up,  nothing else, then the login portal shows up and everything works as it  should....a bit poorly at times, but the hard drive it is on needs  replacement, it's not entirely fubar, but has many bad blocks, I don't  keep anything important on the OS partition so it's no issue. I'll show  you happens with those permission denied kernel related  initramfs/mkinitramfs messages when updating that I get which do not get  logged in anywhere, so I had to reboot and do the updates and reboot  again and see what happens after unfortunately seeing those same  semi-worrying update errors (that do not cause any packages to be fail  to install and be installed corrupted.

[URL="https://imgbox.com/V1zIgThV"][IMG]https://thumbs2.imgbox.com/39/80/V1zIgThV_t.png[/IMG]
[/URL][[IMG]https://thumbs2.imgbox.com/94/d0/GWwLwGgq_t.png[/IMG]]("https://imgbox.com/GWwLwGgq")
 
[[IMG]https://thumbs2.imgbox.com/40/e3/pYQB2RCp_t.png[/IMG]]("https://imgbox.com/pYQB2RCp")

[[IMG]https://thumbs2.imgbox.com/47/32/qFPozxUJ_t.png[/IMG]]("https://imgbox.com/qFPozxUJ")
^
In this one last screengrab, I noticed with Synaptic that there were  still important updates not being made by Ubuntu Mate's Software  Installer....(which, I don't know if it's me...kind of sucks compared to  UM 18.04 LTS), and I got the same treatment. But new kernels get  installed fine, there's only one thing you'd need to see, what I was  told the first time something like this happened, to edit a file related  to initramfs-update to yes from no; after UM 20.04.2 loads and in  between the logo and the login screen, I get a black screen with one  line saying something about the same thing, saying it is set to no. This  is kind of beyond what I ever encountered here, and I saw some weird  stuff before I managed to fix myself. But now I got what I should have  had when I made this thread, screengrabs of the incidents, too bad I  don't have the original one where it kept trying and had a kind of CLI  message telling me I can always change that setting to yes in some file  related to mkinitramfs/initramfs. I shouldn't be told permission denied  when doing sudo initramfs-update, that's for sure. It seems it all comes down to that initramfs-tools/conf.d/resume.save file, where apparently I could change an option from no to yes, but I'm not doing anything yet until somebody with more experience than me (at least with this, in 11 years of Debian/Ubuntu/Mint/other Debian based distros, I've never seen this happen, upgrading software was always much more less problematic than on win7 or win xp x64 when I dual booted.

Thanks to anyone who figures this out in advance!

P.S. Yes I'm aware grub detects Mint 17.3 (I'm going to remove it from the drive it is on, since it's a seriously old and past-its-time OS, the only reason I haven't removed it yet is because, when I installed Ubuntu Mate 20.04 LTS, knowing it didn't need a swap partition, I formatted an entire hdd to ext4 and installed it there, but I never realized it was going to use the old swap partition on the other drive Mint 17.3 is on). So I'm fretting on that, I wonder if OS-Uninstaller, my choice software to get rid of OS's, will take out the swap partition on that drive and if it will create problems for this already strange install of UM 20.04.2....that problem isn't common, after searching on many search engines, I could find very little that looked like my issue, plus, this sort of thing doesn't end up in a log file, it kind of should. As for the Win7....it's not there anymore, it only sees the MBR because I didn't wipe the drive, there's data on it that I want to keep and not enough space to move it elsewhere, for now anyway, it is also on a separate hard drive, each internal hdd have their own OS, but obviously I don't use Mint 17.3 and win7 isn't there, so don't even mention it, grub sees the MBR, that's all.

---

### Post by slaytanicprion on 2021-09-28
After looking up some more, it has to do with the swap partition, from the old Linux Mint 17.3 partition on sda5 (ubuntu mate is on sdb...didn't install a swap partition since it wasn't necessary anymore...had no idea it would start using that old swap partition.

What's happening is strange though, I looked at the swap file and : 
swapon -s
Filename                Type        Size            Used    Priority
/dev/sda5              partition   15237116              295072    -2
[/CODE]

It's not used at all. I don't know what the Priority tag means here either. I remember early on when I installed UM Focal Fossa that I cleared that swap partition, after knowing it would be using it, I didn't want old data from Mint 17.3 that could be in there causing trouble, so with gparted I cleaned it up. That's why the whole system isn't crashing, 20.04 doesn't need a swap, but it will try to use one if it sees one. 

It seems I need to change the file resume or resume.save in /etc/initramfs-tools/conf.d . But I got not no experience with this, never thought a swap partition could give me headaches, especially since I thought finally no more damn swap partition when I moved to this OS. The contents are, for /etc/initramfs-tools/conf.d/resume :

```
RESUME=NONE
```

and resume.save

```

/etc/initramfs-tools/conf.d/resume

```

So resume.save is told to use the resume file which is set to none. I don't know what all of this wants to resume. But I dug deep enough that I think I found the source for that problem. Should I have the old 200gb SATA drive that has Mint auto-mount? or just the swap partition on it? Because it's not. I also didn't have this problem at first, it only showed up after a few new kernels were installed (which work fine). Care to put an end to his head-scratcher for me? I looked around and it seems it has to do with hibernation...and I don't do that, I only have my monitor turn off after some time of inactivity.

---

### Post by mikewhatever on 2021-09-28
Instead of posting screenshots of your desktop, about 90% of which is irrelevant info, copy/paste the text output you want us to see.
It is a strange thing to do, unless you also expect replies as screenshots.

---

### Post by Dennis N on 2021-09-28
The swap partition is set up at installation if one is detected. The OS needs to have its location in case you hibernate so it can resume on startup. Its stored as a UUID in the resume file. You could not hibernate if only a swap file is used. 

If swap location changes or gets removed, kernel updates will regenerate the initramfs and look at resume for the swap partition location, and can't find it so you get some error message. 

You can change swap to a different partition (there are a couple of steps needed to setup the new one), or else switch over to a swap file - a guide to doing that is here:

[Swap Partition to Swap File]("https://www.linuxuprising.com/2018/08/how-to-use-swap-file-instead-of-swap.html")

Note: If there is no swap partition present at installation, then a swap file is created, and a resume file is not created.

---

### Post by slaytanicprion on 2021-09-28
I didn't want a swap partition to start with, I forgot about the old one on another drive later like I said, I chose not to create a swap partition when installing, as 20.04 can run without one, but it decided to use sda5 (old Mint 17.3 swap). I would be okay with it using sda5, why won't it? I don't put my desktop to hibernation ever, except by accident when pressing the moon on the keyboard but that's not something that happens more than once every couple years.

Basically I want those permission denied errors to stop when doing updates. I was told that I could change something from No to Yes the first time it happened (not in the pictures here, forgot to do it), when it tried a lot of times to do what is failing here with initramfs/mkinitramfs, then a CLI-like message told me I could change something later so that it didn't happen again).I expected all of these messages to be logged somewhere but they aren't, hence the vagueness of my post, but afterwards, you get to see what happens everytime a kernel update happens. Plus the message I get before the login window (I don't have it in my mind right now, I'll write it down next time since it's impossible to take a screengrab then), just for 5 seconds a black screen will tell me something about those files or one of them, again. The system recognizes the swap partition, why isn't it using it? If it's what it takes to stop those annoyances I will go ahead, I don't want to create any new partition, don't have the place, well except on the drive sda5 (the old swap that Ubuntu Mate 20.04 used correctly at first but not after installing 2 kernels in a row and a bunch of updates, seems like it didn't like me not rebooting immediately into the new version of the kernel).

The swap file should be present right with 20.04 if I didn't create a swap partition at boot, since it wasn't necessary (and I wasn't aware the system was gonna go ahead and use the old swap partition on a different drive), right? I installed it the way without pointing to the old swap, but apparently it can use both a swap file and any swap partition it will find on other drives. I don't know why this bothers the software installer that much though...it doesn't seem like they are related issues.

How can I tell it to just use the swap partition that's on that other drive it had decided it was going to use until I got to have kernel 5.4.0-79 and 0-80 installed but not used for a very long time before I rebooted, then sometime when installing 0-81 is when it went crazy with those permission denied messages.

I'm running 5.4.0-86 right now, there's a newer kernel already up and ready for update, but I'd rather fix this first.

Thank you for taking a look at this.

---

### Post by slaytanicprion on 2021-09-28
> **mikewhatever said:**
> Instead of posting screenshots of your desktop, about 90% of which is irrelevant info, copy/paste the text output you want us to see.
It is a strange thing to do, unless you also expect replies as screenshots.

This is Software Installer text, it doesn't go to logs, and things move fast as this happens, I couldn't just copy/paste that evasive error text, not my fault this doesn't make it to log files, maybe it should.

I didn't show anything personal and even changed my regular background to a random kitty. The last one is more curiosity, as to why updates remain in Synaptic but are not showing up in Software Installer.

Don't take it the wrong way, but that was not very productive a post.

---

### Post by Dennis N on 2021-09-28
Since the warning says "Permission Denied", here are the permissions I have. It's from Ubuntu Mate 20.04:

```
dmn@Sydney:/etc/initramfs-tools/conf.d$ ls -l
total 8
-rw-r--r-- 1 root root 49 Dec  7  2018 resume
-rw-r--r-- 1 root root 14 May  2 09:36 splash

```

---

### Post by Dennis N on 2021-09-28
And the contents of the resume file. Just one line.

```
dmn@Sydney:/etc/initramfs-tools/conf.d$ cat resume
RESUME=UUID=1a40a397-7304-46fe-bb7b-830f81814c8b
```

---

### Post by Dennis N on 2021-09-28
One last comment (if you want to use the existing partition):

If resume has correct permissions, is in the right format and the UUID is correct, then run:
```

sudo update-initramfs -u
```

Also, check that the swap partition uuid in /etc/fstab is correct.

Then reboot and see everything works.

---

### Post by slaytanicprion on 2021-09-29
My permissions in the directory are normal :

-rw-r--r-- 1 root root 12 Jul 21 06:40 resume
-rw------- 1 root root 35 Jul 21 06:56 resume.save
-rw-r--r-- 1 root root 14 Jul 31  2020 splash

Yeah see, it's the content of resume that isn't good for me, it says RESUME=none, the little I found was that I needed to paste the UUID of a partition in there, the swap I want to use I guess? I would have to have the drive it is on automount then. Strange it didn't tell me that was an issue after the first few updates.

yeah.. I get permission denied when I do that, sudo update-initramfs too, I tried a while ago in the other thread I made before I could grab those unloggable errors.

I have no idea how this could be denied, as you see I have a normal user that should be let done whatever it does (or almost) with sudo.

But this is telling me even more that this resume file wants the UUID to a swap, can you ID what drive the file is pointing at for you?

---

### Post by slaytanicprion on 2021-10-11
content of '/etc/fstab/'
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=5de63a03-0b43-4705-8e28-ba7596f30082 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9c3dc736-72b8-42ba-a452-6adeb1996a31 none            swap    sw              0       0

```

I don't know about the error regarding the installation drive, it is still on sdb1. I got the swap's UUID. 

Looks like I should be inserting it in the resume or resume.save file instead of resume=NONE from what I was able to find out, but it's still unclear, cos I'm getting help topics 8-10 years old for ubuntu 14.04 and other debian distros back 5-10 years ago.

You guys helped out enough to get me to finish line. We've identified the problem, the system can't find the swap partition at boot, because it's not even in those initramfs/conf.d resume files. Don't let me down here! We're almost there!

---

### Post by slaytanicprion on 2021-10-12
is it possible to grab with print screen key the message I get in black  and white (a single line going on about initramfs-update/conf.d/resume  and resume.save). I know it won't work the way I'm trying it.

Strangely,  btw, Ubuntu MATE is now on sdc, the system decided an external drive  was now sdb. I think those issues are linked. I have a problem in that  whenever the desktop is not restarted properly (fully), going to POST  before grub, like right now I'm in the middle of renovating my bathroom  and I forgot to turn off my desktops in the house before I am so swamped  with work and i had to cut the power. There's also been a lot of power  losses lasting 30 seconds to 2 minutes for absolutely no explainable  reasons where I live, last week it happened when there wasn't a single  cloud in the sky. I hope my power variation secured power bars haven't  degraded too much. But anyway, I was saying this because somehow the  drive with Ubuntu MATE on it doesn't stay first HDD in boot (after  DVD/CD/BD and USB boot) order, it always falls back to sda, the drive  with min 17.3 and that swap on sda5. I'm about to just format that drive  (sda). I always have to go in the BIOS/UEFI and put back that drive  first. Well, I do whenever the desktop wasn't restarted purposefully,  like say after an update and I want to get in the new kernel, it will  work just fine, but unwanted power offs always cause that to happen,  this particular drive does though, not the first time I see it drift  from sdb1 to sdc or sde and external drives taking its place at sdb.

If  I'm to do that, I will have to create a swap file, not an issue, the  drive with UM has nothing important on it, I already mentioned how all  of this could be because it is quite a strange acting drive (you should  see those logs), and it has many bad blocks (that I have isolated using  great software, if you want to know what, I'll say). I'll eventually  replace it when not all of my extra money is going into the bathroom  renovations...that I would have left the way it was if it wasn't for my  s/o &#128580;

Meanwhile my previous post is pending an answer. My /etc/fstab/ file shows clearly how things were at install, but things aren't working like they should. I need to know if people here with swaps have the UUID for their swap partition is inserted in that resume file. Lower than it should be performance, the way it is happening right now is very reminiscent of an OS (namely windows) where if there's an issue with the windows swap file, it'll show.

---

