---
title: "Vlc 1.0.2"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-09-23
VLC 1.0.2 was released today. Bugfix release.

Any chance of getting it in?

I'm on jaunty and a PPA had updated to 1.0.2
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

Should I file a bug report (FFE)?

---

### Post by froggyswamp on 2009-09-23
That would be great although I think filing an ultimatum would be more effective :)

---

### Post by mc4man on 2009-09-25
They've added 1.02 for i386 installs, though like the korn build several things that could be enabled aren't.

If you wanted vlc from a repo or ppa then I'd go with the repo version, there's no notable difference

Seeing that they've split i386 and amd_64 it's curious that the dmo loader is still not enabled, though atm it's usefulness in vlc 1.X.X is limited.

(The new 'native support' for wmap thru libavcodec seems to have some issues in the current karmic ( though  has worked perfectly in vlc 1.0.0  -> 1.1 git in hardy for quite some time


Am curious if anyone using the repo or korn ppa gets audio cd info,
 To test you need to change the setting in prefs for Privacy/Network Interaction from manual to 1 of the other 2 choices

---

### Post by andrew.46 on 2009-09-26
Hi mc4man,

> **mc4man said:**
> Am curious if anyone using the repo or korn ppa gets audio cd info,To test you need to change the setting in prefs for Privacy/Network Interaction from manual to 1 of the other 2 choices

Well, I compiled my own and I attach a screenshot of the cddb info coming through...

Anrdrew

---

### Post by Teamgeist on 2009-09-26
It's in already.

[https://lists.ubuntu.com/archives/karmic-changes/2009-September/009605.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/009605.html)

---

### Post by mc4man on 2009-09-26
> Well, I compiled my own and I attach a screenshot of the cddb info coming through...


Same here, though I don't see it when testing the repo and or korn ppa 1.02 build's

Andrew - have you found the 'native' avcodec decoding of wmap to be working? It works here (hardy). though on karmic there are frame errors, ( had to move wmap back to dmo for the moment on karmic for 1.02 and 1.1

(both mplayer and ffplay have no such problems on karmic



Edit;
for those curious about the native wmap support in 1.02+ it will be implemented based on this if
#if LIBAVCODEC_VERSION_INT >= AV_VERSION_INT( 52, 35, 0 )
The current error in karmic is seen here
> 0xb7b03c28] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
[0xb7b03c28] avcodec decoder debug: Using 196608 bytes output buffer
[0xb7b03c28] main decoder debug: using decoder module "avcodec"
[0xb7b03c28] main decoder debug: TIMER module_need() : 441.971 ms - Total 441.971 ms / 1 intvls (Avg 441.971 ms)
[0xb7b03c28] main decoder debug: thread started
[0xb7b03c28] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x922aa80] qt4 interface debug: Updating the geometry
[0x922aa80] qt4 interface debug: Updating the geometry
[0xb7b00e40] main input debug: `/home/doug/Desktop/wmat/wpro.wma' successfully opened
[0x922aa80] qt4 interface debug: New caching: 0
[0x922aa80] qt4 interface debug: New caching: 0
[0xb7b00e40] main input debug: Buffering 0%
[0xb7b00e40] main input debug: Stream buffering done (425 ms in 9 ms)
[0xb7b00e40] main input debug: Decoder buffering done in 0 ms
[0x922aa80] qt4 interface debug: New caching: 100
[0x922aa80] qt4 interface debug: New caching: 100
broken frame: channel len > samples_per_frame
broken frame: channel len > samples_per_frame

edit;
resolved the native support for wmapro to some extent. Appears to be related to the ffmpeg -r, currently using r19777 in karmic and it works as expected. ( as will any -r less than 19777 that's wmapro enabled either in the source or thru wmapro patch (r < 19724 or thereabouts for patch

---

### Post by andrew.46 on 2009-09-28
Hi mc4man,

> **mc4man said:**
> Andrew - have you found the 'native' avcodec decoding of wmap to be working?

The script I used to compile vlc 1.0.2 has a choice of using a static FFmpeg which is the 0.5 release or compiled against the system FFmpeg. Since I am more of an MPlayer user I played it safe and compiled against the older version...

Andrew

---

### Post by mc4man on 2009-09-29
It would appear (unless I'm missing something) that vlc will have a hard time 'keeping up' with the constant changes in ffmpeg in this regard (wmapro support and maybe elsewhere

One of the .c files for wmapro in ffmpeg keeps changing ( only a guess as to that is the cause.

The ironic part for a 32 bit install is that if vlc 1.0.2 detects a libavcodec  =>  52.35. 0 then it will switch from a working dmo to avcodec which may not work depending on the ffmpeg -r

mplayers approach to libav*'s, ect. is far superior ( though I'm sure there are valid reasons why vlc doesn't do likewise or supply a working -r in the source

---

