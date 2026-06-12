---
title: "Superblock last write time is in the future! = Profit?"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by clubsoda on 2009-08-28
1. Superblock last write time is in the future
2. manual fsck
3. ...?
4. Profit!

Obviously I need a widget which stores stock prices or maybe dog racing results in the superblock. :)

Seriously though, "props" (as some cool people say) to all the developers out there.  This week already two significant fixes:-
- No more keyyyboard repeatssss in the realtime keeeernel as of 2.6.31-3-rt
- grub2: Unexplained 12-second delay between BIOS screen and boot menu now gone.

clubsoda

---

### Post by infamousrev on 2009-08-28
Your post is quite confusing :o

---

### Post by Tibuda on 2009-08-28
> **infamousrev said:**
> Your post is quite confusing :o

Yes, it is. I cant understand what is this about... fsck? stock price widget? dog race widget?

---

### Post by olskar on 2009-08-28
Make sense

---

### Post by skillllllz on 2009-08-28
I'm guessing you guys don't frequent Slashdot... because I understood him perfectly... lol

---

### Post by olskar on 2009-08-28
> **skillllllz said:**
> I'm guessing you guys don't frequent Slashdot... because I understood him perfectly... lol


Perhaps we should be ashamed ;)

---

### Post by jmmL on 2009-08-28
> **clubsoda said:**
> 1. Superblock last write time is in the future
2. manual fsck
3. ...?
4. Profit!
The "1.2.3.4. Profit!" thing is a silly slashdot [meme]("http://en.wikipedia.org/wiki/Meme").
I'm pretty sure this is what clubsoda is saying: "Superblock last write times are times from the future. They should obviously be in the past, and this is a bug. When I run a manual fsck, something bad happens". Do you experience data loss clubsoda? You should file a bug if so, or at the very least describe steps to reproduce.

> Obviously I need a widget which stores stock prices or maybe dog racing results in the superblock. :)Clubsoda is making a joke. Seeing as superblock is saying that it has written "in the future", he/she jokes that if only he/she could store stock prices (or race results) in the superblock, he/she could be rich!

> Seriously though, "props" (as some cool people say) to all the developers out there.  This week already two significant fixes:-
- No more keyyyboard repeatssss in the realtime keeeernel as of 2.6.31-3-rt
- grub2: Unexplained 12-second delay between BIOS screen and boot menu now gone."Thanks for the developers for their continued work. I am particularly grateful for

[LIST]
[*]The keyboard repeat bug in -rt kernel being fixed
[*]The 12-second delayed between BIOS and grub being removed"
[/LIST]

I'm a native english speaker, and even I found this hard to comprehend. I'm not trying to offend, but anyone who posts in any language here needs to be aware that many non-fluent speakers frequent these forums, and for this reason posts should be clear and unambiguous.

Just a note: I have no idea what a superblock is, so sorry if my explanation is not clear. I was also not aware of the other two bugs referenced by clubsoda.

---

### Post by Tibuda on 2009-08-28
Thanks, jmmL and skillllllz... I don't frequent slashdot, so the joke made no sense for me.

---

### Post by woedend on 2009-08-28
oops beat me to it.
But I thought the meme came from South Park...I never visit slashdot.

---

### Post by MacUntu on 2009-08-29
Anyways - why does this happen? Seen this the first time today. Next reboot/fsck made the inconsistency consistent again. The shutdown before was a clean one.

---

### Post by NCLI on 2009-08-29
> **jmmL said:**
> The "1.2.3.4. Profit!" thing is a silly slashdot [meme]("http://en.wikipedia.org/wiki/Meme").
I'm pretty sure this is what clubsoda is saying: "Superblock last write times are times from the future. They should obviously be in the past, and this is a bug. When I run a manual fsck, something bad happens". Do you experience data loss clubsoda? You should file a bug if so, or at the very least describe steps to reproduce.

Just a small correction:

It's a 4chan meme, like pretty much any meme, it just spread far across the internet ;)

---

### Post by Paqman on 2009-08-29
> **woedend said:**
> 
But I thought the meme came from South Park...

It is. It was the Underpants Gnomes' plan for world domination, IIRC.

---

### Post by clubsoda on 2009-08-29
First, about the bug, fortunately it [has been reported](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540575) on Debian, although it also looks possible that [this older bug](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=343662) may have come back to life.

I assumed lots of people would be seeing this error but it seems there are certain preconditions:-
1) You live East of Greenwich, or at least your timezone is set to GMT plus X hours.
2) You dual boot with the hardware clock running local time, or at least you have set UTC=no in /etc/default/rcS
3) /usr is on a separate partition from /

Nothing goes wrong if a manual fsck is performed as advised by the stern message in the root console. However, fsck is probably unnecessary because there's nothing actually wrong with the file system.  Just reboot. 

===============================

