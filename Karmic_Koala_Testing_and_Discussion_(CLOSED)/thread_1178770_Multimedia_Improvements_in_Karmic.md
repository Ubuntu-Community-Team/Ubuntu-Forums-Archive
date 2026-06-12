---
title: "Multimedia Improvements in Karmic"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-06-04
Friends I'm pleased to say the bug with swapping audio streams and subtitle streams during playback in totem is fixed :D

What we need now is for the resindvd enhancements in gstreamer to come into our repos, and then we are closer than ever to a reasonable multimedia experience on Ubuntu with the default gstreamer backend.

Simply install the good, bad ugly and ffmpeg gstreamer plugins and your set. :popcorn:

---

### Post by LittleKoy on 2009-06-05
Do you know if the problem with multiple subtitles was solved?

---

### Post by pferraro on 2009-06-05
You called gstreamer the "default backend".  gstreamer is in fact now the *only* backend supported by totem.  totem-xine no longer exists.

---

### Post by Nullack on 2009-06-05
> **LittleKoy said:**
> Do you know if the problem with multiple subtitles was solved?

yes it is :D

---

### Post by LittleKoy on 2009-06-05
> **Nullack said:**
> yes it is :D

If it's the bug I'm thinking of, totem is likely becoming my default player :O

---

### Post by zekopeko on 2009-06-05
no if only it supported styled subs... it would rock.

---

### Post by Gourgi on 2009-06-05
@ Nullack : Thanks for the good news!
keep up devs !

> **zekopeko said:**
> no if only it supported styled subs... it would rock.

+1 on that.
even though i use totem for almost all my video needs
i really need to be able to make tha subs yellow.
yellow is much more relaxing for me.

---

### Post by Nullack on 2009-06-07
So Ive been testing the new resindvd revision in the latest gstreamer bad plugins set - it has numerous fixes for DVD navigation.

I dont get far, audio problems:

Jun  8 11:01:10 PPP pulseaudio[10219]: protocol-native.c: Failed to push data into queue
Jun  8 11:01:32 PPP last message repeated 4259 times
Jun  8 11:01:34 PPP pulseaudio[10219]: ratelimit.c: 531 events suppressed
Jun  8 11:01:34 PPP pulseaudio[10219]: asyncq.c: q overrun, queuing locally
Jun  8 11:01:34 PPP last message repeated 10 times
Jun  8 11:01:35 PPP pulseaudio[10219]: protocol-native.c: Failed to push data into queue
Jun  8 11:01:35 PPP last message repeated 22 times
Jun  8 11:02:00 PPP pulseaudio[10219]: ratelimit.c: 133 events suppressed
Jun  8 11:02:00 PPP pulseaudio[10219]: asyncq.c: q overrun, queuing locally
Jun  8 11:02:12 PPP last message repeated 15 times
Jun  8 11:02:17 PPP pulseaudio[10219]: ratelimit.c: 697 events suppressed
Jun  8 11:02:17 PPP pulseaudio[10219]: asyncq.c: q overrun, queuing locally
Jun  8 11:02:17 PPP last message repeated 10 times

---

### Post by Nullack on 2009-06-07
Ive bugged it:

