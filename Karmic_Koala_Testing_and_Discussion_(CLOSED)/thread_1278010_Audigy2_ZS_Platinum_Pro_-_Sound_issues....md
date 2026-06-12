---
title: "Audigy2 ZS Platinum Pro - Sound issues..."
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Menthu_Rae on 2009-09-29
Hey everyone,

Wondering if people can help me out please? Basically in Jaunty I had my soundcard set up via SPDIF to a Dolby Digital/DTS Decoder.

**In Jaunty** - normal sounds (Flash, Movies with 2ch Stereo, Music, etc) would run in the standard stereo mode, and when I played a movie with DTS or DD5.1 output, the SPDIF stream would switch and send it to my decoder (via SPDIF output in VLC).

**In Karmic** - This doesn't happen. I get DTS/DD5.1 via VLC, and sound via rhythmbox... but I have no sound from flash or any other "normal" programs that would output **stereo sound**...

I did manage to fix it, by running alsamixer and adjusting all the volume levels to maximum. However, this did not last... It was working fine yesterday, but it seems after suspending or rebooting my PC, the sound just decides to do whatever it wants.

[LIST]
[*]DTS/DD5.1 *works*
[*]Rhythmbox stereo output *works*
[*]Flash sound **doesn't work**
[*]Other stereo sound outputs **don't work**
[/LIST]

Can someone please guide me as to what I should be looking at? I've adjusted everything I can via **alsamixer**/asound.state, **pavucontrol**, etc... but no dice except for that one time it worked yesterday :(

---

### Post by khelben1979 on 2009-09-29
Regarding flash: what version of flash are you using? (just right click on a YouTube window)

Maybe you need to run alsaconf every time you boot up the system? Have you tested this?

Also, since Karmic isn't finished yet, I think you can expect it to work worse than Jaunty.

---

### Post by Menthu_Rae on 2009-09-30
> **khelben1979 said:**
> Regarding flash: what version of flash are you using? (just right click on a YouTube window)

Maybe you need to run alsaconf every time you boot up the system? Have you tested this?

Also, since Karmic isn't finished yet, I think you can expect it to work worse than Jaunty.

Hey mate, thanks for the reply.

Using flash **10.0.32.18** 64-bit (from Adobe Labs). Flash is **not** the issue though.

**alsaconf** doesn't exist in Karmic from what I can see.

Yes, it's an alpha - but I have no idea what settings are getting changed and how I can fix it? I can accept that it may not be perfect and I may lose my settings - but I can't accept that I have no control over those settings when I need the control (as exhibited by me fixing it via alsamixer, and then that same solution NOT working the next day!)...

So - anyone else got any ideas or the same issue? :confused:

---

### Post by ranch hand on 2009-09-30
I haven't a clue about your problem but I can tell you that in looking at config files for some other things they are calling for files that do not yet exist.

Stuff works but maybe not as you would expect.  Be cool.

We are still a month out from release.

---

### Post by Menthu_Rae on 2009-09-30
> **ranch hand said:**
> I haven't a clue about your problem but I can tell you that in looking at config files for some other things they are calling for files that do not yet exist.

Stuff works but maybe not as you would expect.  Be cool.

We are still a month out from release.

No need to be cool- **I managed to fix it!**

OK, so if anyone is having this issue:

* Check your sound levels in alsamixer, ensure that PCM/Master and IEC958 are all at their max/desired output
* Ensure that your programs (in my case VLC) have SPDIF output enabled
* Ensure that within the Pulseaudio control panel (right click on speaker icon --> Sound Preferences --> Hardware --> **Profile: Analogue Stereo Duplex** [yes, even if you are using **digital** output, choose analogue!]

So I now have sound in flash, sound in stereo movies via VLC and 5.1 Dolby/DTS sound via VLC in movies that support it - **all via SPDIF** :) :popcorn:

---

### Post by Menthu_Rae on 2009-10-22
[SIZE="3"]**EDIT2:** Confirmed it's VLC. Version 1.0.2-1ubuntu**1** is **fine**, whereas 1.0.2-1ubuntu**2** is stuffed! I removed VLC completely, added the version from the c-korn PPA (1.0.2-1~ppa1~karmic2) and now SPDIF is back to working again![/SIZE]

[SIZE="3"]**EDIT:** Definitely something changed in VLC! Playback via XBMC is perfectttttt! :popcorn: Time to huntdown a previous version of VLC and maybe submit a bug report...[/SIZE]


[COLOR="Silver"]Dammit it's broken again! :mad: Some updates came through last night and I didn't touch anything - yet it's broken!

It seems like something has changed in VLC perhaps, since the "Audio Device" option is now greyed out :confused:

Doing what I said in the previous post didn't fix it, nor did mucking around with the pulseaudio daemon.conf, alsamixer, or anything else :(

Oh well, everything will have to run via 5.1 analogue now I guess.[/COLOR]

---

