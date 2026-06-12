---
title: "All about ureadahead"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keybuk on 2010-03-20
Hey folks, we developers don't get the spare time to hang out on the forums for most of the release cycle, but in the past day I've tried to keep up with various boot-related issues and I've seen a few posts about ureadahead - and people recommending removing it.

I thought it might be a good idea to try and explain what it does, how it does it, and why "status 4" is a good thing.

Also I want to stress that I'm not going to tell you that there's nothing wrong with it, and that you haven't had a genuine issue, but just that I haven't heard about it if you have!  I'd really appreciate it if anybody who is having problems could help out with some debugging to understand the problem, then I'll be able to fix it for you and everyone else!

**What does ureadahead do?**

In order to boot Ubuntu, we need to read somewhere between 100MB and 200MB of data from the disk and into memory.  Unfortunately the slowest part of your otherwise awesome machine is its hard disk -- that's why we want this data into memory in the first place.

Hard disks aren't just slow to read data, they're slow to find it as well!  So we can lose a time of time during boot just waiting for the hard disk to find the data we need, and then read it into memory.

What ureadahead does is figure out what pieces of which files we actually need, and read everything from the disk into memory in one go.  By doing it at once we don't need to spend so much time finding everything, and because it's already in memory, we don't waste anywhere near as much time during boot.

**It's just for SSD right, not rotational HDD?**

No, quite the opposite.  You're thinking of sreadahead ("Super-readahead").  This was a similar tool written by Intel for their Moblin project, and is very unashamedly optimised for SSDs.

We tried it for a while, but found that its performance was simply terrible on rotational hard drives.

I sat down, drank a large amount of Tea, and wrote ureadahead ("Über-readahead") to replace it.  ureadahead from the get go was unashamedly optimised for rotational hard drives, that's not to say it's poor on SSD either, it performas at least as well as sreadhead there.

**But ureadahead takes several seconds of my boot!**

Yes it does; it's reading all the data in one go.  If you didn't have it, those several seconds would be simply spread out across everything else, and probably last two or three times longer!

**I looked at bootchart, and ureadahead doesn't get full throughput**

Even though ureadahead reads everything in one go, and is heavily optimised to read everything in the actual order it's on the disk, it still has to skip over the bits it doesn't need.

This "seek time" is the same performance penalty as finding data in the first place.

The only way to avoid this is defragmenting your disk.

**But Linux filesystems don't need defragmenting!**

Whoever told you that is deeply mistaken, this is one of the most common myths of Linux.

What is true is that Linux filesystems avoid, where possible, fragmenting their inode tables.  This means that the index of how files are split up (fragmented) across the disk, and where those parts are, tends to be kept together as a whole.

That's a good thing; fragmentation of inode tables is a big problem for other filesystems (FATs in that filesystem, etc.) so by keeping them together, it wins a lot of performance.

But the data itself is still fragmented, and spread all over your disk in a random order.  And unfortunately during boot, it's the data we need.

One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.

**When does ureadahead reprofile?**

Any time a package is installed or upgraded that contains a file in /etc/init or /etc/init.d; this is a bit brute-force, and means we're probably reprofiling a bit more than we'd like.

To force a reprofile, simply remove the "pack" files in /var/lib/ureadahead and reboot.

In a future version we intend to move to each boot improving the pack file by identifying things read that were never used, and new things that weren't read last time.

**When does ureadahead stop profiling?**

ureadahead slightly assumes you're using auto-login; so waits about 45s after the display manager starts before it stops reprofiling.  If you're logging in with a password, and want your desktop files included in the pack, type quickly ;)

(This will be addressed in a future version too).

**ureadahead slows down my boot!**

I want to hear from you!  It really shouldn't; to give you an example of the savings, my trusty laptop boots in about 1m30s without ureadahead - and only 30s with it.

Make sure you have the bootchart package installed.  Remove the ureadahead pack files, and move the /etc/init/ureadahead.conf file to something like ureadahead.disabled.  Reboot, login, etc. and wait for the bootchart to appear ("watch status bootchart" until stop/waiting).

Now put the ureadahead conf file back, reboot and login again and wait for bootchart to appear.

Finally reboot and login once more, and wait for bootchart to appear.

You'll now have three bootcharts.  One is without ureadahead, one is when ureadahead is profiling, and the final one is with ureadahead behaving normally.

File a bug report on ureadahead (ubuntu-bug ureadahead) and attach these three files along with the output of "sudo ureadahead --dump" (this is quite a bit, so capture it in a file).

I'll take a look, and we'll see if we can fix that bug for you!

**ureadahead exits with status 4!**

This isn't actually a bug ;-)

Status 4 (usually ureadahead-other exits with this) means that you had a mountpoint in your fstab that didn't have any files on it needed during boot.  Probably that drive with all those MP3s and movie files on it.

It still reads everything needed during boot, the status is just there for me to debug other issues.

The real bug here is that Upstart spams the console with that message, even though the ureadahead-other.conf file has "normal exit 4" in it!

(In other words, If your boot fails, this message is completely unrelated to that!  It's more likely that there is an issue with the X server starting, or an issue with init scripts not being run -- a good clue might be whether you see a login: screen after pressing Alt+F2)

---

### Post by drs305 on 2010-03-20
Thank you for taking the time to explain this!

---

### Post by Jay_Bee on 2010-03-20
Hi keybuk,
I don't have a problem with ureadahead I just want to thank you for this very interesting and informative post :)

---

### Post by michy99 on 2010-03-20
The only problem I have with ureadahead is that when it does a reprofile, it slows everything down to a crawl and the only way to fix it is to re-boot. In other words, when I do an update which requires a ureadahead profile, I re-boot. The boot process takes forever and anything I do is slow as molasses. I re-boot again and everything is back to normal.

---

### Post by MacUntu on 2010-03-20
> **drs305 said:**
> Thank you for taking the time to explain this!

+1

Good read for testing newbies! :)

---

### Post by vishalrao on 2010-03-20
thanks "SJR"... go dancing monkeys go!

---

### Post by dino99 on 2010-03-20
Good news to have you sparing time with us a saturday afternoon.

I'm one which have some issues to boot and reboot:

let say my system have 2 hdd ide & ihdd sata; each of them have a different OS: Jaunty64, Karmic32 and the last Lucid32. They are all ext3 but Lucid ext4, and boot with grub2 (Lucid release).

95 % boot fail with kernel panic (not syncing, can't mount unknown block) the first time, making again a cold boot, it generally boot but complaint since a week or so with hdd needed fsck. Have a quick message on screen saying ureadahead ended with status 4 now (some days ago that was status 2).

Here is for booting, when i want to reboot: session is closed but system never stopped (freezed, cold stop needed), stop (switch off) work fine.

So, Lucid was a clean install with A2, then updated. Logs does not help about those problems as nothing is logged about starting or closing.

I wonder if these problems are related to:
- parted used when installing A2
- one of gdm/ureadahead/plymouth given some conflicts/priority/timing

i would like to report about that but how: which package, how to trace and generate usefull logs .

---

### Post by kansasnoob on 2010-03-20
Very, very informational and helpful! Many thanks :D

---

### Post by kansasnoob on 2010-03-20
Note to mods: could we make this a sticky please?

---

### Post by keybuk on 2010-03-20
> **michy99 said:**
> The only problem I have with ureadahead is that when it does a reprofile, it slows everything down to a crawl and the only way to fix it is to re-boot. In other words, when I do an update which requires a ureadahead profile, I re-boot. The boot process takes forever and anything I do is slow as molasses. I re-boot again and everything is back to normal.

Actually the boot when profiling is probably just how slow your boot would be without ureadahead installed, and should be addressed when we do online reprofiling.

The slowness after could be related to the kernel trace buffer size, which has a fix pending for next week

---

### Post by plun on 2010-03-20
> 
Make sure you have the bootchart package installed. Remove the ureadahead pack files, and move the /etc/init/ureadahead.conf file to something like ureadahead.disabled. Reboot, login, etc. and wait for the bootchart to appear ("watch status bootchart" until stop/waiting).

Remove pack files.... ???

Move ureadahead.conf.... ???

Just dont get it....;)

---

### Post by VMC on 2010-03-20
> **keybuk said:**
> ..."status 4" is a good thing.Apparently I don't have problems. I don't see "status 4" anywhere, both removing "quiet" and watching text, and viewing "/var/log" files. Or I'm looking in the wrong place.

> **keybuk said:**
> ...
**But Linux filesystems don't need defragmenting!**
...
One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.How far into the future and is there anything I can do now, outside of a fresh install?

> **keybuk said:**
> 
**When does ureadahead reprofile?**
...
**When does ureadahead stop profiling?**
...
**ureadahead slows down my boot!**
 I use autologin. Also from grub to desktop is 25 seconds using P4, 2 gig ram, Intel i865 video, 1 rotational SATA hard drive. That's the fastest boot I have ever experience!

I could do the boot test you suggest for my viewing pleasure, but as I see it, for me anyway, ureadahead has preformed very well.

---

### Post by MacUntu on 2010-03-20
> **VMC said:**
> and is there anything I can do now, outside of a fresh install?

Not practicable and naïve, but:

* use ureadahead --dump to get the list of boot files
* determine the total size of all files
* on a second disk, create a partition (at the "front" of the disk) just large enough to hold the boot files
* copy over the files
* resize the partition so it's large enough to hold the rest of your system
* copy over the rest of your system (of course not overwriting the boot files)