[https://bugs.launchpad.net/ubuntu/+bug/384666](https://bugs.launchpad.net/ubuntu/+bug/384666)

---

### Post by Nullack on 2009-06-09
Hmm well the recent pulse audio updates havent fixed it.
```

Jun  9 14:12:17 PPP kernel: [76167.992625] gvfs-gdu-volume[9768]: segfault at 18 ip 00007fdfadf4d2f1 sp 00007fff6553d600 error 4 in libgdu.so.0.0.0[7fdfadf42000+22000]
Jun  9 14:13:14 PPP kernel: [76225.133371] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.133377] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.133382] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:14 PPP kernel: [76225.317568] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.317574] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.317579] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:14 PPP kernel: [76225.383962] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.383967] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.383972] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:14 PPP kernel: [76225.424938] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.424944] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.424949] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:14 PPP kernel: [76225.489033] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.489039] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.489044] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:14 PPP kernel: [76225.526516] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 14:13:14 PPP kernel: [76225.526522] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun  9 14:13:14 PPP kernel: [76225.526526] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Jun  9 14:13:15 PPP kernel: [76225.831805] UDF-fs: Partition marked readonly; forcing readonly mount
Jun  9 14:13:15 PPP kernel: [76225.863063] UDF-fs INFO UDF: Mounting volume 'SERENITY', timestamp 2005/12/07 01:35 (1000)
Jun  9 14:13:25 PPP kernel: [76235.969753] gvfs-gdu-volume[9870]: segfault at 18 ip 00007f771aae12f1 sp 00007fff53721520 error 4 in libgdu.so.0.0.0[7f771aad6000+22000]
Jun  9 14:14:42 PPP pulseaudio[9685]: protocol-native.c: Failed to push data into queue
Jun  9 14:15:08 PPP last message repeated 4836 times
Jun  9 14:17:43 PPP pulseaudio[9685]: protocol-native.c: Failed to push data into queue
Jun  9 14:20:23 PPP pulseaudio[9685]: asyncq.c: q overrun, queuing locally
Jun  9 14:20:23 PPP last message repeated 10 times
Jun  9 14:21:36 PPP kernel: [76726.931655] gvfs-gdu-volume[10053]: segfault at 18 ip 00007f6ee4a552f1 sp 00007fff2a3fe230 error 4 in libgdu.so.0.0.0[7f6ee4a4a000+22000]
```

As well, Im dissapointed to see that gstreamer still hasnt gotten DVD navigation right with Totem. Audio streams and subtitle streams still fail to be properly detected......

What are other testers seeing with DVD navigation?

---

### Post by psyke83 on 2009-06-10
I popped in a copy of The Da Vinco Code, opened Totem and to my surprise, shock and elation, the DVD menu appeared :P.

Some comments from testing with this particular movie:
[LIST]
[*]"Play Main Movie" works as expected, and displayed all the interstitial advertisements correctly before playing the main movie (booo.... a bug, not a feature! :P).
[*]Changing audio tracks and subtitles works via DVD navigation, but Totem's View -> Subtitles sub-menu merely displays a ghosted "Empty" entry.
[*]"Scene Selection" works correctly (but it seemed to freeze Totem in one instance).
[*]Navigating manually via the playback slider always results in the error "An error occurred / Could not read from resource". I was suspicious that it could be a physical defect (scratch/dirt), but the disc is in fairly good shape.
[*]Audio has slight (but annoying) microstutters, and audio/video occasionally changes speed erratically. This is unrelated to Totem/resindvd, it's [bug #345627]("https://bugs.launchpad.net/bugs/345627") which I seem to experience with *all* media whose audio codec uses a rate of 48000Hz (which includes this DVD).
[*]Drive buffering is not optimal (i.e., it should always try to buffer enough video to compensate for the delay incurred when a drive must spin back up from standby). My laptop's ancient DVD-ROM/CD-RW combo drive may be at fault, though.
[/LIST]

Nullack, I didn't observe any errors similar to what you posted... perhaps there was an update somewhere that resolved that particular issue, or perhaps Serenity's particular DVD navigation is exposing some features that resindvd cannot yet handle correctly? I don't own that DVD so I can't test it, unfortunately. Perhaps try another DVD. As for the audio problems, it seems unusual that no other content causes this issue, but it indeed seems to be a PulseAudio interaction bug. 

P.S. I get all sorts of suspicious output from my kernel log, but I recall most DVDs always giving these kind of buffer errors and so forth. Again, probably my DVD at fault:```
[11023.820139] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11023.820155] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[11023.820170] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[11023.820194] end_request: I/O error, dev sr0, sector 8388520
[11023.820208] Buffer I/O error on device sr0, logical block 1048565
[11023.840121] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11023.840134] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[11023.840146] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[11023.840167] end_request: I/O error, dev sr0, sector 8388520
[11023.840177] Buffer I/O error on device sr0, logical block 1048565
[11024.423745] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11024.423761] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[11024.423775] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[11024.423799] end_request: I/O error, dev sr0, sector 16679280
[11024.423811] Buffer I/O error on device sr0, logical block 2084910
[11024.498973] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11024.498981] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[11024.498988] sr 1:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[11024.499000] end_request: I/O error, dev sr0, sector 16679280
[11024.499008] Buffer I/O error on device sr0, logical block 2084910
[11024.903553] UDF-fs: Partition marked readonly; forcing readonly mount
[11024.984320] UDF-fs INFO UDF: Mounting volume 'DAVINCI_CODE', timestamp 2006/08/05 15:44 (103c)
[11550.236198] sr 1:0:0:0: [sr0] Unhandled sense code
[11550.236204] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11550.236209] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[11550.236216] sr 1:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[11550.236226] end_request: I/O error, dev sr0, sector 1056752
[11550.236234] Buffer I/O error on device sr0, logical block 264188
[11550.236240] Buffer I/O error on device sr0, logical block 264189
[11550.236247] Buffer I/O error on device sr0, logical block 264190
[11550.236250] Buffer I/O error on device sr0, logical block 264191
[11550.236254] Buffer I/O error on device sr0, logical block 264192
[11550.236258] Buffer I/O error on device sr0, logical block 264193
[11550.236262] Buffer I/O error on device sr0, logical block 264194
[11550.236265] Buffer I/O error on device sr0, logical block 264195
[11550.236269] Buffer I/O error on device sr0, logical block 264196
[11550.236273] Buffer I/O error on device sr0, logical block 264197
[11556.534430] sr 1:0:0:0: [sr0] Unhandled sense code
[11556.534436] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11556.534442] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[11556.534449] sr 1:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[11556.534459] end_request: I/O error, dev sr0, sector 1057008
[11556.534466] __ratelimit: 54 callbacks suppressed
[11556.534470] Buffer I/O error on device sr0, logical block 264252
[11556.534476] Buffer I/O error on device sr0, logical block 264253
[11556.534480] Buffer I/O error on device sr0, logical block 264254
[11556.534484] Buffer I/O error on device sr0, logical block 264255
[11556.534487] Buffer I/O error on device sr0, logical block 264256
[11556.534491] Buffer I/O error on device sr0, logical block 264257
[11556.534495] Buffer I/O error on device sr0, logical block 264258
[11556.534499] Buffer I/O error on device sr0, logical block 264259
[11556.534502] Buffer I/O error on device sr0, logical block 264260
[11556.534506] Buffer I/O error on device sr0, logical block 264261

```

---

