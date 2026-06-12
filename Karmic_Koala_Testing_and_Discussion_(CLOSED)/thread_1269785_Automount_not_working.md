---
title: "Automount not working"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2009-09-18
If I insets a DVD into one of my drives it does not automount like januty does. With no dvd or cd in my two drives both are displayed when I click on the computer icon. If I insert a dvd into one of the drives the icon disappears. On jaunty it would display the name of the dvd or cd. Anyone else seeing this?

Bill

---

### Post by steeleyuk on 2009-09-18
I've had this happening today on a fresh install. It happens with a data CD as well. The only exception is audio CDs which seem to work fine.

---

### Post by tlois on 2009-09-18
Same here.  Had just gotten an external cd/dvd drive that worked 30 mins ago, but after update, it is not there.  Oddly, when i open the media file, the contents of the cd is in a separate file there, not as a cd image, but a file, and i can't open it.

---

### Post by ace214 on 2009-09-18
I have also experienced this. I am able to play my DVD in VLC, but it's jumpy (every few seconds, the play speed will increase for about 1 second and then return to normal).

In the Disk Utility (under System->Administration) it shows my disks as being not partitioned and an "Unrecognized" file system type.

File a bug?

---

### Post by sparker256 on 2009-09-19
> **ace214 said:**
> I have also experienced this. I am able to play my DVD in VLC, but it's jumpy (every few seconds, the play speed will increase for about 1 second and then return to normal).

In the Disk Utility (under System->Administration) it shows my disks as being not partitioned and an "Unrecognized" file system type.

File a bug?

Not sure what to file it against but I think this is a bug.

Bill

---

### Post by mc4man on 2009-09-19
Noticed the same on a fresh a6 install, filed a bug though somewhat difficult to document - nothing happens nor is anything reported (other than the cdrom icon disappearing.

If you see the same then maybe add here to confirm

(am thinking it may be related to the udev testing, maybe not

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150)

---

### Post by moviemaniac on 2009-09-19
> **mc4man said:**
> (am thinking it may be related to the udev testing, maybe not

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150)

Should be a duplicate of [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/430605](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/430605)

which might be due to the transition to udev.

//edit: VLC and other applications work just fine when you point them to /dev/sr0 (or whatever your drive is)

---

### Post by mc4man on 2009-09-19
> Should be a duplicate of

Saw that but wasn't sure, I'm finding that ALL disks that have a  mountable file-system will fail to automount
The obvious exceptions being blank media and audio cd's

as noted most players can access thru the device rather than the non-existent mount-point, either from gui or cli

Though not a factor for this I'm also finding that in systems with 2 cd/dvd drives only the boot drive (sr0) is being written to fstab.
Both drives though will have entries in /etc/udev/rules.d/70-persistent-cd.rules


Edit: I tend to think this will be squared away in the near future

---

### Post by moviemaniac on 2009-09-19
Yeah, I can confirm that, I've tried many, many CD's and DVDs today and not a single one mounted - except audio CDs. 

and yes, I also only have one drive in my fstab (actually, there are both in it, but they're pointing to the same physical drive for the different mount points...) and both have entries in /etc/udev/rules.d/70-persistent-cd.rules as you mentioned.

I have a feeling this is because hal is being deprecated and udev hasn't taken over fully yet, so I too expect ths to go away soon with new udev packages. Makes me think we should also file the bug against udev to make sure it gets noticed by the right developers?

---

### Post by mc4man on 2009-09-19
> Makes me think we should also file the bug....

It already got marked as a dup of the one in dev so time will tell, though can't imagine it won't be fixed

---

### Post by novafluxx on 2009-09-19
So how can I mount a disc manually then, never had to do it before and I've got no clue!? I'm trying to install Virtual Box Additions (I run Ubuntu alpha's in VB under Windows, and actually install them to my laptop):confused:


EDIT: OK, so I decided to just try "mount /dev/sr0" and it put it on my desktop, bingo!

---

### Post by VMC on 2009-09-19
> **novafluxx said:**
> So how can I mount a disc manually then, never had to do it before and I've got no clue!? I'm trying to install Virtual Box Additions (I run Ubuntu alpha's in VB under Windows, and actually install them to my laptop):confused:


EDIT: OK, so I decided to just try "mount /dev/sr0" and it put it on my desktop, bingo!

This works for me. ```
mount -t iso9660 -o ro /dev/cdrom /cdrom
sudo umount /cdrom
```

---

### Post by novafluxx on 2009-09-19
Is this a known bug? If not, has anyone filed it?

---

### Post by moviemaniac on 2009-09-20
> **novafluxx said:**
> Is this a known bug? If not, has anyone filed it?
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/430605](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/430605)

---

### Post by n3had on 2009-09-20
ah i thought i am the only one facing it

---

### Post by sparker256 on 2009-09-21
It look like it has been fixed with todays updates.

Bill

---

### Post by oboedad55 on 2009-09-21
> **sparker256 said:**
> It look like it has been fixed with todays updates.

Bill

Monday, Sept. 21, 8:30 pm, looks like the automount is indeed fixed with recent updates. Hallelujah!

---

### Post by novafluxx on 2009-09-21
Hooray! Karmic is coming along quite nicely!

Change the thread title to SOLVED ;-)

---

### Post by oboedad55 on 2009-09-21
> **novafluxx said:**
> Hooray! Karmic is coming along quite nicely!

Change the thread title to SOLVED ;-)

There, how's that? :P

---

### Post by novafluxx on 2009-09-21
> **oboedad55 said:**
> There, how's that? :P

LOL Has to be done by OP using Thread Tools :) but nice work :-D