For me that halves the time spent with ureadahead (7,200 rpm disk) but over time (as files get changed) this speedy effect wears down.

EXT4's online defragmentation should make this task a lot easier. :D

---

### Post by emarkay on 2010-03-20
KB-  Thanks for the info - make sure this gets into the documentation!
MU - what's this about "online Defrag"? That sounds scary - taking the "Cloud" a bit too far?

---

### Post by lavinog on 2010-03-20
> **keybuk said:**
> Actually the boot when profiling is probably just how slow your boot would be without ureadahead installed, and should be addressed when we do online reprofiling.

The slowness after could be related to the kernel trace buffer size, which has a fix pending for next week

Thank you for the info.
I wonder if the fix will fix this bug:
[url]https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715
[/url]

---

### Post by lavinog on 2010-03-20
> **emarkay said:**
> 
MU - what's this about "online Defrag"? That sounds scary - taking the "Cloud" a bit too far?

online defrag refers to defragging while the filesystem is mounted.  No cloud involved.

---

### Post by emarkay on 2010-03-20
> **lavinog said:**
> online defrag refers to defragging while the filesystem is mounted.  No cloud involved.


Aha! - Oldschool "Online"  (TRON-era terminology.)  Thanks.
FWIW, got a URL?  :)

---

### Post by lavinog on 2010-03-20
> **MacUntu said:**
> Not practicable and naïve, but:

* use ureadahead --dump to get the list of boot files
* determine the total size of all files
* on a second disk, create a partition (at the "front" of the disk) just large enough to hold the boot files
* copy over the files
* resize the partition so it's large enough to hold the rest of your system
* copy over the rest of your system (of course not overwriting the boot files)

For me that halves the time spent with ureadahead (7,200 rpm disk) but over time (as files get changed) this speedy effect wears down.

EXT4's online defragmentation should make this task a lot easier. :D

The problem here would be that many of the boot files will change over time...so you might have to do this many times.

A simpler approach could be to parse the dump list.  For each file, check for excessive fragments.  For each of those files, copy the file to a ramdisk (/dev/shm), delete the original, then copy the file back from the ramdisk.  You might have to do a sync between copies.

I wrote a script to do something like this, but in the end I realized my test system was still using ext3, so it didn't help.

---

### Post by Anduu on 2010-03-20
Very informative.

Thank you very much for taking the time out of your busy schedule to pay us a visit :KS

---

### Post by lavinog on 2010-03-20
> **emarkay said:**
> Aha! - Oldschool "Online"  (TRON-era terminology.)  Thanks.
FWIW, got a URL?  :)

[url]http://lwn.net/Articles/317787/
[/url]
The 3rd paragraph explains the reason for the "online" distinction.

---

### Post by MacUntu on 2010-03-20
> **lavinog said:**
> For each of those files, copy the file to a ramdisk (/dev/shm), delete the original, then copy the file back from the ramdisk.

But that wouldn't necessarily bring them closer together on-disk. Also rotational hard disks are a lot faster at their "beginning" (less access time, higher throughput), so putting those files there would make sense (some Windows defraggers already do this).

Anyways, I think we'll all use SSDs earlier than EXT4 gets its online-defrag *teasing akira fujita and co.*. :D

---

### Post by lavinog on 2010-03-20
> **MacUntu said:**
> But that wouldn't necessarily bring them closer together on-disk. Also rotational hard disks are a lot faster at their "beginning" (less access time, higher throughput), so putting those files there would make sense (some Windows defraggers already do this).

Anyways, I think we'll all use SSDs earlier than EXT4 gets its online-defrag *teasing akira fujita and co.*. :D

I see your point, but again, once those files get updated, they will become fragmented or moved.

Using your approach, wouldn't making a small filesystem just for the system files work as well.  This could then keep all system files near the beginning, while allowing some free space to minimize future fragmentation.

As for SSDs, I would still prefer files to not be fragmented (helps with data recovery)

---

### Post by MacUntu on 2010-03-20
I'm right there with you. That's why I called it "not practicable and naïve". :P

---

### Post by monraaf on 2010-03-20
> **keybuk said:**
> **When does ureadahead stop profiling?**

ureadahead slightly assumes you're using auto-login; so waits about 45s after the display manager starts before it stops reprofiling.  If you're logging in with a password, and want your desktop files included in the pack, type quickly ;)


Thanks for the informative post. But isn't there a potential privacy issue here? i.e. If you have an encrypted home then information about the files stored there may end up in one of these unencrypted pack files.

---

### Post by MacUntu on 2010-03-20
I think you are right: if I open a file '~/no_one_should_know_i_exist.txt' during ureadahead's profiling phase, then it will show up in /var/lib/ureadahead/pack (owned by root with 600 permission, but root cannot access an encrypted home dir, right?). Maybe worth a bug report.

---

### Post by k3lt01 on 2010-03-20
Thanks Keybuk, I'll try sometime today to get the relevant info posted to the report for both karmic and Lucid. Are there 2 separate reports or should I just put them both down on 1?

Btw fwiw, my issue can take an hour to get my machine to reboot when ureadahead reprofiles. It's not a small increase in time by any means.

---

### Post by kansasnoob on 2010-03-20
Bumpity-bump-bump-bump :)

Lets get this in the stickies :P

---

### Post by andrewabc on 2010-03-20
Thanks for info. Did not realize new readahead thing. Thought was just a change to plymouth.

Plymouth is just the graphical display thing, and has nothing important to do with how OS is booted? Correct?

EDIT:
googled and seems I was correct.

---

### Post by tseliot on 2010-03-20
This thread was stuck as requested.

---

### Post by phillw on 2010-03-20
> **keybuk said:**
> 

Thanks for taking the time and such an excellent explanation :D

Phill.

---

### Post by k3lt01 on 2010-03-20
Ok here goes some questions for you Keybuk.

I have Karmic done, it took approx 1/2 an hour before the lappy was at a usable stage and even then everything was just slow as a wet week.

I am unable to do Lucid with the instructions you provided, sorry. I'll explain. I installed bootchart, it also installed bootchartpy or whatever it's called. I then re-installed ureadahead which I promptly disabled  as per your instructions and as I had already done with karmic. I rebooted it went as per usual, at least usual until my lappy rebooted itself which it hasn't done for weeks since I last removed bootchart and bootchartpy. The only time I can keep this laptop going long enough to do anything, and even then it is pretty well unusable, is when a crash report was produced against plymouthd. Now plymouthd has never crashed until just now but I am unsure as to what caused it. I personally feel it was bootchart and bootchartpy. I don't really know as I can't get to read it because the laptop just reboots after a few minutes.

So now to my questions.
Do you want my Karmic info posted on the bug report for ureadahead?
Do you have another way to get the info for Lucid without bootchart and bootchartpy installed? I can remove it if there is another program that can do a similar thing.

---

### Post by mc4man on 2010-03-21
I find it's been working extremely well, particularly over the last few weeks. Now bootchart shows it running pretty much by itself as in the cropped image with most everything else directly after.
 The apparent 'boot time' is about 14-15 secs, (desktop up, populated and usable), this on an older p4 with some half decent sata hdd's.

---

### Post by k3lt01 on 2010-03-21
Bug report, [number 543230 ureadahead slows down my boot process]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/543230"), filed. This is for my Karmic install, I'm still trying to keep Lucid going long enough to get anything to happen.

---

### Post by soul_rebel on 2010-03-21
Would it be possible to do some CPU bound work during the read ahead phase?

What would happen if ureadahead was given some sort of "realtime" IO priority and all the others boot processes were set at the highest niceness and started in parallel?

I think it basically would act like a pipe letting process work as soon as readahead finds the files they need. Just like the classical reader/writer situation of concurrent programming.

By looking at any bootchart with readahead it seems that something like this could give a further 15%-40% improvement, by closing the last big hole in the current approach of disk first, cpu later.
So how about it?

---

### Post by Uncle Spellbinder on 2010-03-21
> **keybuk said:**
> **But Linux filesystems don't need defragmenting!**

[COLOR="Red"]Whoever told you that is deeply mistaken, this is one of the most common myths of Linux.[/COLOR]

What is true is that Linux filesystems avoid, where possible, fragmenting their inode tables.  This means that the index of how files are split up (fragmented) across the disk, and where those parts are, tends to be kept together as a whole.

That's a good thing; fragmentation of inode tables is a big problem for other filesystems (FATs in that filesystem, etc.) so by keeping them together, it wins a lot of performance.

But the data itself is still fragmented, and spread all over your disk in a random order.  And unfortunately during boot, it's the data we need.

One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.

The first time I've heard anyone "in the know" say that. The Ubuntu Forums (and others) are filled with new users asking if fragmentation effects Linux. I can't recall anyone saying it does. The stock answer from members seem to be "Linux does not need defragging as fragmentation does not effect Linux". Thanks for the clarification, keybuk.

---

### Post by k3lt01 on 2010-03-22
I have just tried a few times to get Lucid to create a bootchart, it wont do it, bootchart and pybootchartgui keep it crashing or rebooting after a few minutes. I am rushing to type this before it crashes or reboots. I am going to totally remove bootchart etc as it just isn't working properly

---

### Post by k3lt01 on 2010-03-22
Back again 41 minutes later after a 32 minute ureadahead reprofile, another reboot to be able to use my laptop, a post in the plymouth thread which prompted this one and now I am posting here.

Basically, I cannot get Lucid to work with bootchart and pybootchartgui, it just doesn't like them for some reason. However, ureadahead is still taking approx 1/2 an hour or more to reprofile my Acer laptop.

