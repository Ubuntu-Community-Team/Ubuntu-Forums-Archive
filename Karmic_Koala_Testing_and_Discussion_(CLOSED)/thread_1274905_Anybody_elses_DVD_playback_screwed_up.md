---
title: "Anybody elses DVD playback screwed up?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2009-09-25
Hi guys,

yesterday I popped one of my CSI 9 DVDs in the drive to continue watching the series but Totem, (S)Mplayer and VLC all refused to play them spitting out libdvdread errors. It's not the DVD as others fail too (some work, though). I suspect one of the updates I did before shutting down the machine two days ago screwed it up.
Anybody else affected by this?

---

### Post by jonolumb on 2009-09-26
I too am having trouble with DVD playback - sometimes I can watch the start of a DVD but I normally get libdvdread errors about half way through and can't watch the rest.

It seems that DVD ripping is not working very well either...

---

### Post by amano on 2009-09-26
*Sigh* It seems that playing DVDs will remain a neverending story. I hope that this can be sorted out. Anybody mind filing a bug?

---

### Post by moviemaniac on 2009-09-26
I found out it was actually my fault that I screwed up my DVD-playback. I had the same problem like you - some titles would play, some not, sometimes it would crash in the middle or only play select episodes from one DVD.
My problem was - as I found out after quite some headscratching and recompiling stuff: I installed a folder with a bunch of selected debs using dpkg -i *.deb a few days ago but an old libdvdcss2 slipped in which subsequently caused many playback problems. After discovering this I updated to the latest version from Medibuntu.org, rebooted (yes, you've gotta do that for some reson...) and it worked like a charm again.

---

### Post by mc4man on 2009-09-26
One thing I have noticed is some unexpected failures to crack on the keys on some dvd's. This has mainly occurred when using sr0, and only on a small number of disks.

The best solution ( and generally a good first step when having playback issues) is,** after a disk as been inserted**, to open the .dvdcss folder in home, find the folder matching the volume label of the disk and delete it.
Then try the player again.

If still no good or parts of the dvd won't play then again **delete the folder** and start a player such as vlc using a different key extraction method, ( the default is disc(player) key.
```

export DVDCSS_METHOD=title && vlc dvd://
```
or if not on the sr0 drive
```
export DVDCSS_METHOD=title && vlc
```
Then open from media -> disk

This was mainly a few days ago with the on and off detection and mounting of udf volumes

The reason for deleting the folder is that by default all players look to the .dvdcss folder first, if a matching volume label folder is found then the keys inside will be used whether correct or not, complete or not

---

### Post by moviemaniac on 2009-09-26
thanks, mc4man, I've gotta remember that one just in case!

---

### Post by kansasnoob on 2009-09-26
totem-xine seems to work OK here.

VLC not so much.

---

### Post by mc4man on 2009-09-26
> VLC not so much. 

Maybe take a look at what vlc -vv produces

Because it can be a lot sometimes better to output to a file

```
vlc -vv > vlc_output.log 2>&1
```

or if on sr0
```
vlc -vv dvd:// > vlc_output.log
```

Totem-xine uses it's own version of libdvdnav, one of the reasons it's a shame they removed it (I built totem-xine 2.26.x so it packaged as 2.28 and replaces the  current transitional one 

................................................................

If libdvdcss is suspected ( though probably not the case here ) a dvdcss debug can be added ( more useful if the title's folder in .dvdcss is deleted, or .dvdcss itself



```
export DVDCSS_VERBOSE=2 && vlc -vv dvd:// > vlc_output.log 2>&1


```

or an all in one with title method (again best with no existing folder in .dvdcss

```
export DVDCSS_VERBOSE=2 && export DVDCSS_METHOD=title && vlc -vv dvd:// > vlc_output.log 2>&1
```

Edit: on my testing install have left everything alone, on my working install have gotten sick of inconsistencies concerning /dev/sr0 ( drive locked every once and a while) and have now dumped libbrasero-media0 for the moment

---

### Post by jonolumb on 2009-09-27
I am currently running Ubuntu Karmic Alpha 6 and was having a few problems yesterday - however, an "sudo apt-get update && sudo apt-get upgrade" downloaded and installed an updated version of libdvdcss2 from the medibuntu repositories which seems to have fixed everything - DVD playback and Ripping is now working as it should.

---

### Post by Nullack on 2009-09-27
resindvd has never really worked. libdvdnav is better but it aint feature complete.

---

### Post by philinux on 2009-09-27
Put dvd in and nothing mounted on desktop or under places. Totem crashed and vlc spit this out 
```
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

```

Also eject button does not work. :confused:

---

### Post by amano on 2009-09-27
> **kansasnoob said:**
> totem-xine seems to work OK here.

Totem-xine? I thought that Totem completely dropped the xine backend...

Or do you mean Totem-gstreamer?

---

### Post by philinux on 2009-09-27
> **amano said:**
> Totem-xine? I thought that Totem completely dropped the xine backend...

Or do you mean Totem-gstreamer?

Check synaptic totem-xine is there.

---

### Post by taavikko on 2009-09-27
> **philinux said:**
> Check synaptic totem-xine is there.

```
A simple media player for the GNOME desktop (transitional package)
```
Which will pull gstreamer...

---

### Post by philinux on 2009-09-27
> **taavikko said:**
> ```
A simple media player for the GNOME desktop (transitional package)
```
Which will pull gstreamer...

Hi Thomas,

It says it just depends on totem. :confused:

---

### Post by taavikko on 2009-09-27
> **philinux said:**
> Hi Thomas,

It says it just depends on totem. :confused:

Think it's just an elaborate plan not to confuse those whom are used to use totem-xine.
Since it's been stripped from totem...

---

### Post by philinux on 2009-09-27
> **taavikko said:**
> Think it's just an elaborate plan not to confuse those whom are used to use totem-xine.
Since it's been stripped from totem...

I reckon you're right there lol.

Oh I better reboot and recover my Borat dvd.

---

### Post by mc4man on 2009-09-27
There are some continuing issues with dvd playback that can manifest in various ways. (seperate from audio or video output issues

if the volume isn't showing up then you need to either mount as root or boot up with a dvd in the drive. (this will probably lead to a locked drive at some point 

If the dvd is showing up there is a possibility of authentication failure which may crash vlc or have totem say something to the effect of encrypted blah blah.

If having such problems then either wait out a solution or for the moment remove libbrasero-media0, reboot and you should see a marked improvement.
[B]
Vlc has perfect navigation and full use of the dvd,[/B] it's only minor flaw can be subtitle rendering. Totally fail to understand those who claim otherwise.
If experiencing any issues with dvdnav in vlc then change the default launch command from vlc %U to the more proper vlc %f


Atm totem-xine (2.26) can still work with totem-common (2.28 ), though the cleanest way to use is build a totem 2.26 source, changing the package versioning to 2.28 and install only totem-xine.

The current totem works within it's continuing limitations on 2 separate installs.
It's biggest issue here is that on an install with 5.1 sound it is unable to play ac3 audio streams. If the disk contains a dts stream (as stream 0), then playback is fine.
( the problem with ac3 is pulseaudio will shoot to 100% cpu

There are no issues with ac3 on a 2.1 system

---

### Post by moviemaniac on 2009-09-27
> **mc4man said:**
> 
Vlc has perfect navigation and full use of the dvd,[/B] it's only minor flaw can be subtitle rendering. Totally fail to understand those who claim otherwise.

Another minor flaw is that the fullscreen-menu isn't working (at least in the official Karmic builds) which I find quite annoying. And VLC's deinterlacers are still... subpar to say the least (they've been for years). I used to watch DVDs in VLC for over a year now but since SMplayer is making rapid progress (apart from DVD menu support still being experimental) AND it has good deinterlacers (I still love Xine's more but that's unusable for me due to a bug in the fglrx drivers...) I tend to use SMplayer more and more for watching DVDs. For everything else, VLC was and is my default player :D

---

### Post by mc4man on 2009-09-27
> the fullscreen-menu isn't working

It works fine here but I use my own builds. Both the repo and korn builds lack some features, not sure why you can't do in fullscreen though.

Would agree that smplayer is also a great alternative to totem

---

### Post by philinux on 2009-09-27
Finally got the a dvd mounted. Had to logout then login and it got mounted on desktop.

---

### Post by moviemaniac on 2009-09-27
> **mc4man said:**
> It works fine here but I use my own builds. 

Well, in that case I'm also gonna go back to building my own versions. Did that for a year in Intrepid (anyone remember the separate video-window in the official builds?) so why not continue the tradition. I just thought I could be lazy now with Karmic :lolflag:

On another note: I just had both SMplayer and VLC die on me when playing an episode from CSI 9 DVD 5. They'd exit with a libdvdread-error (most probably CSS-related) when entering a chapter 2/3 into the episode. I tried the trick with the CSS-cache but nothing helped so I rebooted into OSX to watch the rest... Ah well, you've gotta be prepared for stuff like that when using an alpha release :popcorn:

@philinux: I've got similar problems with my internal drive* (sr0), both external ones (sr1 and 2) work just fine as far as mounting is concerned.
*It's a slot-in drive so I can't even eject the media sometimes...

---

### Post by terry_gardener on 2009-09-27
when i try to play some dvd's it says unable to open location you may not have permission, some dvd's play ok, some dvd's start to play but stop part way through with error unable to read from resources. 

i have tried both totem movie player (Default gstreamer version) and vlc. 

i have the latest libdvdcss2 package installed as per the medibuntu repos. 

i have even tried deleting the .dvdcss from home folder.

---

### Post by moviemaniac on 2009-09-27
Seems like quite a few of us are experiencing problems in a number of applications. What do we file this bug against? Might this have to do with the transformation to udev/devicekit?

---

### Post by mc4man on 2009-09-27
> On another note: I just had both SMplayer and VLC die on me when playing an episode from CSI 9 DVD 5. 

For curiosities sake i'll have that disk sent out next week though the wildcard would be R1 vs R4

> Might this have to do with the transformation to udev/devicekit? 
I believe that's at the heart of many of the issues that aren't of the 'quality of playback' type.

Patience would certainly be a virtue here

---

### Post by moviemaniac on 2009-09-27
> **mc4man said:**
> For curiosities sake i'll have that disk sent out next week though the wildcard would be R1 vs R4

I'm in Austria, no kangaroos and R2 :D (Unless you're from Australia and meant yourself, that is). I've got the R1 DVD box here (being a collector I import movies from all over the world) as it won't be released here for another coupl'a months. For the sake of comparison: it was episode 1 on disc 5 and, as I mentioned, it stopped playing at about 2/3 in. I didn't investigate more as my brother was watching too, but I think the error occurred at a VTS switch. I'll have a more detailed look at it tomorrow.

> **mc4man said:**
> Patience would certainly be a virtue here

A line that should be added to the usual Alpha-warnings. As long as it gets sorted out in the end I'm okay with these sometimes annoying - but interesting as you get to know how everything works and plays together - breakages. That's why I use the Alpha in the first place - to help sort these kinda things out.

---

### Post by mc4man on 2009-09-27
sorry about the  location, 

If you come across any other titles, feel free to mention, I've got a fair number and can always have sent out ( my netflis queue is almost always partially empty.


If you decide to build vlc.
On my working install (also have a straight up testing install, no changes, mods)

Using the repo ffmpeg libs ( extra version + -dev's ) and repo libx264-dev should be ok, no potential config limitations. ( native wmapro decoding will not be available if that matters.

I've settled on this atm
ffmpeg -r19777 (static and shared
libx264-75
a tree to current live555 (ver. repo package 

some add. modules enabled
globalhotkeys
dmo loader (32 bit only
snapshot
real
cddax
and some other minor or testing things

Left the native wmapro decoding in avcodec as it works perfectly in vlc when using -r19777 or earlier wmapro enabled ffmpeg (either in code or patched

I think overall the best building method is to use the vlc_1.02.orig source, a good starter .diff (not the karmic repo's) and use debuild.

Then any pre-build changes will be written to a new .diff. This .diff can be used on the .orig to make any further adjustments if needed or for a re-build.

The final working .diff then can later be used on a 1.02-git if desired. 

( for 1.1-git (yellow *******), I just do a sudo make install after removing current 1.02 packages

There is a good space saving doing as package sets, you can delete the source folder and only install packs. wanted

screen reflects what you get, in this case i also made a version change so got a complete new .diff (vs. having the one used re-written

I only install vlc, libvlc2, libvlccore2, vlc-nox, vlc-data,  pulse and sdl plugins (and delete the source folder after build

---

### Post by ranch hand on 2009-09-28
I can't play audio CDs but DVDs work fine on this box.

---

### Post by itsjareds on 2009-09-28
I haven't had this issue (don't have any DVDs to play), but try updating your package list now. I installed some updates and I saw one package with dvd in the name.

---

### Post by moviemaniac on 2009-09-28
> **itsjareds said:**
> I installed some updates and I saw one package with dvd in the name.

DVDrip - just a program to, well, rip DVDs, unrelated to the issues here.

@mc4man: Thanks! I'll try it this way! previously I used to completely remove the repo vlc and then just build them with make install after configuring, but your way seems a *bit* more elegant :D

---

### Post by moviemaniac on 2009-09-28
Ah well. Sometimes I'm really blind....
I just build myself a custom version only to find the fullscreen-controls still not working. Just for fun I moved back from the OpenGL to the (previously CPU-hogging which is why I didn't use it) Xv renderer and the controls reappeared.

DVD-playback-problems on that particular DVD are still tere, though.

---

### Post by philinux on 2009-09-28
Is there a bug report for this. DVDs dont even mount.

I have to logout then login to get it mounted. Or put dvd in at login screen.

Once mounted it plays fine.

These are only errors it spits out in dmesg when you put a dvd in, nothing in messages log.
```
[  148.460279] sr 4:0:0:0: [sr0] unaligned transfer
[  148.460344] sr 4:0:0:0: [sr0] unaligned transfer
[  148.460353] sr 4:0:0:0: [sr0] unaligned transfer
[  148.460636] sr 4:0:0:0: [sr0] unaligned transfer
[  148.460705] sr 4:0:0:0: [sr0] unaligned transfer
[  148.460762] sr 4:0:0:0: [sr0] unaligned transfer
```

---

### Post by moviemaniac on 2009-09-28
This sounds familiar: [https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237)

But I think this bug is filed against the wrong package - if I were you I'd file a new bug against devicekit-disks which seems to be the most likely suspect: [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks)

---

### Post by philinux on 2009-09-28
Ok I filed a bug against devicekit-disks
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065)

Can someone is the same boat pop along and confirm it for me. 

Cheers.

---

### Post by moviemaniac on 2009-09-28
> **philinux said:**
> Can someone is the same boat pop along and confirm it for me. 

Strange. I swear I had a similar problem with my sr0 drive. Now I tried to reproduce it to confirm your bugreport and it works just fine. :confused:

---

### Post by philinux on 2009-09-28
> **moviemaniac said:**
> Strange. I swear I had a similar problem with my sr0 drive. Now I tried to reproduce it to confirm your bugreport and it works just fine. :confused:

After logout and log back in. Then open dvd and close it gets mounted. This is what dmesg shows. But at least it mounted.
Mount shows this, /dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=philinux)
```
sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1860.289775] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1860.289785] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 1860.289802] end_request: I/O error, dev sr0, sector 13988136
[ 1860.289810] __ratelimit: 3 callbacks suppressed
[ 1860.289816] Buffer I/O error on device sr0, logical block 3497034
[ 1860.289823] Buffer I/O error on device sr0, logical block 3497035
[ 1860.329984] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1860.329998] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1860.330007] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 1860.330025] end_request: I/O error, dev sr0, sector 13988136
[ 1860.330035] Buffer I/O error on device sr0, logical block 3497034
[ 1860.330044] Buffer I/O error on device sr0, logical block 3497035
[ 1860.476665] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1860.580166] UDF-fs INFO UDF: Mounting volume 'BORAT', timestamp 2007/02/06 19:26 (103c)
```

---

### Post by moviemaniac on 2009-09-28
> Sep 28 13:18:16 klaus-imac kernel: [10558.636550] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
Sep 28 13:18:16 klaus-imac kernel: [10558.636563] end_request: I/O error, dev sr0, sector 2097136
Sep 28 13:18:16 klaus-imac kernel: [10558.637507] sr 0:0:0:0: [sr0] unaligned transfer
Sep 28 13:18:16 klaus-imac kernel: [10558.637675] sr 0:0:0:0: [sr0] unaligned transfer
Sep 28 13:18:16 klaus-imac kernel: [10558.870983] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep 28 13:18:16 klaus-imac kernel: [10558.899692] ISOFS: changing to secondary root
Sep 28 13:18:16 klaus-imac kernel: [11895.282372] UDF-fs: Partition marked readonly; forcing readonly mount
Seems okay and works

Can you reproduce the error on your end with _all_ discs?

---

### Post by philinux on 2009-09-28
Maybe it's a 64 bit thing?

---

### Post by moviemaniac on 2009-09-28
might be, I'm on 32bit

---

### Post by mc4man on 2009-09-28
A decent way to separate whether the problem is 32 vs 64 bit and or local hardware specific is to remove libbrasero-media0 (also removes brasero and rhythmbox)

Then reboot with no media in the drive and see. You can always add those 3 packages back.

---

### Post by philinux on 2009-09-28
Ok, just in jaunty so will chroot that and reboot.

---

### Post by philinux on 2009-09-28
> mc4man
A decent way to separate whether the problem is 32 vs 64 bit and or local hardware specific is to remove libbrasero-media0 (also removes brasero and rhythmbox)

Then reboot with no media in the drive and see. You can always add those 3 packages back.

Ok that fixed it. So it is indeed 64 bit related. Well my problem at least.

Where the bug then. Which package?

---

### Post by mc4man on 2009-09-28
@ philinux
If the removal of libbrasero-media0 'fixed' it then that is reflective of the issue affecting **both 32 and 64 bit **
It's been an ongoing thing, fixed. broken, fixed, broken 

orig bug 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/433150)

was 'fixed' till gksu nautilus was fixed with a new libbrasero-media0 version which broke it, then 'fixed' with some updates the next day, now broken again.

[http://ubuntuforums.org/showthread.php?p=7991250#post7991250](http://ubuntuforums.org/showthread.php?p=7991250#post7991250)

I'd wait it out,


(personally I never intend to use brasero or rhythmbox but that's irrelevant here. (possibly rhythmbox could be built without cd burning in brasero which would remove the dep. on libbrasero-media0

---

### Post by philinux on 2009-09-28
Cheers for that. At least I've got an explanation.

---

### Post by ranch hand on 2009-09-28
I just tried the video on my 64bit test drive and it is working fine with no tweeks.

This testing stuff is quite a FUN ride.

---

### Post by mc4man on 2009-09-28
Well went ahead and built a rhythmbox on my 'working' install, removing the brasero burning option.

It works as well as the rhythmbox on my 'testing' install, 

Back on the testing noticed an odd thing with rhythmbox ( the testing install is straight up, all updates, no mods.

Rhythmbox can't play audio cd's -  no 'cdda uri handler' and or a 'can't start pipeline', and additionally when an audio cd is in the drive can't play any local files ( keeps trying to play the cd I think.

Removed the audio cd and it then plays files

---

### Post by punkybouy on 2009-09-28
Some DVD's work and some don't on my 32 bit 8.04 LTS and the one's that do not are ones that worked a month ago.  On 64 bit Jaunty none work.  So who messed up?

---

### Post by ranch hand on 2009-09-28
[mc4man]("http://ubuntuforums.org/member.php?u=320715")
There is a thread on the CD issue.

[punkybouy]("http://ubuntuforums.org/member.php?u=84274")
I am having no trouble with my Jaunty 64bit at all.

---

