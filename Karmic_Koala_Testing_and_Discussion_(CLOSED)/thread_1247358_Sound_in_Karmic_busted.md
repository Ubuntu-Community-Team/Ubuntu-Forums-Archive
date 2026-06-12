---
title: "Sound in Karmic busted"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-08-22
Is the sound across the board broken in Karmic for all that are running it? And do we all get the volume deprecated if we try and add it to the panel?

Asking to see if need to file a bug report..

---

### Post by cyberkilla on 2009-08-22
Sound works for me, but I think it was broken when I upgraded to Karmic.

I can't remember what I did to fix it though! Sorry.

---

### Post by Starks on 2009-08-22
For me, Pulseaudio has good days and bad days.

Sometimes it'll play nice, other times it'll mute without reason.

---

### Post by bear24rw on 2009-08-22
sound usually works for me but sometimes only a few applications at a time, flash in firefox and music in banshee cannot play at the same time for instance..

---

### Post by sports fan Matt on 2009-08-22
mine doesnt work and I cant seem to check it because of what ive described above.

---

### Post by sports fan Matt on 2009-08-23
no updates and still no sound this morning, just fyi

---

### Post by taavikko on 2009-08-23
Use "alsamixer" and/or "alsamixer -Dhw" to see if channels are muted.

check the output device with the volume-applet->Right Click-> "output" tab

---

### Post by sports fan Matt on 2009-08-23
I'll see if I can ..seems like I cant even see the volume indicator since its depreciated

---

### Post by sports fan Matt on 2009-08-23
Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC662 rev1                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-64.00]                                                &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;MM&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;      0               98<>98  100<>100   0<>0      0<>0     0<>0     0<>0     &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Front Mi   Line     Mic      &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Thats the output from the terminal of alsa mixer..

---

### Post by taavikko on 2009-08-23
> **sox fan Matt said:**
> seems like I cant even see the volume indicator since its depreciated

?

Default session includes "gnome-volume-control-applet" provided via  gnome-media.
If you have tweaked/purged randomly stuff, then reset those and run default installation.

---