Sorry keybuk but the Karmic data samples are all I can provide and unless someone else can get you Lucid data samples I think its all your going to get to work with on the bug report. I hope it's a help of sorts.

---

### Post by keybuk on 2010-03-22
> **dino99 said:**
> Good news to have you sparing time with us a saturday afternoon.

I'm one which have some issues to boot and reboot:

let say my system have 2 hdd ide & ihdd sata; each of them have a different OS: Jaunty64, Karmic32 and the last Lucid32. They are all ext3 but Lucid ext4, and boot with grub2 (Lucid release).

95 % boot fail with kernel panic (not syncing, can't mount unknown block) the first time, making again a cold boot, it generally boot but complaint since a week or so with hdd needed fsck. Have a quick message on screen saying ureadahead ended with status 4 now (some days ago that was status 2).

This sounds like there is an issue with your drive controller to me; most likely a driver issue, but more remotely hardware.

That the kernel panics on most boots is very strange, you should file a bug on the kernel (ubuntu-bug linux).  It's almost impossibly unlikely to be an issue with any userspace process like ureadahead, plymouth or gdm - your crash is way before they're even started.

---

### Post by keybuk on 2010-03-22
> **lavinog said:**
> Thank you for the info.
I wonder if the fix will fix this bug:
[url]https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715
[/url]

Yes, very much so.

---

### Post by keybuk on 2010-03-22
> **monraaf said:**
> Thanks for the informative post. But isn't there a potential privacy issue here? i.e. If you have an encrypted home then information about the files stored there may end up in one of these unencrypted pack files.

The only information that would appear in the pack file is the filename and size, and a rough idea of which bits of the file are used during boot.

No data from the file is stored in the pack.

Also the pack is only readable by root since filenames themselves can be considered "disclosure".

---

### Post by keybuk on 2010-03-22
> **MacUntu said:**
> I think you are right: if I open a file '~/no_one_should_know_i_exist.txt' during ureadahead's profiling phase, then it will show up in /var/lib/ureadahead/pack (owned by root with 600 permission, but root cannot access an encrypted home dir, right?). Maybe worth a bug report.

It's not considered a security issue for root to know about the filenames (since root can find them out in any number of uninteresting ways - not in the least that root can access the filesystem while mounted).

Only disclosure to other non-root users would be a bug; and the pack is readable only by root to prevent this.

---

### Post by lean on 2010-03-22
Online defrag seems to be the way forward. Another improvement would be to use compressed files. The 10sec target is definitily technically possible, but needs some soft ressources to achieve (more programmers ;)

---

### Post by keybuk on 2010-03-22
> **andrewabc said:**
> Plymouth is just the graphical display thing, and has nothing important to do with how OS is booted? Correct?

Yes, Plymouth is the boot-time splash screen.  It does both graphical and text though - and also handles the issue of prompting for questions during boot (e.g. "filesystem check failed, try to fix it?")

---

### Post by keybuk on 2010-03-22
> **soul_rebel said:**
> Would it be possible to do some CPU bound work during the read ahead phase?

There isn't really much interesting CPU bound work that we need to do during boot.

It's not the right time for contributing to SETI ;-)

> **soul_rebel said:**
> What would happen if ureadahead was given some sort of "realtime" IO priority and all the others boot processes were set at the highest niceness and started in parallel?

It already has that priority; it's blocked in Upstart to avoid the race where we could check the filesystem and mount it read/write before running ureadahead - which can reorder the blocks and defeat the pack.

(ureadahead runs while the filesystem is readonly)

I think that your suggestion would only achieve an improvement if we had CPU-bound work that did not rely on any data from the disk - and we just don't have that anymore.  Part of the boot speed effort has been to eliminate all such processing from the boot.

---

### Post by MacUntu on 2010-03-22
> **keybuk said:**
> It's not considered a security issue for root to know about the filenames (since root can find them out in any number of uninteresting ways

So you are saying anyone that can boot a live CD is able to get the file list of an encrypted home directory? I know this is far beyond the scope of this thread, but that's all but uninteresting. :p

---

### Post by keybuk on 2010-03-22
> **MacUntu said:**
> So you are saying anyone that can boot a live CD is able to get the file list of an encrypted home directory? I know this is far beyond the scope of this thread, but that's all but uninteresting. :p

They would not be able to get the complete file list without the password, and certainly never be able to get the contents of the files.

There may be some individual filenames available from other parts of the system, for example in log files, session caches, nautilus thumbnail data, or the ureadahead pack - but only those filenames and no data.

---

### Post by lavinog on 2010-03-22
A while back there was a brainstorm idea to convert all boot scripts to machine code in hopes to reduce boot times.
Would there be any actual speed increase doing this?  If so would the gain outweigh the maintanability?

---

### Post by ShadowDragon on 2010-03-22
> **lean said:**
> The 10sec target is definitily technically possible
Sure it is. I have my entire desktop(!) ready in about 7 seconds (with auto login, can't type quick enough...) on my laptop running Karmic. It's just an Dell Vostro which I bought in Nov 2008. And that's even with some daemons starting during boot due to the LAMP server and VMWare I have installed. :)
Ureadahead sure does it works well for as far as I can see on my bootchart.

Haven't tested it on Lucid though... Experiencing some issues with Xorg and all new the graphics stuff... But if I look at the differences there will be in Lucid, and [some people achieving 4 seconds boots](http://ubuntuforums.org/showpost.php?p=8994639&postcount=226) in Lucid Beta, it might even be possible to break the 5 seconds barrier for getting to full desktop. :D


If I could only ditch my BIOS and replace it with UEFI...:-k:-D

---

### Post by lavinog on 2010-03-22
> **ShadowDragon said:**
> 
If I could only ditch my BIOS and replace it with UEFI...:-k:-D

Right.
It takes almost 10 seconds to get to the grub menu for me.
Detecting my SATA drives seem to take forever.

---

### Post by Longinus00 on 2010-03-22
The one thing I noticed about ureadahead is that every time it does a reprofile the amount of memory used after logging is much higher than normal (500MB as opposed to ~200MB on a 1GB laptop). It never seems to go away and makes my older laptop with 256MB unbearably slow. I assume that ureadahead is not finishing properly or freeing memory correctly but I've never really dug into it.

---

### Post by k3lt01 on 2010-03-22
@ Longinus. May I suggest you dig into it and add to the bug report so we can see if it can be made easier for low powered/low memory machines to work with it.

---

### Post by xebian on 2010-03-22
@keybuk
Won't you mind telling us which folder(s) you read ahead from?

---

### Post by ShadowDragon on 2010-03-22
To get a first impression you could use:
```
sudo ureadahead --dump --sort=path | grep '^/'
```

---

### Post by xebian on 2010-03-22
> **ShadowDragon said:**
> To get a first impression you could use:
```
sudo ureadahead --dump --sort=path | grep '^/'
```

Thanks ShadowDragon.  

I could see that it's more inclined for the mobile users.

@keybuk

Is it possible to have some kind of profiles say desktop or mobile?  From the dump I could see that a lot of them does not apply for my desktop - like modem manager, bittorrents, etc.  This way a user can streamline it knowing which one is not necessary.  This would be awesome - total control.

---

### Post by Longinus00 on 2010-03-22
It looks like the memory usage is also about doubled for my 256MB computer after profiling (Xubuntu 9.10). The doubling behavior is also exhibited on my 1GB laptop as mentioned in my previous post. (Ubuntu 10.04)
[LIST]
[*]Normal boot
```
             total       used       free     shared    buffers     cached
Mem:        249176     245136       4040          0      34784      81848
-/+ buffers/cache:     128504     120672
Swap:       514040          0     514040
```
[*]Profiling boot
```
             total       used       free     shared    buffers     cached
Mem:        249160     242120       7040          0       3296      28152
-/+ buffers/cache:     210672      38488
Swap:       514040      73624     440416
```
[/LIST]
Both of these are taken right after login after opening a terminal. The dump size is ~39 MB, quite a bit smaller than all that chewed up memory.
```
/var/lib/ureadahead/pack: created Tue, 23 Mar 2010 01:20:58 +0000 for hdd 8:6
27 inode groups, 1419 files, 1613 blocks (39204 kB)
```

None of the missing memory seems to be owned by any process; the resident set size drops drastically (about 2x) on a profiling boot. This seems to almost certainly be some problem with either the kernel or the ureadahead kernel patch.

The relevant bug for this is [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by keybuk on 2010-03-23
> **xebian said:**
> @keybuk
Won't you mind telling us which folder(s) you read ahead from?

Whatever folder(s) you use on boot.

ureadahead uses the kernel tracing mechanism to get a list of the files actually read on boot on _your_ machine.

---

### Post by keybuk on 2010-03-23
> **xebian said:**
> Thanks ShadowDragon.  

I could see that it's more inclined for the mobile users.

@keybuk

Is it possible to have some kind of profiles say desktop or mobile?  From the dump I could see that a lot of them does not apply for my desktop - like modem manager, bittorrents, etc.  This way a user can streamline it knowing which one is not necessary.  This would be awesome - total control.

One of the whole points of ureadahead is that the profile is custom tailored to each machine.  If you see modem manager and bittorrent in your dump, it's because they were started on boot on your machine.

---

### Post by ShadowDragon on 2010-03-23
> **Longinus00 said:**
> It looks like the memory usage is also about doubled for my 256MB computer after profiling (Xubuntu 9.10). The doubling behavior is also exhibited on my 1GB laptop as mentioned in my previous post. (Ubuntu 10.04)
[...]
None of the missing memory seems to be owned by any process; the resident set size drops drastically (about 2x) on a profiling boot. This seems to almost certainly be some problem with either the kernel or the ureadahead kernel patch.

The relevant bug for this is [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

Nice find! Seems to explain a few thing I have noticed on my system and others.
/me subscribed to bug 501715.

---

### Post by Owen.C93 on 2010-03-23
I might aswell look at defraging then. Can anyone recommend a defargmenter.

Any time I google them I just get responses saying linux doesn't need one. I put it into synaptic but I' not sur if that's what I'm looking for?

---

### Post by VMC on 2010-03-23
> **Owen.C93 said:**
> I might aswell look at defraging then. Can anyone recommend a defargmenter.

Any time I google them I just get responses saying linux doesn't need one. I put it into synaptic but I' not sur if that's what I'm looking for?

Read this for some more information on [***defrag***]("https://bugs.launchpad.net/ubuntu/+bug/321528"). It also depends on what file system your currently using.

---

### Post by MacUntu on 2010-03-23
Even if you defragment all files you'll still have gaps between files (results in seeks). IMO that's a bigger problem than file fragmentation, eg. out of the 2,000 files in my pack file only 50 are fragmented (read: having discontinuities in block numbers used).

---

### Post by lavinog on 2010-03-23
> **Owen.C93 said:**
> I might aswell look at defraging then. Can anyone recommend a defargmenter.

Any time I google them I just get responses saying linux doesn't need one. I put it into synaptic but I' not sur if that's what I'm looking for?

I don't think the online defragger for ext4 is ready yet.

You can use the command filefrag to get an idea on how fragmented a file is.  If you make a new copy of the file, you should get a less fragmented file. (emphasis on "should")
There are many scripts around that do this automatically.

You can also use the approach mentioned in post #13 of this thread...it may yield the best results.

---

### Post by xebian on 2010-03-23
> **keybuk said:**
> One of the whole points of ureadahead is that the profile is custom tailored to each machine.  If you see modem manager and bittorrent in your dump, it's because they were started on boot on your machine.

This is a home built whitebox and these don't make sense.

```

/usr/lib/ModemManager/libmm-plugin-generic.so (10 kB), 1 blocks (12 kB)
/usr/lib/ModemManager/libmm-plugin-gobi.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-hso.so (26 kB), 1 blocks (28 kB)
/usr/lib/ModemManager/libmm-plugin-huawei.so (30 kB), 1 blocks (32 kB)
/usr/lib/ModemManager/libmm-plugin-mbm.so (26 kB), 1 blocks (28 kB)
/usr/lib/ModemManager/libmm-plugin-moto-c.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-nokia.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-novatel.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-option.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-sierra.so (18 kB), 1 blocks (20 kB)
/usr/lib/ModemManager/libmm-plugin-zte.so (14 kB), 1 blocks (16 kB)

/etc/acpi/events/asus-brightness-down (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-brightness-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-eee-volume-mute (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-eee-volume-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-f8sv-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-rotate (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-video (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-wireless-2 (0 kB), 1 blocks (4 kB)
/etc/acpi/events/battery (0 kB), 1 blocks (4 kB)
/etc/acpi/events/ibm-wireless (0 kB), 1 blocks (4 kB)
/etc/acpi/events/lenovo-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/panasonic-lockbtn (0 kB), 1 blocks (4 kB)
/etc/acpi/events/sony-volume-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/thinkpad-cmos (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-battery (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-hibernate (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-ibutton (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-lock (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-mail (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-next (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-play (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-prev (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-stop (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-www (0 kB), 1 blocks (4 kB)


```

---

### Post by keybuk on 2010-03-23
> **xebian said:**
> This is a home built whitebox and these don't make sense.

```

/usr/lib/ModemManager/libmm-plugin-generic.so (10 kB), 1 blocks (12 kB)
/usr/lib/ModemManager/libmm-plugin-gobi.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-hso.so (26 kB), 1 blocks (28 kB)
/usr/lib/ModemManager/libmm-plugin-huawei.so (30 kB), 1 blocks (32 kB)
/usr/lib/ModemManager/libmm-plugin-mbm.so (26 kB), 1 blocks (28 kB)
/usr/lib/ModemManager/libmm-plugin-moto-c.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-nokia.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-novatel.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-option.so (14 kB), 1 blocks (16 kB)
/usr/lib/ModemManager/libmm-plugin-sierra.so (18 kB), 1 blocks (20 kB)
/usr/lib/ModemManager/libmm-plugin-zte.so (14 kB), 1 blocks (16 kB)

/etc/acpi/events/asus-brightness-down (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-brightness-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-eee-volume-mute (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-eee-volume-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-f8sv-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-rotate (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-video (0 kB), 1 blocks (4 kB)
/etc/acpi/events/asus-wireless-2 (0 kB), 1 blocks (4 kB)
/etc/acpi/events/battery (0 kB), 1 blocks (4 kB)
/etc/acpi/events/ibm-wireless (0 kB), 1 blocks (4 kB)
/etc/acpi/events/lenovo-touchpad (0 kB), 1 blocks (4 kB)
/etc/acpi/events/panasonic-lockbtn (0 kB), 1 blocks (4 kB)
/etc/acpi/events/sony-volume-up (0 kB), 1 blocks (4 kB)
/etc/acpi/events/thinkpad-cmos (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-battery (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-hibernate (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-ibutton (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-lock (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-mail (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-next (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-play (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-prev (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-stop (0 kB), 1 blocks (4 kB)
/etc/acpi/events/tosh-www (0 kB), 1 blocks (4 kB)


```

Drop the ureadahead pack, and reboot.  It'll regenerate.

Then check /sys/kernel/debug/tracing/trace

---

### Post by lavinog on 2010-03-23
> **keybuk said:**
> 
Then check /sys/kernel/debug/tracing/trace

This file is world readable...doesn't this bring up the same security issue mentioned before...even though the dump file can only be read by root, the trace file contains similar information.

---

### Post by xebian on 2010-03-23
> **keybuk said:**
> Drop the ureadahead pack, and reboot.  It'll regenerate.

Then check /sys/kernel/debug/tracing/trace

That's new pack after deleting *pack*.

BTW man ureadahead doesn't say much but I'm getting an exit status 5 on one box and there's no pack file.

---

### Post by Longinus00 on 2010-03-23
Thought I'd just chime in on memory usage of ureadahead for my 1GB laptop. (Ubuntu 10.04)
[LIST]
[*]Normal Boot
```
             total       used       free     shared    buffers     cached
Mem:       1018228     502744     515484          0      71844     240096
-/+ buffers/cache:     190804     827424
Swap:      1044216          0    1044216

```
[*]Profiling Boot
```
             total       used       free     shared    buffers     cached
Mem:       1018228     837472     180756          0     128800     243972
-/+ buffers/cache:     464700     553528
Swap:      1044216          0    1044216

```
[/LIST]
Again ureadahead is slightly more than doubling the amount of memory used after booting.

Trying to track down exactly where all the memory is going is a little tricky. The pack size is about 100 MB too small.
```
/var/lib/ureadahead/pack: created Wed, 24 Mar 2010 00:14:42 +0000 for hdd 8:3
29 inode groups, 2862 files, 2906 blocks (169292 kB)

```
If you add in the tracing buffer it's a little too large (or still too small depending on if it is really kb or kB).
```
cat /sys/kernel/debug/tracing/buffer_size_kb
128000
```

---

### Post by keybuk on 2010-03-23
> **xebian said:**
> That's new pack after deleting *pack*.

BTW man ureadahead doesn't say much but I'm getting an exit status 5 on one box and there's no pack file.

5 is an error while tracing

Add "console output" to /etc/init/ureadahead.conf and try again - you should get a message on the console

---

### Post by xebian on 2010-03-23
> **keybuk said:**
> 5 is an error while tracing

Add "console output" to /etc/init/ureadahead.conf and try again - you should get a message on the console

Thanks. will check it out later.

I'm convinced about the mobile inclination.  I see them as well in a virtualized ubuntu guest from the same box.  The only difference now are the gnome stuff vs. the kde stuff with the host.

Another thing I noticed is it reads as much as apps installed in your systems.  However, I think they should not even be as they have nothing to do with boot up like - cups, games, USBCreator, etc..

---

### Post by lavinog on 2010-03-23
> **Longinus00 said:**
> 
If you add in the tracing buffer it's a little too large (or still too small depending on if it is really kb or kB).
```
cat /sys/kernel/debug/tracing/buffer_size_kb
128000
```

how many filesystems / pack files do you have?

---

### Post by yoasif on 2010-03-24
> If the ureadahead daemon is optimized for auto-login ("slightly
assumes you're using auto-login; so waits about 45s after the display
manager starts before it stops reprofiling" from
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)), why is this the
default option? Shouldn't the fastest boot be the one that is
preselected, especially if the ureadahead daemon is optimized for this
use case?
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-March/010960.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-March/010960.html)

---

### Post by lavinog on 2010-03-24
> **yoasif said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-March/010960.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-March/010960.html)

I don't think it is technically "optimized" for autologin.
It just assumes that autologin is active and only continues to trace for an additional 45 seconds.

If autologin is not active it will still work, as long as you login before the 45 seconds is up.
If you don't login during that period, it just wont preread the files needed for logging in.

Maybe a separate daemon could be used during login to trace login files...then if the login screen is idle, it can cache the login files for the most frequent users.

---

### Post by Starks on 2010-03-25
ureadahead is a miracle worker. back in the jaunty/karmic days, my boot  times averaged anywhere from 40 seconds to 90 seconds.

on the very same hardware, i'm down to 20 seconds now.

---

### Post by soul_rebel on 2010-03-26
> **keybuk said:**
> There isn't really much interesting CPU bound work that we need to do during boot.

It's not the right time for contributing to SETI ;-)
It already has that priority; it's blocked in Upstart to avoid the race where we could check the filesystem and mount it read/write before running ureadahead - which can reorder the blocks and defeat the pack.

(ureadahead runs while the filesystem is readonly)

I think that your suggestion would only achieve an improvement if we had CPU-bound work that did not rely on any data from the disk - and we just don't have that anymore.  Part of the boot speed effort has been to eliminate all such processing from the boot.

You did not really understand me. I was suggesting of doing CPU-bound work dependent on data from the disk as soon as this data is available in cache.

I'll try with a semplified example scenario:
readahead reads files /1 /2 /3 /4
process 1 needs file /1 and so on. 4 processes in total.

BOOT:
readahead starts.
Processes 1-4 start immediately after. They all are locked in IO-wait.
readahead completes reading /1 and goes on.
process 1 is awaken from IO-wait as its blocks are ready; reads its file from cache and does its cpu-bound work.
And so for processes 2-4.

Let's say readahead takes 4 units of IO time and each process takes 1 CPU time.
Current approach is 4+1+1+1+1=8.
My proposed approach in this basic example would do it in 5 as processes 1-3 run while readahead is running.

This was the theoretical, simplistic, optimal example. It is surely an improvement over the current approach, but it could pose a few implementation problems. 
Writes and possible scheduler limitations come to mind.
Writes could be cached too and flushed only when readahead is done and each process is granted normal IO priority.
The scheduler might already support all that is needed.

Maybe this improvement is not that hard to achieve.
I hope I made myself better understood. :-)