My apologies to those who may have found my first message incomprehensible.  It was not my intention to be obscure. Thanks, jmmL for your tactfully worded constructive criticism which is valued and duly taken aboard.  [Translation for non-native english readers: In future I shall try to express my attempts at humour with greater clarity.]

===============================

Ah yes, the South Park (Underpants) Gnomes episode which was first broadcast in Dec '98.  <[Extract here](http://www.youtube.com/watch?v=Pe6kGJDGctU)>. I wonder if there are prior references to the profit "meme" on Slashdot or 4ch...

---

### Post by NCLI on 2009-08-29
Hmm, Southpark may have come up with it, but i have no doubt that 4chan/b/ made it into a meme.

---

### Post by ronacc on 2009-08-29
@ clubsoda jokes are one of the hardest things to translate :lolflag:

---

### Post by kansasnoob on 2009-08-29
> Nothing goes wrong if a manual fsck is performed as advised by the stern message in the root console. However, fsck is probably unnecessary because there's nothing actually wrong with the file system. Just reboot.

And sometimes reboot & reboot & reboot & reboot & reboot:

[http://ubuntuforums.org/showthread.php?t=1252690](http://ubuntuforums.org/showthread.php?t=1252690)

Typical alpha annoyance.

---

### Post by Paqman on 2009-08-30
> **NCLI said:**
> Hmm, Southpark may have come up with it, but i have no doubt that 4chan/b/ made it into a meme.

4chan turns *everything* into a meme. Whether it's actually funny or not.

---

### Post by jithin1987 on 2009-09-03
I have dual boot and UTC=no in /etc/default/rcS.
How can I fix this issue. Its highly annoying as I am using rseiub regualry in karmic :(

---

### Post by kansasnoob on 2009-09-03
> **jithin1987 said:**
> I have dual boot and UTC=no in /etc/default/rcS.
How can I fix this issue. Its highly annoying as I am using rseiub regualry in karmic :(

Are you updated?

Post the output of:

```
uname -r 
```

For me the problem resolved with 2.6.31-9.

---

### Post by jithin1987 on 2009-09-03
Its 2.6.31-9-generic. Its been happening always for me.

---

### Post by bobince on 2009-09-06
Yeah, this happens to me when a crash causes fsck on next boot. I'm currently in UTC+2h and that's exactly how far 'in the future' the timestamp is. Only appeared on my '/' ext4 partition so far; I didn't experience this in Jaunty, but then I think I always ran hwclock UTC.

---

### Post by rajeev1204 on 2009-09-16
I get fsck failures quite often.

---

### Post by kimda on 2009-09-16
> **rajeev1204 said:**
> I get fsck failures quite often.

Old harddrive? Maybe your harddrive is failing. Have you tried checking it with smartctl utility? 

[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)

---

### Post by dino99 on 2009-09-16
that's same for me:

dual boot
utc+2
files in /dev are in the future (+2)

can't find a way to boot karmic ( chrooted daily upgraded)
always fail with fsck error 16 in a root maintenance shell

---

### Post by Roger E Critchlow Jr on 2009-09-16
This started happening to me during the upstart-less updates yesterday, so I kept getting kicked into a maintenance shell with superblocks dated in the future.

What I was seeing was that the hwclock time was correct, in my local timzone, but the system was running on UTC but thinking that it was running local time.

And , now, after my last update today, the hwclock time has moved to UTC, while /etc/adjtime still claims LOCAL, and /etc/default/rcS still claims UTC=no.  The TZ is still applied so everything thinks I'm six hours into the future now.

I've just fixed it by resetting date with date (why doesn't date accept its own output format as input???) and hwclock -w to write the hardware clock.

-- rec --

---

### Post by TeutonJon78 on 2009-09-18
I noticed this problem on a fresh install with Karmic A5 and A6. (in a VirtualBox 3.0.4 VM)

The "wrong" time was definitely off by the UTC time.  I'm on the west coast of the US, and it was UTC-7 (DST) showing up as the "wrong time".  So something if off with the time settings of the live installer.

---

### Post by MacUntu on 2009-09-18
I've resolved this by setting the system clock (BIOS) to UTC (I'm at UTC+2) - something I didn't want to do in the first place but those fsck-messages were getting on my nerves.

---

### Post by TeutonJon78 on 2009-09-18
> **TeutonJon78 said:**
> I noticed this problem on a fresh install with Karmic A5 and A6.

The "wrong" time was definitely off by the UTC time.  I'm on the west coast of the US, and it was UTC-7 (DST) showing up as the "wrong time".  So something if off with the time settings of the live installer.

I just rebooted and it complained again about mount time.  Basically, it seems that UTC time isn't working at the time of the boot process the check is going on.

The unmount time is the correct local time, but the time that is checking it against is back to UTC time which seems to be the future.

---