### Post by taavikko on 2009-08-23
> **sox fan Matt said:**
> ```
Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC662 rev1                                                    &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-64.00]                                                &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;MM&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;               &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;      0               98<>98  100<>100   0<>0      0<>0     0<>0     0<>0     &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Front Mi   Line     Mic      &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
Thats the output from the terminal of alsa mixer..

As you can see all the channels are muted, unmute them with M

---

### Post by sports fan Matt on 2009-08-23
Im trying to get there still no sound yet

---

### Post by sports fan Matt on 2009-08-23
After unmuting "making the green m" visible, nothing has changed..no sound.

---

### Post by sports fan Matt on 2009-08-23
im gonna wait and see for a fix in regards to : Hey, just upgraded from Jaunty to Karmic and as soon as my machine rebooted from the upgrade I'm completely without sound, and can't even add the volume control, it says (Deprecated) beside it.


its exactly what im having and even with the fix, its a no go...hopefully it will be fixed before the final release :)

---

### Post by taavikko on 2009-08-23
> **sox fan Matt said:**
> im gonna wait and see for a fix in regards to : Hey, just upgraded from Jaunty to Karmic and as soon as my machine rebooted from the upgrade I'm completely without sound, and can't even add the volume control, it says (Deprecated) beside it.


its exactly what im having and even with the fix, its a no go...hopefully it will be fixed before the final release :)

Those are one of those things when upgrading release.
I would clean $HOME of old settings and restart the session, it should "at least" few problems you might face.

Or starting by removing .pulse* in virtual console without running session.

btw. there's an edit button, which can be used.

---

### Post by sports fan Matt on 2009-08-23
Very true and honestly its minor and i completely suspect before the final release these bugs will be worked out:)

---

### Post by nanog on 2009-08-24
I've had the volume does not work bug crop up many times in karmic(there are multiple posts). In my case it always has something to do with *junk* that get dropped into the .pulse directory:

```
rm -r ~/.pulse; sudo apt-get remove --purge pulseaudio; sudo apt-get update; sudo apt-get install pulseaudio
```

---

### Post by psyke83 on 2009-08-24
> **nanog said:**
> I've had the volume does not work bug crop up many times in karmic(there are multiple posts). In my case it always has something to do with *junk* that get dropped into the .pulse directory:

```
rm -r ~/.pulse; sudo apt-get remove --purge pulseaudio; sudo apt-get update; sudo apt-get install pulseaudio
```

That's a good idea, but purging and re-installing pulseaudio isn't necessary.

sox fan Matt, install and run "pavucontrol", and check the Configuration tab. You may need to change the profile.

---

### Post by hotstovejer on 2009-08-24
Here's something that I want to throw at everyone to see what they think in regard to this issue.

I currently am duelbooting jaunty and karmic. I share my home dir with both distros, and I was looking at my .pulse dir, and found this!

```
drwx------  2 hotstovejer hotstovejer  4096 2009-08-23 22:26 .
drwxr-xr-x 79 hotstovejer hotstovejer 12288 2009-08-23 22:26 ..
-rw-r--r--  1 hotstovejer hotstovejer     4 2009-08-22 21:11 2de74bac880c76c7fce8b8974a82d762:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    12 2009-08-22 21:11 2de74bac880c76c7fce8b8974a82d762:default-source
-rw-------  1 hotstovejer hotstovejer 17438 2009-08-23 14:45 2de74bac880c76c7fce8b8974a82d762:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-22 21:11 2de74bac880c76c7fce8b8974a82d762:runtime -> /tmp/pulse-PKdhtXMmr18n
-rw-------  1 hotstovejer hotstovejer 31868 2009-08-23 14:43 2de74bac880c76c7fce8b8974a82d762:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-------  1 hotstovejer hotstovejer 12288 2009-04-20 16:30 6a9564a283ee3d965db312b549a9e89e:card-database.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer    38 2009-04-20 16:53 6a9564a283ee3d965db312b549a9e89e:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    37 2009-04-20 16:53 6a9564a283ee3d965db312b549a9e89e:default-source
-rw-------  1 hotstovejer hotstovejer 14785 2009-04-20 16:55 6a9564a283ee3d965db312b549a9e89e:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-04-20 16:53 6a9564a283ee3d965db312b549a9e89e:runtime -> /tmp/pulse-1gpGDXM63zNJ
-rw-------  1 hotstovejer hotstovejer 29993 2009-04-20 17:42 6a9564a283ee3d965db312b549a9e89e:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer    54 2009-02-27 23:04 85967b5260f059c0c4d20d1d49a746a3:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    52 2009-02-27 23:04 85967b5260f059c0c4d20d1d49a746a3:default-source
-rw-------  1 hotstovejer hotstovejer 13276 2009-02-26 19:49 85967b5260f059c0c4d20d1d49a746a3:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-02-27 23:04 85967b5260f059c0c4d20d1d49a746a3:runtime -> /tmp/pulse-iPRZW9xfU8es
-rw-------  1 hotstovejer hotstovejer 13638 2009-02-27 22:34 85967b5260f059c0c4d20d1d49a746a3:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer     9 2009-08-14 12:08 9b647215ccb50933baa49fb54a859a04:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    52 2009-08-14 12:08 9b647215ccb50933baa49fb54a859a04:default-source
-rw-------  1 hotstovejer hotstovejer 14410 2009-08-14 12:08 9b647215ccb50933baa49fb54a859a04:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-14 12:08 9b647215ccb50933baa49fb54a859a04:runtime -> /tmp/pulse-A3NdVfxfZwg8
-rw-------  1 hotstovejer hotstovejer 16835 2009-08-14 20:10 9b647215ccb50933baa49fb54a859a04:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer   696 2009-08-23 17:46 b549d12ad13901c5e3d79ef24a916cfc-card-database.tdb
-rw-r--r--  1 hotstovejer hotstovejer    43 2009-08-23 22:26 b549d12ad13901c5e3d79ef24a916cfc-default-sink
-rw-r--r--  1 hotstovejer hotstovejer     9 2009-08-23 11:23 b549d12ad13901c5e3d79ef24a916cfc:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    42 2009-08-23 22:26 b549d12ad13901c5e3d79ef24a916cfc-default-source
-rw-r--r--  1 hotstovejer hotstovejer    52 2009-08-23 11:23 b549d12ad13901c5e3d79ef24a916cfc:default-source
-rw-r--r--  1 hotstovejer hotstovejer 61440 2009-08-24 07:37 b549d12ad13901c5e3d79ef24a916cfc-device-volumes.tdb
-rw-------  1 hotstovejer hotstovejer 14410 2009-08-23 17:44 b549d12ad13901c5e3d79ef24a916cfc:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-23 22:26 b549d12ad13901c5e3d79ef24a916cfc-runtime -> /tmp/pulse-Hrd1heSRatGo
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-23 11:23 b549d12ad13901c5e3d79ef24a916cfc:runtime -> /tmp/pulse-OScTGkz8FnUb
-rw-r--r--  1 hotstovejer hotstovejer 73728 2009-08-23 22:26 b549d12ad13901c5e3d79ef24a916cfc-stream-volumes.tdb
-rw-------  1 hotstovejer hotstovejer 15884 2009-08-23 17:43 b549d12ad13901c5e3d79ef24a916cfc:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer     9 2009-08-08 16:48 f62688251ec7f370f52b3b0449ed0105:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    17 2009-08-08 16:48 f62688251ec7f370f52b3b0449ed0105:default-source
-rw-------  1 hotstovejer hotstovejer 16729 2009-07-14 18:26 f62688251ec7f370f52b3b0449ed0105:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-08 16:48 f62688251ec7f370f52b3b0449ed0105:runtime -> /tmp/pulse-0L9vOWeiZkpy
-rw-------  1 hotstovejer hotstovejer 41410 2009-08-11 13:59 f62688251ec7f370f52b3b0449ed0105:stream-volumes.x86_64-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer 24576 2009-08-22 21:08 f7ff135de41543470b0b65d54a8b02dc-card-database.tdb
-rw-r--r--  1 hotstovejer hotstovejer    43 2009-08-23 16:01 f7ff135de41543470b0b65d54a8b02dc-default-sink
-rw-r--r--  1 hotstovejer hotstovejer     9 2009-08-18 14:37 f7ff135de41543470b0b65d54a8b02dc:default-sink
-rw-r--r--  1 hotstovejer hotstovejer    42 2009-08-23 16:01 f7ff135de41543470b0b65d54a8b02dc-default-source
-rw-r--r--  1 hotstovejer hotstovejer    52 2009-08-18 14:37 f7ff135de41543470b0b65d54a8b02dc:default-source
-rw-r--r--  1 hotstovejer hotstovejer 57344 2009-08-22 21:08 f7ff135de41543470b0b65d54a8b02dc-device-volumes.tdb
-rw-------  1 hotstovejer hotstovejer 14410 2009-08-18 14:37 f7ff135de41543470b0b65d54a8b02dc:device-volumes.x86_64-pc-linux-gnu.gdbm
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-23 16:01 f7ff135de41543470b0b65d54a8b02dc-runtime -> /tmp/pulse-ywSeRJH0vPJl
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-18 14:37 f7ff135de41543470b0b65d54a8b02dc:runtime -> /tmp/pulse-DvPdCsZym4tW
-rw-r--r--  1 hotstovejer hotstovejer 57344 2009-08-23 16:02 f7ff135de41543470b0b65d54a8b02dc-stream-volumes.tdb
-rw-------  1 hotstovejer hotstovejer 15894 2009-08-18 21:34 f7ff135de41543470b0b65d54a8b02dc:stream-volumes.x86_64-pc-linux-gnu.gdbm
```

I checked out my karmic machine at work, and had this.

```
drwx------  2 hotstovejer hotstovejer  4096 2009-08-21 08:14 .
drwxr-xr-x 41 hotstovejer hotstovejer  4096 2009-08-21 08:14 ..
-rw-r--r--  1 hotstovejer hotstovejer  3072 2009-08-06 15:00 085559bcbf0df022aefec28c49692198-card-database.i486-pc-linux-gnu.gdbm
-rw-------  1 hotstovejer hotstovejer 12288 2009-05-06 13:43 085559bcbf0df022aefec28c49692198:card-database.i486-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer   696 2009-08-17 09:41 085559bcbf0df022aefec28c49692198-card-database.tdb
-rw-r--r--  1 hotstovejer hotstovejer  3072 2009-08-06 15:00 085559bcbf0df022aefec28c49692198-device-volumes.i486-pc-linux-gnu.gdbm
-rw-------  1 hotstovejer hotstovejer 12288 2009-01-10 16:54 085559bcbf0df022aefec28c49692198:device-volumes.i486-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer   696 2009-08-17 09:41 085559bcbf0df022aefec28c49692198-device-volumes.tdb
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-08-21 08:14 085559bcbf0df022aefec28c49692198-runtime -> /tmp/pulse-fZOjs5p7P2Xf
lrwxrwxrwx  1 hotstovejer hotstovejer    23 2009-07-29 09:41 085559bcbf0df022aefec28c49692198:runtime -> /tmp/pulse-crSJap8ubtSM
-rw-r--r--  1 hotstovejer hotstovejer  3072 2009-08-06 15:00 085559bcbf0df022aefec28c49692198-stream-volumes.i486-pc-linux-gnu.gdbm
-rw-------  1 hotstovejer hotstovejer 12288 2009-01-10 16:54 085559bcbf0df022aefec28c49692198:stream-volumes.i486-pc-linux-gnu.gdbm
-rw-r--r--  1 hotstovejer hotstovejer   696 2009-08-17 09:41 085559bcbf0df022aefec28c49692198-stream-volumes.tdb

