---
title: "cdripper / encoder in Karmic"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-09-01
So now when both kaudiocreator and grip is gone what is left?
Just tried ripperX and its not good.

What I want to do: 
* rip cd to flac
* get tags from net
* be able to specify the file name.

---

### Post by Teamgeist on 2009-09-01
Have you tried sound-juicer?

```
sudo apt-get install sound-juicer
```

---

### Post by eyelessfade on 2009-09-01
Yeah, its to simple for my taste. I like more control over the application. For instance I wan't to specify compression level, write exactly how the filename should be, not just use a premade list.

---

### Post by ezsit on 2009-09-01
I use ripperx and can do all of that. I've used ripperx for years and its always been one of the best.

---

### Post by scaine on 2009-09-01
What happened to grip?  I used that for my MP3s, but switched to sound juicer when I re-did everything as FLAC...

Worst interface in the world, but soooo flexible.  I really liked Grip.

---

### Post by seeker5528 on 2009-09-03
> **eyelessfade said:**
> Yeah, its to simple for my taste. I like more control over the application. For instance I wan't to specify compression level, write exactly how the filename should be, not just use a premade list.

Can't help you with the naming thing, but compression level is configurable. At least for ogg vorbis, I upped the compression level to something like 7 (10 being the highest).

[http://www.vorbis.com/faq/#quality](http://www.vorbis.com/faq/#quality)

Go to:

Edit --> preferences --> edit profiles...

Select the profile you want to edit.

Select 'Edit'.

Change the options in the box labeled 'GStreamer pipeline'.

EDIT: 

For flac, my profile looks like this: 

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc
```

If I read things correctly and didn't miss anything, it seems like you should be able to tack the quality option to the right side of the option line like so:

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc quality=8
```

Later, Seeker

---