---

### Post by oboedad55 on 2009-09-21
> **novafluxx said:**
> LOL Has to be done by OP using Thread Tools :) but nice work :-D

Thank you very much, [bowing humbly]. I learned something today! I've only been here about three years. I guess I never solved anything... :(

---

### Post by novafluxx on 2009-09-21
I just learned it in the past few days myself

---

### Post by oboedad55 on 2009-09-21
> **novafluxx said:**
> I just learned it in the past few days myself

I was wondering where the "solved" button was... Well, maybe someone will see my sterling addition and figure it out. Or the OP can come back and fix it up proper like.

---

### Post by blakamin on 2009-09-29
Broken again:confused:

---

### Post by oboedad55 on 2009-09-29
> **blakamin said:**
> Broken again:confused:

New updates cause it? I'm still having trouble playing music files. CDs don't work nor do files played in Rhythmbox. I;ve tried other players to no avail.

---

### Post by blakamin on 2009-09-29
Cant even mount unless I reboot with a disc in there.

---

### Post by mc4man on 2009-09-30
This issue as been marked on launchpad as low importance so maybe it'll be fixed at some point, maybe it will be fixed inadvertantly,

What's interesting is that (at least here), it all centers around libbrasero-media0, which was updated to fix gksu nautilus at which point the cd/dvd drive became fully borked as described here.

As a bit of an experiment reverted libbrasero..., and brasero back to the last version.

Now my cd/dvd drives work perfectly, media automounts, no locked drives, ect. and gksu nautilus also works fine. ( it is better to run gksu nautilus from Alt+F2, but also works from terminal

The only caveat is to not run gksu ... when the cd/dvd drive is in an 'open' state.

Otherwise perfect in all regards

( not a solution, just an observation

---

### Post by oboedad55 on 2009-09-30
> **mc4man said:**
> This issue as been marked on launchpad as low importance so maybe it'll be fixed at some point, maybe it will be fixed inadvertantly,

What's interesting is that (at least here), it all centers around libbrasero-media0, which was updated to fix gksu nautilus at which point the cd/dvd drive became fully borked as described here.

As a bit of an experiment reverted libbrasero..., and brasero back to the last version.

Now my cd/dvd drives work perfectly, media automounts, no locked drives, ect. and gksu nautilus also works fine. ( it is better to run gksu nautilus from Alt+F2, but also works from terminal

The only caveat is to not run gksu ... when the cd/dvd drive is in an 'open' state.

Otherwise perfect in all regards

( not a solution, just an observation

Do your audio CDx work? Mine haven't worked at all in karmic, nor any other music files.

---

### Post by mc4man on 2009-09-30
> Do your audio CDx work

audio cd's work fine both in my slightly modded install and in the testing. (atm with the reverted brasero 

What doesn't work is 2 players, rhythmbox and banshee
Rhythmbox not at all, banshee fails to get metadata but can extract and also play if the tracks are loaded from ~/.gvfs/cdda mount on scdX

In the tester -  amarok2, vlc and audacious2 work fine, amarok and aud2 get metadata, the repo vlc doesn't

In the working - amarok 1.4, vlc, and audacious2 work perfectly, retrieving album, track info. Also I've set both amarok 1.4 and aud2 to autorun/autoplay  cd's from both drives, works great.

edit: 
I've found that autorun/autoplay of audio cd's is best done thru a script as a 'launch command' rather than using the players default one, particularly with multiple drives (internal and external

---

### Post by moviemaniac on 2009-10-01
well f*** me! I just reverted back to the previous versions of brasero and libbrasero-media0 (THANKS, mac4man!), rebooted and DVD playback is back - both in VLC and SMplayer. Didn't try Audio-CDs though, but that's what I have my standalone CD-player for :D

---

### Post by isecore on 2009-10-01
How can CD/DVD-drives not mounting be of "low importance"??? 

What's next, when harddrives no longer mount on boot, is it going to be "low importance" on fixing that?

I admit that I don't really use discs that often, but it's still fairly important that it works for the average user, and not forcing them into the terminal everytime they want to watch a DVD or whatever.

---

### Post by moviemaniac on 2009-10-01
I filed a bug against the brasero-package which is the root of the problems - please mark it as affecting you so it gets the proper attention: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/439846](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/439846)

---

### Post by mc4man on 2009-10-01
your bug report about this have been marked as a dup of the orig (by philinux) and that one now has a status of high. So I'd expect a proper fix to be coming at some point sooner than later

To track
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065)

---

