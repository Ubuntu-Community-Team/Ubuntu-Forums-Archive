---
title: "DeVeDe fails due to Mplayer/mencoder"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tymanthius on 2009-10-13
When I start Devede it says it can't find mplayer or mencoder.  

So I start mplayer & get:

```

mplayer: symbol lookup error: mplayer: undefined symbol: codec_wav_tags

```

Same thing on mencoder, not surprisingly.  

I've read the thread that links to the script to build it yourself.  That didn't work, and I don't really want to build it myself.

This just started recently, but I"m not sure exactly when.  

I've also tried installing the ppa version of mplayer (2:1.0~rc3+svnXXXX).

Still no joy.  Is the ONLY way to get this to work via building it myself?  Or does we expect it fixed by the release date?

---

### Post by tymanthius on 2009-10-22
Ok, so we are in the RC, but this is still broken.  I've figured out that it has to do with the 'extra' codec packages.  Apparently the ones not marked extra work.  

Anyone have a clue?

---

### Post by mikedep333 on 2009-10-23
I installed devede and I have a bunch of the "extra" codec packages installed. Mplayer and devede work fine for me. I have the latest packages installed.

---

### Post by tymanthius on 2009-10-23
Ok, so it seems I may need to just do a full reinstall as something else seems borked on my system.  No biggie, I just wanted an idea about what to do.

That's what I get for playing with Alpha's.  ;)

Although, honestly I have very few problems even with the Alpha releases.  This was the ONLY persistant one.

---

### Post by Seventh Reign on 2009-10-23
This happens with Mencoder every few months ...

---

### Post by eluminx on 2009-10-23
You probably have the same problem i did, and it has to do with openshot.  Check this out [http://ubuntuforums.org/showthread.php?t=1281367]("http://ubuntuforums.org/showthread.php?t=1281367") and also this might help [https://answers.launchpad.net/openshot/+faq/723]("https://answers.launchpad.net/openshot/+faq/723")  Hope that helps, it did for me...

---

### Post by tymanthius on 2009-10-24
Yea, gonna just to the reinstall after stable.  Nothing here I care about, as I have a 2nd drive for data.  :)

---

### Post by mc4man on 2009-10-24
The repo version of mplayer uses the system ffmpeg shared libs (libavcodec, libavformat, ect.

so this error 
> mplayer: symbol lookup error: mplayer: undefined symbol: codec_wav_tags

is just indicating that mplayer and those shared are incompatible. 

While this could certainly be from the borked Openshot ppa versions, it would also likely occur if one built or picked up from a ppa perfectly good shared ffmpeg libs. 

The karmic repo mplayer/mencoder is best used with the karmic repo ffmpeg shared libs (or a very close revision

---