```

Do you think the pulse folder is causing conflicts? I was thinking about creating a new user on each side and seeing what might happen. 

Any thoughts?

Thanks!

Jeremy

BTW, other than the sound issue, I am diggin the little Koala. :)

---

### Post by sports fan Matt on 2009-08-24
that command returns pavucontrol is already the newest version.
pavucontrol set to manually installed.

---

### Post by Enigmatic on 2009-08-24
Not quite related, but I'm noticing that the mute level for sound is at 30% of the overall volume. Is there any way to get this down to 0%? Ie that the volume doesn't disappear until 0 vs the current 30% or so.

---

### Post by cyberkilla on 2009-08-25
Just a quick FYI, my sound was broken when I upgraded to Karmic...

I later found that it was a group issue. If you look on Users & Groups, you can select your useraccount and check the box next to Audio.

That fixed it for me.

---

### Post by crimsun on 2009-08-25
> **hotstovejer said:**
> I currently am duelbooting jaunty and karmic. I share my home dir with both distros, and I was looking at my .pulse dir, and found this!

Not an issue. We don't use gdbm in Karmic's PA anymore.

---

### Post by crimsun on 2009-08-25
> **Enigmatic said:**
> Not quite related, but I'm noticing that the mute level for sound is at 30% of the overall volume. Is there any way to get this down to 0%? Ie that the volume doesn't disappear until 0 vs the current 30% or so.

That's an ALSA bug. File a bug against linux.

---

### Post by plun on 2009-08-25
> **crimsun said:**
> That's an ALSA bug. File a bug against linux.

Hello crimsun

Can you please clarify this !?

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)

PulseAudio bug  ???

---

### Post by sports fan Matt on 2009-08-25
If I decide to retry Karmic I'll look at it, I accidently borked the volume control so now im back on jaunty.

---

### Post by jwssr on 2009-08-25
RED sox...I suppose!  

I have spent maqny hours on sound in karmic as well as jaunty...

With karmic...I have found that without these 3 tools it is impossible to diag any problems...

gnome-alsamixer
paman
pavucontrol

All 3 of these can be installed with synaptic or apt-get install.

paman is run from a terminal window w/o root .....ie  $ paman
it will show all info about pulse audio...although you many chaange info with this tooll....I do not...rather use alsamixer and pavucontrol.

pavucontrol  shows up in applications/sound & video/pulseaudio volume control.
although for the past 2 alpha rel 3/4  there seems to be big problems
..connection failed:connection terminated errro shows up after 8 secs on both of my boxes running karmic....I use this tool for info only.

alsamkixer shows up in applications/sound & video/GNOME ALSA mixer..
this is where you can see if any channels are muted, sliders showing volume levels, ice958 (digital audio) and the audio sinks....ie analog,digital, hdmi..
this is where I usually get things done....

right now karmic is very unstable in sound...as it is an ALPHA release...expect problems as they will be here until the end of the cycle...then expect it to work flawlessly....not right now...

use this experience as a learning tool about alsa, pulseaudio...there is a ton of reading to be done...if you are up to it...all over the net...google is your friend...

good luck and sox go in as a wild card...remember 2003.

---

### Post by sports fan Matt on 2009-08-25
I knew that honestly, Thanks for the suggestions but I had checked and all are the latest version, but you are right..it will be fixed :)

---

### Post by crimsun on 2009-08-25
> **plun said:**
> Hello crimsun

Can you please clarify this !?

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)

PulseAudio bug  ???

Depends when the mixer is touched.

The easiest way to confirm is to reboot, avoid logging in via GDM/KDM, switch to a console getty, log in, and inspect the output from "amixer -Dhw:0".

---

### Post by crimsun on 2009-08-25
> **jwssr said:**
> right now karmic is very unstable in sound

If you're not filing bugs, we can't fix them.

---