---

### Post by Starks on 2010-03-28
Shouldn't stuff be happening before ureadahead finishes?

[http://imgur.com/ZqZjQ.png](http://imgur.com/ZqZjQ.png)

---

### Post by lavinog on 2010-03-28
> **Starks said:**
> Shouldn't stuff be happening before ureadahead finishes?

[http://imgur.com/ZqZjQ.png](http://imgur.com/ZqZjQ.png)

It could be that the files that are being read are really fragmented.
How much free space do you have in the drive?

I don't think there is an easy way to determine what stuff to start based on what was read in, but looking at your throughput, I am thinking that it is just reading the files slow.

---

### Post by lavinog on 2010-03-28
I found out that you can add bootchart=svg to the boot commandline to have it output in svgz instead.
svgz seems a much better format for these reasons:

It takes bootchart almost twice as much time to generate the png image.
```

time sudo bootchart -f svg -o "/var/log/bootchart" Shredder-karmic-20100328-1.tgz 
Parsing Shredder-karmic-20100328-1.tgz
Wrote image: /var/log/bootchart/Shredder-karmic-20100328-1.svgz

real	0m5.412s
user	0m7.120s
sys	0m0.470s
greg@Shredder:/var/log/bootchart$ time sudo bootchart -f png -o "/var/log/bootchart" Shredder-karmic-20100328-1.tgz 
Parsing Shredder-karmic-20100328-1.tgz
Wrote image: /var/log/bootchart/Shredder-karmic-20100328-1.png

real	0m9.102s
user	0m10.990s
sys	0m0.600s

```

The file size is much smaller.
```

-rw-r--r-- 1 root root  358144 2010-03-28 10:56 Shredder-karmic-20100328-1.png
-rw-r--r-- 1 root root   45081 2010-03-28 10:56 Shredder-karmic-20100328-1.svgz
-rw-r--r-- 1 root root 2061146 2010-03-28 10:42 Shredder-karmic-20100328-1.tgz

```


The information is parsable.
```

greg@Shredder:/var/log/bootchart$ zcat Shredder-karmic-20100328-1.svgz |grep -A 13 'Header text'
	<!-- Header text -->
	<text style="font-family: sans-serif; font-size: 14pt; font-weight: bold;" x="10" y="22">Boot chart for Shredder (Sun Mar 28 10:42:06 CDT 2010)</text>
	<g style="font-family: sans-serif; font-size: 9pt; fill: #000000;" transform="translate(10, 24)">
		<!-- System information -->
		<text dy="1.2em">uname: Linux 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64</text>
		<!-- OS information -->
		<text dy="2.4em">release: Ubuntu 9.10</text>
		<!-- CPU information  -->
		<text dy="3.6em">CPU: AMD Athlon(tm) Dual Core Processor 4850e</text>
		<!-- Kernel cmdline -->
		<text dy="4.8em">kernel options: root=UUID=84cadf52-515e-47d7-a0c7-a12bb53ea9a3 ro verbose vga=791 bootchart=svg </text>
		<!-- Boot time -->
		<text dy="6.0em">time: 1:03</text>
	</g>

```

The only problem I see is that some programs display the image differently.

I am pretty sure that no one is counting the 4-5 seconds that is being wasted on image conversion, but for a 10 sec goal this seems substantial.
The reason why I am posting this here is because I wanted to point out how to make it parsable.  This could be handy for trend analysis to look at boot times over the course of time.

---

### Post by Longinus00 on 2010-03-28
> **lavinog said:**
> Stuff about bootchart

Wrong thread?

---

### Post by lavinog on 2010-03-28
> **Longinus00 said:**
> Wrong thread?

It was to show how to do trend analysis for ureadahead.  Also to show how it can slow down the boot.
In hindsight I could have started a new thread and just linked it here.

---

### Post by k3lt01 on 2010-03-28
I don't think it's in the wrong place. Considering keybuk asked us to install bootchart some of us, like in my case at least in Lucid it wont work with bootchart, we may need an alternative.

---

### Post by bwallum on 2010-03-29
The -18 kernel update (just downloaded) causes my lucid system to hang on the os splash. Booting with the -17 kernel is ok.

Is this related to ureadahead? How do I get lucid to load on the -18 kernel?

EDIT
Now booting on -18 following further updates.

---

### Post by _h_ on 2010-03-29
Just curious about something, ureadhead creates a pack file on first boot that it uses to help speed boot, is there any way to forcefully make ureadhead wipe and recompile this boot pack at all?

---

### Post by Xorlathor on 2010-03-29
Thanks for sharing what ureadahead does! Well, I'm a newbie around here, and am very eager to learn more about Ubuntu and the boot process is part of that. Is ureadahead integrated in Lucid, or is it optional? How do I know if I have it installed? (I am indeed using the most updated version of Ubuntu 10.4, despite being rather new to Ubuntu)

And my basic idea of what ureadahead does: It grabs all the boot processes needed from my hard drive, and shoves it into RAM so it can be accessed faster and thus my computer can boot quicker.

---

### Post by farrell on 2010-03-29
> Is ureadahead integrated in Lucid, or is it optional? How do I know if I have it installed? (I am indeed using the most updated version of Ubuntu 10.4, despite being rather new to Ubuntu)

ureadahead is preinstalled in lucid and also in karmic (i think it came as update after karmic was released), so you should have it available already. You can check the status of the ureadahead package by typing:

```
dpkg --status ureadahead
```


> And my basic idea of what ureadahead does: It grabs all the boot processes needed from my hard drive, and shoves it into RAM so it can be accessed faster and thus my computer can boot quicker.

This is correct except for one word: ureadahead grabs all the boot FILES needed... This way, the boot processes can execute quickly.

---

### Post by lavinog on 2010-03-29
> **_h_ said:**
> Just curious about something, ureadhead creates a pack file on first boot that it uses to help speed boot, is there any way to forcefully make ureadhead wipe and recompile this boot pack at all?

Delete the pack files located in /var/lib/ureadahead/

---

### Post by _h_ on 2010-03-29
> **lavinog said:**
> Delete the pack files located in /var/lib/ureadahead/

Thanks. :popcorn:

---

### Post by ranch hand on 2010-03-29
OK, so I run the updates and install plymouth (uninstalled a couple days ago so that I could boot).

Boot into the OS, wait for it to be really working and reboot.  Shouldn't that second boot be faster?

It was 11 seconds slower (37, 48).

---

### Post by farrell on 2010-03-30
> **ranch hand said:**
> Boot into the OS, wait for it to be really working and reboot.  Shouldn't that second boot be faster?
It was 11 seconds slower (37, 48 ).

I have never seen ureadahead slowing down the boot, the second boot should have been faster. A bootchart would help here, does it work again for you? (Or am i mistaken that it was you who had problems with bootchart?)

Or maybe your box needs a reinstall? Although i can't explain why, a reinstall has cured more weirdness than applying all updates for me.

---

### Post by VMC on 2010-03-30
> **farrell said:**
> ... Although i can't explain why, a reinstall has cured more weirdness than applying all updates for me.

I have experienced this myself. Keeping updated and noticed several programs being held back, and then a re-install clears everything. Also it brings to the forefront any new problems that just an updated system doesn't show.

---

### Post by lavinog on 2010-03-30
> **ranch hand said:**
> OK, so I run the updates and install plymouth (uninstalled a couple days ago so that I could boot).

Boot into the OS, wait for it to be really working and reboot.  Shouldn't that second boot be faster?

It was 11 seconds slower (37, 48).

With all of the updates that have been occuring, it is possible that the system has become fragmented enough to slow it down (see earlier posts).
In which case a new install might help.

---

### Post by ranch hand on 2010-03-30
> **farrell said:**
> I have never seen ureadahead slowing down the boot, the second boot should have been faster. A bootchart would help here, does it work again for you? (Or am i mistaken that it was you who had problems with bootchart?)

Or maybe your box needs a reinstall? Although i can't explain why, a reinstall has cured more weirdness than applying all updates for me.
Yes, I have a lot of problems with bootchart.  In this installation it seems to work about all the time though.  I have another, the first one I upgraded from 9.10 to the tool chain, it doesn't work pretty much all the time.  The rest of them are in between those two extremes.

I am attaching .gz files of the two bootcharts in question.  I got thinking that maybe I did not let ureadahead finish before rebooting yesterday but when I booted this morning it came in at 50 seconds.

There are a couple of things that are going to make my boot slower than it could be.

A>Am booting from a dual drive external enclosure, USB type.

B>There are eleven OS' on this drive so things like blkid are going to take a bit longer as all are installed on 2 partitions with / on one drive and /home on the other.  There is also a formatted partition for back up files.

C>I never use auto login.  I do have a very short password that is the same for all the test installs and I am fast at getting it in so it should be very consistant from boot to boot.

I am not going to reinstall this installation as it is an upgrade 9.04>9.10>10.04.  I do have a clean install of 10.04 from the last ISO-testing issue of the B1 ISO (day before B1 was released).  Its bootchart worked on two out of three boots yesterday.  The last one came in at 30.46.

---

### Post by Starks on 2010-03-31
Am I supposed to get ureadahead status 4 during boot up?

---

### Post by lavinog on 2010-03-31
> **Starks said:**
> Am I supposed to get ureadahead status 4 during boot up?

Status 4 is normal.

---

### Post by rewolff on 2010-03-31
> **Ma****u said:**
> So you are saying anyone that can boot a live CD is able to get the file list of an encrypted home directory? I know this is far beyond the scope of this thread, but that's all but uninteresting. :p
You have to realize, that someone able to boot the live CD can also install a hardware or software keylogger to eventually access your encrypted partition. (or they can install a cronjob that checks for the mounted encrypted partition and Emails the files somewhere once it is...). 

There really isn't much you can do against someone who has access to the hardware let alone someone having "root" access to a machine. (which is practically equivalent).

---

### Post by rewolff on 2010-03-31
> **soul_rebel said:**
> 
I'll try with a semplified example scenario:
readahead reads files /1 /2 /3 /4
process 1 needs file /1 and so on. 4 processes in total.

The problem is that the data needed for "1" may be spread out between lots of 2, 3 and 4 files. Part of the speed that ureadahead achieves happens because it sorts all required disk-accesses so that the reads happen from beginning to end. So in fact, the files required for process 1 may be spread out: /1a /2 /1b /3 /1c /4 . 

When you do the math, statistically with more than 4 processes and files, it quickly becomes a very small advantage to start the processes earlier. 

A "cheap" thing to try anyway, may be to just start the readahead in the background. Any reference to say "1c" before the readahead is there will cause the readahead to become slower, but still be useful for everything that happens later. 

Worst case, the running boot processes will slow the readahead down so much that it becomes useless. We'll be back to the situation before ureadahead..... 

One thing I want to say though.... This pops up in a situation with RAID1, so I'll first explain it for RAID1, but later go back to where it is relevant for ureadahead....

Suppose I have a RAID1 over 4 drives. Each drive can handle 50Mb per second, the stripe size is 64k (not that it matters for a mirrored drive). 

How much performance can I get for linearly reading from the raid array? I have 4 disks, 50Mb /sec each, so 200Mb, right? Wrong! You request 1Mb, so the first drive will have to read the first and fifth 64k. These are spaced 5ms apart on this drive, so they are (likely) on the same track: A rotation takes 8.3ms on a 7200RPM drive. So to fetch both these 64k segments, the drive will have to read most, if not all of the track. As the track switch is synchronized with the last sector on the first track, even IF a track switch happens, it will still take 5ms to fetch the next 64k block. So even though you're reading from 4 drives each capable of 50M/sec, the total throughput will still be only 50Mb/sec!

Similarly, if ureadahead requires some blocks that have up to 1Mb of data in between that is not needed, it won't matter whether you request that data off the drive or not.

With speeds of up to 100Mb per second, modern drives store about 800kb per track. So only when you start skipping the read of more than about 1Mb between two segments that you need, a speedup is going to be noticed by NOT reading the part in between.

---

### Post by soul_rebel on 2010-03-31
> **rewolff said:**
> The problem is that the data needed for "1" may be spread out between lots of 2, 3 and 4 files. Part of the speed that ureadahead achieves happens because it sorts all required disk-accesses so that the reads happen from beginning to end. So in fact, the files required for process 1 may be spread out: /1a /2 /1b /3 /1c /4 . 

When you do the math, statistically with more than 4 processes and files, it quickly becomes a very small advantage to start the processes earlier. 
You are assuming that a process needs all its files togheter, while instead it needs them sequentially. So unless the first file needed by a process is the last one read by readahead, you still get an improvement as it start working on that file as soon as it is ready.

I also think that if in the future there will be some sort of "defragmenting" or packing of boot files, the improvement could be close to the situation of my theoretical example.

> **rewolff said:**
> 
Worst case, the running boot processes will slow the readahead down so much that it becomes useless. We'll be back to the situation before ureadahead..... 

readahead is given realtime priority, so it is never slowed down by other processes.

The more I think of this, the more it makes sense, at least in theory of course :-) I hope someone sees it too.

---

### Post by conorsulli on 2010-03-31
Ah!I was getting the status 4 message every time so as I had my /home partition separate on my hdd. 

Thanks for clearing it up!

---

### Post by pe1dnn on 2010-04-01
I wonder what is wrong with my system, a Fujitsu Siemens C1020 laptop. Old but the times I see are much higher than others I saw in this thread.

Here is when ureadahead is colleciting [http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-4.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-4.png)

This is on the subsequent boot: [http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-5.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-5.png)

So ureadahead takes about 30 seconds. So I'm a long way from the 10 seconds goal an will most likely never reach it. But 30 seconds is way more than the 3 seconds I saw in other pictures. Any ideas?

The system is upgraded from 9.10 to the current 10.04. The first picture is actually from booting after installing todays updates, not because I dumped the pack.

I guess my drives are slow but if I look at the second picture I see disk activity all the way during the ureadahead period but not throughput all the time, so will that be seek time? I don't think I can get the random group of files that ureadahead read sequentially on disk without gaps. That would help, at least so it seems through my layman's eyes.

The filesystem is ext4 now, but only recently converted from ext3. Should that become better over time after the files have been refresh and take advantage of ext4.

So am I doing something wrong or is it just because of old hardware? As it is now with or without ureadahead does not make much of a difference.

Any thoughts about the?

Regards, Henk.

---

### Post by ranch hand on 2010-04-01
Remember that the 10 second target is set for a mini computer running an atom processor and using a SHH drive and auto login.

If you are on an older box you may not even be running a 7200rpm HDD (probably not).  This makes a big difference.

My box does have 7200rpm HDDs in it and I am getting (when plymouth works) in the 30 to 40 second range with password login.  This is from grub to usable desktop.  I do not think that is really too bad.

I also expect it to get better as the devs straighten out plymouth.

---

### Post by farrell on 2010-04-01
> **pe1dnn said:**
> So ureadahead takes about 30 seconds. So I'm a long way from the 10 seconds goal an will most likely never reach it. But 30 seconds is way more than the 3 seconds I saw in other pictures. Any ideas?

I also suspect your HDD to be the bottleneck. If you don't want to change it, you can check the fragmentation and maybe reinstall or defrag with e4defrag (which is not yet stable). You can check the fragmentation of your file system by booting from a live-cd/usb and running the folloing on the UNMOUNTED partition:

```
sudo fsck.ext4 -fv UUID=5b4ecd6b-6611-4bd4-89de-b5693f572bfb
```> **ranch hand said:**
> I am not going to reinstall this installation as it is an upgrade 9.04>9.10>10.04. I do have a clean install of 10.04 from the last ISO-testing issue of the B1 ISO (day before B1 was released). Its bootchart worked on two out of three boots yesterday. The last one came in at 30.46.

Good to see someone looking at these test cases! The things you mentioned that may slow down your boot shouldn't be too much of an issue. Maybe the additional 20 seconds can be attributed to the upgrading from 9.04...

---

### Post by ranch hand on 2010-04-01
The most interesting install that I have is a 9.10>10.04 upgrade from the time of the tool chain.  Only a few problems with it.

When all my installs (all on the same drive) and most other ATI users were unable to boot, that one never even blinked.  I figure some thing is wrong with it and can stay that way.

It is not the one I use the most but it is my main back up and has been used as my production OS for probably a quarter of this testing cycle when nothing else would work.  It is really my favorite Lizard (10.04 = Lounge Lizard).

It boots very evenly in the 30s and I am happy with that.  Boot chart went in early in the cycle and has been removed, purged, sworn at and finally just ignored because it just will not work.  It did work once in all this time.

I really do not think that the boot needs to be a lot faster than this.  Heck, I smoke  and roll my own.  With 9.04 I can hit enter on the grub menu and have one built before I need to login.  With this here new fangled system I haven't the time to do that.

Probably better for me health wise.

---

### Post by lavinog on 2010-04-01
> **pe1dnn said:**
> 
The filesystem is ext4 now, but only recently converted from ext3. Should that become better over time after the files have been refresh and take advantage of ext4.

Somewhere it was mentioned that upgrading an ext3 partition to ext4 will not get the full benefit of being ext4.
I am looking for the source, but what you should do is a fresh install if you want the speed.
Edit: This wasn't the source I was looking for but he pretty much says the same thing here:
[http://www.linux-mag.com/id/7272/1/](http://www.linux-mag.com/id/7272/1/)
> 
One of our primary design goals was that it should be painlessly easy to upgrade from ext3 to ext4. You might not get all of the benefits of ext4 unless you do a backup/reformat/restore of your filesystem, but you would get at least some of the benefits by simply remounting the filesystem using ext4 and enabling some of ext4&#8217;s features.


Shrink your existing partitions, and create new ones, install, then copy your files back. (This also helps clean out trash you didn't know existed.)

---

### Post by lavinog on 2010-04-01
> **ranch hand said:**
>  With this here new fangled system I haven't the time to do that.

Probably better for me health wise.

Ubuntu, It saves lives.

---

### Post by pe1dnn on 2010-04-02
Thanks for the replies. Since this is not a production system with lots of extra packages but rather plain installation I think the most sense makes a reinstallation first before trying to fix it another way like defragging. The Beta1 disk is booting as we speak. I'll let you know if it made a difference.

---

### Post by pe1dnn on 2010-04-02
Okay, I installed Ubuntu 10.04 B1 fresh, updated it up to today and ran the boot test again.

When ureadahead is learning (I removed the pack):

[http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100402-3.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100402-3.png)

And after 3 more reboots:

[http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100402-6.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100402-6.png)

So 1:10 minute without and 50 seconds with ureadahead assistence. So it saves me 20 seconds and the fresh installed 10.04 B1 on ext4 seems about 8 seconds faster compared to the old upgraded 9.10 to 10.04 and the converted ext3 file system. The filesystem is 4 Gb so it does not have to seek far on the 40 GB drive. Since the PC has 1 GB ram, no time is lost on writing the swap partition.

It looks like the "slow" boot is really due to the HD (Fujitsu MHT2040AT 40 GB 2.5 ATA). Its not 7200 not even a 5400 but a 4200 rpm disk. I'm not get a new one on this laptop, it's a 2.5 inch PATA disk and I think there is not a store in my town any more that has these drives and even if, it is unlikely that they will be much faster anyway.

So unless the files ureadahead needs get in a contiguous space on disk somehow to avoid seeks so it can keep reading, there doesn't seem to be much hope to get it any faster.

The only improvement I see technically is that during ureadahead boot processing could already start using the files ureadahead already fetched instead of waiting until ureadahead read all the data from disk. Worst case it would be the same if the last file read is the first file needed but otherwise this would speed up the process more especially if files needed first are early in the ureadahead's store. But this was already mentioned earlier in the thread.

Another option would be if ureadahead not only remembers which files to load but also keep the data in a large contiguous file and use that instead of the files scattered on the disk. But of course that would introduce the security risk mentioned before.

I read somewhere that removing the hal package also saves a little but I don't know if it is still the case with 10.04 B1.

---

### Post by lavinog on 2010-04-02
The drive could also be getting some read errors (look at the SMART data in the disk utility)
The read errors are corrected transparently by the hd firmware, but the process can slow things down.
4200 rpm is quite slow, but I beleive 40g drives were last used in laptops over 3 years ago.

> it's a 2.5 inch PATA disk and I think there is not a store in my town any more that has these drives and even if, it is unlikely that they will be much faster anyway.

[NEWEGG: Western Digital Scorpio Blue WD800BEVE 80GB 5400 RPM 8MB Cache 2.5" ATA-6 Notebook Hard Drive -Bare Drive: $49.99 ](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136129)

---

### Post by runesvend on 2010-04-08
I'm very interested in how ureadahead improves performance on SSDs. Have any benchmarks been done on this?

I understand the reasoning behind reducing seek times on a regular HDD, where we know that physically - on the disk platter - LBA=1000 comes after LBA=999 and after that comes LBA=1001.
But as I understand it, with SSDs, the LBA doesn't correspond to any physical location on the SSD, it merely points to the same *data*, not the same physical location. As I have understood it, because of the necessary wear-levelling algorithms in SSDs, when I edit a text file and save it, the SSD will save the text file's data to a new cell on the SSD, and delete the text file's data from the old cell on the disk. The LBA will, of course, remain the same, so the OS can say "give me LBA=26383" and still get the same text file. But the data itself will have moved to a completely different place physically on the disk.

How can ureadahead be useful for anything in this context? As far as I have understood, the only software in the computer that actually knows the physical location of the data on an SSD is the controller's firmware in the SSD.

I don't get any performance gain on my SSD with ureadahead either (mind you, i get 5-6 second boot times, so perhaps there isn't much to improve). But it's more or less the same. Sometimes half a second slower, sometimes half a second faster, and seemingly totally unrelated to ureadahead being enabled.

Can anyone clear this up?
As far as I know, all SSDs implement wear-levelling algorithms, right?

---

### Post by a-user on 2010-04-08
well, if i remember right the answer to your question is given by NCQ and or the controler of the ssd. when there are many read commands for the ssd the controller itself tries to remix the order for optimal access and read speed.

now, ureadahead does not know the physical position but because it inserts all commands one after the other teh controller can arrange them in optimal order.

wihtout ureadahead the time gap between to orders would be to big for that. when the second command arrives the first is already in progress and thus the order cannot be swaped if it would have been better.

well, i'm not an expert on this, but i think i'm quite close to the correct answer.

---

### Post by MacUntu on 2010-04-08
Also note that with SSDs ureadahead runs in the background. If it reads the block before it's needed -> good, else there's no penalty. That's why files are sorted by access times for SSDs (AFAIK).

---

### Post by a-user on 2010-04-08
oh that's an interesting additional info. thx.

---

### Post by lavinog on 2010-04-08
> **a-user said:**
> well, if i remember right the answer to your question is given by NCQ and or the controler of the ssd. when there are many read commands for the ssd the controller itself tries to remix the order for optimal access and read speed.

now, ureadahead does not know the physical position but because it inserts all commands one after the other teh controller can arrange them in optimal order.

wihtout ureadahead the time gap between to orders would be to big for that. when the second command arrives the first is already in progress and thus the order cannot be swaped if it would have been better.

well, i'm not an expert on this, but i think i'm quite close to the correct answer.
Should ureadahead be sorting any information then if NCQ is rearranging it in its own way?
The sort is done during the profile, but what if sorting is preventing NCQ from working efficiently (looking at NCQ for rotational drives, it almost seems that NCQ isn't needed for sequential data)

---

### Post by k3lt01 on 2010-04-08
Keybuk has been working hard, He updated my bug report and also updated others I see. Apparently a fix is coming through to lesson the memory footprint, whether or not it is ureadahead or the kernel I don't know maybe someone else with more knowledge can clear this up for me. I'm reluctant to  re-install ureadahead (yes I removed it again because it, or the kernel?, just kept crippling my machine nearly very update) until the fix is released.

---

### Post by lavinog on 2010-04-08
> **k3lt01 said:**
> Keybuk has been working hard, He updated my bug report and also updated others I see. Apparently a fix is coming through to lesson the memory footprint, whether or not it is ureadahead or the kernel I don't know maybe someone else with more knowledge can clear this up for me. I'm reluctant to  re-install ureadahead (yes I removed it again because it, or the kernel?, just kept crippling my machine nearly very update) until the fix is released.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
The following could be used to recover your memory until a fix is released:
```

echo 2048|sudo tee /sys/kernel/debug/tracing/buffer_size_kb

```

---

### Post by ShadowDragon on 2010-04-08
> **lavinog said:**
> Should ureadahead be sorting any information then if NCQ is rearranging it in its own way?
The sort is done during the profile, but what if sorting is preventing NCQ from working efficiently (looking at NCQ for rotational drives, it almost seems that NCQ isn't needed for sequential data)
Problem with NCQ is that it only has a queue size of 32... That why we also use I/O Schedulers with sorting algorithms.

---

### Post by k3lt01 on 2010-04-08
> **lavinog said:**
> [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
The following could be used to recover your memory until a fix is released:
```

echo 2048|sudo tee /sys/kernel/debug/tracing/buffer_size_kb

``` Shall try this now in Karmic and get back to you as soon as I can. I'll then try it in Lucid.

---

### Post by k3lt01 on 2010-04-09
That didn't work Lavinog. 51 minutes to get to a usable stage, not the slowest but certainly getting up there.

Unless there is something else to try I'll remove ureadahead again until the next kernel and/or ureadahead update.

---

### Post by lavinog on 2010-04-09
What do the different symbols mean when doing a ureadahead --dump ?
```

/usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so (38 kB), 1 blocks (40 kB)
  [@#########                                                                ]

        0, 40960 bytes (at 2428284928)

/usr/bin/net (5949 kB), 7 blocks (2284 kB)

  [@#########################################################################]
  [##########################################################################]
  [######################################################....................]
  [..........................................................................]
  [..........................................................................]
  [..........................................................................]
  [.......@##################################################################]
  [####......................................................................]
  [..........................................................................]
  [..........................................................................]
  [..........................................................................]
  [..........................................................................]
  [..........................................................................]
  [..........................................................................]
  [..............................................................@###########]
  [####################......................................................]
  [.@###############################....................@####################]
  [##########################################################################]
  [##################################################################......@#]
  [######################################################...........@########]
  [########                                                                  ]

        0, 827392 bytes (at 3519836160)
        1847296, 290816 bytes (at 3521683456)
        4497408, 131072 bytes (at 3524333568)
        4853760, 131072 bytes (at 3524689920)
        5066752, 659456 bytes (at 3524902912)
        5750784, 229376 bytes (at 3525586944)
        6025216, 69632 bytes (at 3525861376)


```

edit:
Is ureadahead reading the py files and the pyc files or just checking the metadata of the py files?
It would seem wasteful to read both the source and the compiled file.

```

/usr/lib/python2.6/subprocess.py (45 kB), 0 blocks (0 kB)
  [............                                                              ]


/usr/lib/python2.6/subprocess.pyc (33 kB), 1 blocks (36 kB)
  [@########                                                                 ]

        0, 36864 bytes (at 2873835520)

```

---

### Post by runesvend on 2010-04-09
Thanks for your explanations a-user and MacUntu, that makes a lot of sense. I hadn't thought of that.

It'd be cool if Intel opened up their drives a bit, so the boot time could be improved even more. I can't see how it could hurt Intel if they made available the physical locations of LBAs, through some form of API. It's kind of hard to optimize anything with a black box like that.

---

### Post by lavinog on 2010-04-09
Why are /var/log files in the pack file?
I don't see any need to read them in?  Especially since there have been some cases where log files can become huge.

EDIT: Filed bug report: [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/559525](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/559525)

---

### Post by Artemis3 on 2010-04-11
Well, so far bootchart shows my best lucid boot time is 56s and the same machine with jaunty one week ago was 46s.

---

### Post by lavinog on 2010-04-11
> **Artemis3 said:**
> Well, so far bootchart shows my best lucid boot time is 56s and the same machine with jaunty one week ago was 46s.

I don't recall if bootchart in jaunty includes the time to show the desktop.
Can you post the two bootcharts?

---

### Post by Artemis3 on 2010-04-13
Here you go: 46secs jaunty vs. 68secs lucid.

---

### Post by Artemis3 on 2010-04-13
I just upgraded packages and rebooted twice, here is the last one: 55secs.

I don't even have apache2 running because of the [gallery2 bug](https://bugs.launchpad.net/ubuntu/+source/gallery2/+bug/558961). And removed privoxy because polipo is doing the job now ^_^

---

### Post by lavinog on 2010-04-13
> **Artemis3 said:**
> I just upgraded packages and rebooted twice, here is the last one: 55secs.

I don't even have apache2 running because of the [gallery2 bug](https://bugs.launchpad.net/ubuntu/+source/gallery2/+bug/558961). And removed privoxy because polipo is doing the job now ^_^

Your bootchart from jaunty stops once gdm is loaded.
The bootchart for karmic and lucid stops once the user is logged in...so that is majority of the difference.

I also see about 5 secs of activity from ck-history...I am not sure what that is.  I don't see it on any of my systems.  I did find this bug report though: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/400863](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/400863)
Did you update to lucid or fresh install?
It looks like the read rate on your drive improved substantially.

Also are you logging in automatically?...it looks like there is about 7 seconds of dead time.

EDIT:
It looks like your lucid machine is finishing its startup scripts at about 37 seconds Which would be about 9 seconds faster than jaunty.

It looks like you have some non-standard programs installed (apache2, mysql, winbind, exim4, polipo, icecast, tor, noip)
It is taking ureadahead about 25 secs to read all of the data.

---

### Post by Artemis3 on 2010-04-13
Its an upgrade, not fresh install. Also, log in is not automatic, we can subtract those 7 secs ^_^

Is it still possible to use "profile" as kernel option at grub? Does it collide with ureadahead?

Also, in Jaunty, my boot time used to be around 2 to 3 minutes, until it occurred me to turn off bluetooth in the bios (i don't have any bluetooth devices). I wonder what will happen if i turn it back on now? 

Interesting bug about the ConsoleKit history log, Mine is just 64M long :)

---

### Post by lavinog on 2010-04-13
> **Artemis3 said:**
> 
Is it still possible to use "profile" as kernel option at grub? Does it collide with ureadahead?


you can reprofile by removing the pack files in /var/lib/ureadahead and rebooting.

---

### Post by rudihawk on 2010-04-19
> **Jay_Bee said:**
> Hi keybuk,
I don't have a problem with ureadahead I just want to thank you for this very interesting and informative post :)

+1 

Thanks for that, that was really interesting!

---

### Post by P4man on 2010-04-20
> **pe1dnn said:**
> I wonder what is wrong with my system, a Fujitsu Siemens C1020 laptop. Old but the times I see are much higher than others I saw in this thread.

Here is when ureadahead is colleciting [http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-4.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-4.png)

This is on the subsequent boot: [http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-5.png](http://dl.dropbox.com/u/5330132/Fujitsu-lucid-20100401-5.png)

Your disk throughput is really very low. I have an old laptop here (Dell D600) with an antique 40GB 4200rpm  drive, and I get 28MB/s throughput where you only get half that.

If its not a hardware problem, then maybe its because you converted the filesystem from Ext3 to Ext4 which iirc, doesnt give you any of the speedups of Ext4.

---

### Post by k3lt01 on 2010-04-20
Just thought I'd let you know my laptop must have just broken a record for how long it took. Over 2 hours and I had to turn it off (hadn't finished yet either) and boot back into Karmic (my karmic install doesn't have ureadahead anymore) so I could get some work done.

---

### Post by ranch hand on 2010-04-20
> **k3lt01 said:**
> Just thought I'd let you know my laptop must have just broken a record for how long it took. Over 2 hours and I had to turn it off (hadn't finished yet either) and boot back into Karmic (my karmic install doesn't have ureadahead anymore) so I could get some work done.
Congratulations.  Quite an achievement.

---

### Post by UpSignal on 2010-04-20
guys, i'm sorry to ask this here, but, if indeed some files do fragment in linux, what program can i use do do a disk defrag? everyplace i search on google, there's a guy saying "nah, linux never fragments, you don't need one". 
:s

---

### Post by k3lt01 on 2010-04-20
> **UpSignal said:**
> guys, i'm sorry to ask this here, but, if indeed some files do fragment in linux, what program can i use do do a disk defrag? everyplace i search on google, there's a guy saying "nah, linux never fragments, you don't need one". 
:sThere are umpteen (that means alot of) threads on this issue. Try the search function within the forum itself.

I myself don't know why people get worked up about this simply because it isn't the issue it is in Windows. Yes Linux fragments but no where near the amount Windows does. Furthermore if you do a clean install and then replace your files from a backup there will be minimal (if any) fragmentation.

---

### Post by lavinog on 2010-04-21
There is a sort of rule of thumb that once you have less than 10% free space, fragmentation quickly becomes an issue.
For users with small partitions or small drives this can become an issue quickly.

If you read some of the earlier posts on this thread there are a couple of solutions, but currently the ext4 defrag program is not ready yet.

There is a program called filefrag that can give you an idea on how fragmented a file is.
I assume that dumping the ureadahead pack files can give the same info for boot files.

---

### Post by P4man on 2010-04-21
> **lavinog said:**
> There is a sort of rule of thumb that once you have less than 10% free space, fragmentation quickly becomes an issue.
For users with small partitions or small drives this can become an issue quickly.

Isnt 5 or 10% of your Ext partition actually reserved for this very reason? IIRC you can not fill an Ext4 partition to its full, well, capacity.

---

### Post by ShadowDragon on 2010-04-21
Yup.

Quote: Manpage of tune2fs
```
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by  privileged  processes.   Reserving some number of filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem  fragmentation,  and  to  allow system daemons, such as sys&#8208;
              logd(8), to continue to function correctly after  non-privileged
              processes  are  prevented  from writing to the filesystem.  Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.
```

---

### Post by Longinus00 on 2010-04-21
Fragmentation is more complicated than just file fragmentation. Even if all the files on your drive are fragment free the actual files can still be scattered all over your disk. This can slow down loading even more than file fragmentation might. I don't know if ext4 has any improvements over ext3 to improve locality of reference.

---

### Post by ranch hand on 2010-04-21
> **Longinus00 said:**
> Fragmentation is more complicated than just file fragmentation. Even if all the files on your drive are fragment free the actual files can still be scattered all over your disk. This can slow down loading even more than file fragmentation might. I don't know if ext4 has any improvements over ext3 to improve locality of reference.
Yes it does because of the larger block size.  This keeps files closer together.

---

### Post by ShadowDragon on 2010-04-26
Could it be that ureadahead presumes that the data must be fetched from /dev/sda, while the bootdisk could be /dev/sdb?

> **jocko said:**
> Thanks for the hint. That was not the problem (cat /sys/block/sd*/queue/rotational said "0", so it was properly detected as a SSD), but it got me thinking:

I had a rotational hard drive as /dev/sda and the SSD as /dev/sdb, so I just switched the sata cables around to make the SSD become /dev/sda, and now ureadahead behaves properly and makes it [boot in less than 6 seconds]("http://img717.imageshack.us/i/jockodesktoplucid201004.png/")!

---

### Post by Longinus00 on 2010-04-26
> **ranch hand said:**
> Yes it does because of the larger block size.  This keeps files closer together.

Block size is independent of ext3/4. You can have an ext4 partition with a smaller block size than an ext3 partition. Larger block sizes would also hurt locality of reference for many small files.

---

