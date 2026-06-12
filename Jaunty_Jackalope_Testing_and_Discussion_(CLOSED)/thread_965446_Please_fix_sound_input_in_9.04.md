---
title: "Please fix sound input in 9.04"
date: 2008-10-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dcarpenter on 2008-10-31
Hello, I have had a problem with sound input in default installs for the past 3 or 4 Ubuntu releases.  In the default install on my desktop, the microphone volume has been set to zero and the analog mix input slider is hidden, as well as muted.  Both of these sliders need to be turned up in order for sound input to work on my Audigy 2 card and the fact that one is muted and one isn't even visible in volume control without a little tweaking is a major usability bug in my opinion.  The average linux novice should not have to jump through hoops to get something as basic as sound input working on a desktop oriented distribution.  You can check out my bug report [here.]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/290910")

---

### Post by Slug71 on 2008-11-01
Yeh i agree here. I think PA and Alsa both need a good kick up the ***. From Alpha 4 - RC my mic and sound worked perfect using 64bit. Whe the Final came out i decided to do a fresh install with 32bit and now my sound works fine but i cant get my mic working again. Going to go back to 64bit today until Alpha 3 of Jaunty.

EXT4, PA and Alsa need priority for Jaunty and then a new Theme.

---

### Post by Naddiseo on 2008-11-01
+1

I really want to be able to record my guitar playing again. I used to be able to back in dapper, then I got a new sound card, and haven't been able to since. I tried the PA testing back in Intrepid, and I couldn't figure out how to link audacity to my input sources. So hopefully, this release!!

---

### Post by plun on 2008-11-01
Yup......

Alsa 1.0.18 is out now.

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)


PulseAudio is still a "pig" and version 0.9.14 is within GIT...
a real mess to compile.

Using 0.9.13 for the moment from Lukes ppa...

---

### Post by Slug71 on 2008-11-01
So i got 64bit installed again and same as 32bit!?:mad:

Sound Recorder seems to be broken.
My Volume properties no longer has a Digital option which is why i think my mic is not working.

PA 0.9.13 didnt fix anything.???

The Final of Intrepid seems to have gone backwards.

Please let this be fixed with Jaunty.

---

### Post by plun on 2008-11-01
> **Slug71 said:**
> 

PA 0.9.13 didnt fix anything.???

The Final of Intrepid seems to have gone backwards.


Yup maybe....  :D

0.9.13 works better for me now and I also switched to 2.6.28-RC2

Also compiled Alsa 1.0.18

Then I broke everything with PA from GIT..:lolflag:):P

---

### Post by Slug71 on 2008-11-01
> **plun said:**
> Yup maybe....  :D

0.9.13 works better for me now and I also switched to 2.6.28-RC2

Also compiled Alsa 1.0.18

Then I broke everything with PA from GIT..:lolflag:):P


:lolflag::lolflag:
Guess i'm gonna be onboard with Jaunty from Alpha 1.

---

### Post by Gina on 2008-11-02
Yes, recording sound is yet another feature that needs looking into.

I'll be onboard with Jaunty just as soon as something is available to test. :)

---

### Post by plun on 2008-11-02
I wonder if Ubuntus packages are complete wrong built for PulseAudio :confused:

libtool and libltdl3 and libltdl7, also dev versions seems to be a challenge. 

:confused:

---

### Post by plun on 2008-11-06
For the first time in history I have glitch free sound.  :guitar:

PulseAudio ver 13 and Libasound2 broke for Luke so I compiled from GIT again.

AND it works....:)

This patch is needed
[http://www.pulseaudio.org/ticket/398](http://www.pulseaudio.org/ticket/398)

I hope Luke skips ver 13 and moves on....  Rock solid  !

---

### Post by autocrosser on 2008-11-07
Hi plun---what is the address of Luke's PPA? Do you know if he got the problems taken care of yet?

---

### Post by rudenko_ruslan on 2008-11-07
> **autocrosser said:**
> what is the address of Luke's PPA?
[PPA for Luke Yelavich]("https://launchpad.net/~themuso/+archive")? :-k

---

### Post by plun on 2008-11-07
rudenko posted the url and the ppa is also probably broken for Jaunty

Pulseaudio broke during build for Luke and also alsa-plugins

New alsa-utils seems to be out...
[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000161.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/000161.html)

I took the GIT road and the patch, hopefully Luke skips ver .13 and goes to a git version, Fedora 10 uses code from GIT for glitch free sound....  works great !   

ver .13 is alsa crazy with tons of under/overruns.

---

### Post by autocrosser on 2008-11-07
Thanks for the note--I looked at Luke's PPA & saw that libasound was running behind us, decided to wait...

Could you outline what you are doing for GIT & the links?

Thanks!!

---

### Post by plun on 2008-11-07
> **autocrosser said:**
> Thanks for the note--I looked at Luke's PPA & saw that libasound was running behind us, decided to wait...

Could you outline what you are doing for GIT & the links?

Thanks!!

Well... it seems to be "the cat and the rat" with packages...

Alsa is upgraded to 1.0.18 and PA ver .13 cannot be built.

Its also "mission impossible" for myself, also noticed earlier.


Ver .14 is within the GIT and I am sure that Fedora 10 uses this code, LennartP also works for Redhat.


GIT
```
git clone git://0pointer.de/pulseaudio.git

```

You must bootstrap for compiling.

It might also be trouble with a symlink libltbl (or what is whas)

Also this patch is needed:
[http://www.pulseaudio.org/ticket/398](http://www.pulseaudio.org/ticket/398)

Just 2 rows to change within source if you do it manual.


Today this was "poisoned" with Debian code and I have over/underruns again...  alsa-plugins.

I have then installed compiled code from Alsa.

Skip Debian maybe...:)

---

