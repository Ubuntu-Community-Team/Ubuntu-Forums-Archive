---
title: "Flash failure"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c-m on 2009-08-22
I have installed karmic on my desktop machine along with Adobe's flash plugin.

flash worked perfectly fine (on my desktop anyway) under 9.04, but in Karmic video (on youtube, iplayer etc..) constantly pauses, though sound continues. At fullscreen the video tears and is jerky.

I am running a core2duo at 2.66ghz with 2gb ram and nvidia 6200 graphics card.

Any suggestions?

---

### Post by olskar on 2009-08-22
Sorry, no suggestions.. but;

[http://xkcd.com/619/](http://xkcd.com/619/) ;)

---

### Post by nhasian on 2009-08-22
> **c-m said:**
> Any suggestions?

yes you didnt mention if you were using 32bit or 64bit karmic?  if its 64 bit then you can grab the 64bit adobe flash from:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

the one in the repos is still 32bit.

---

### Post by miegiel on 2009-08-22
> **olskar said:**
> Sorry, no suggestions.. but;

[http://xkcd.com/619/](http://xkcd.com/619/) ;)

That's just FUD [-X

> **c-m said:**
> I have installed karmic on my desktop machine along with Adobe's flash plugin.

flash worked perfectly fine (on my desktop anyway) under 9.04, but in Karmic video (on youtube, iplayer etc..) constantly pauses, though sound continues. At fullscreen the video tears and is jerky.

I am running a core2duo at 2.66ghz with 2gb ram and nvidia 6200 graphics card.

Any suggestions?

If you're running a 64bit ubuntu try the deb in this post :
[http://ubuntuforums.org/showthread.php?p=7800146#post7800146](http://ubuntuforums.org/showthread.php?p=7800146#post7800146)

Or try the script in this post :
[http://ubuntuforums.org/showthread.php?p=7717588#post7717588](http://ubuntuforums.org/showthread.php?p=7717588#post7717588)
(make sure you correctly copy the *wget* url, it's abbreviated in the post)

---

### Post by c-m on 2009-08-23
Its the 32bit karmic.

I've just noticed that the Nvdia driver is not installed. But I cannot install it via synaptic I get a 404 error.

---

### Post by miegiel on 2009-08-23
> **c-m said:**
> Its the 32bit karmic.

I've just noticed that the Nvdia driver is not installed. But I cannot install it via synaptic I get a 404 error.

It will probably be back later. I just read something about nvidia 6000 cards in the [_Adobe Flash install information for AMD64_]("http://ubuntuforums.org/showthread.php?p=7831260#post7831260") thread. Who knows, it might be related.

When the driver is back use the script (bottom link) for inspiration on removing flash, but don't install the 64bit player of course :twisted: Then just try installing flash again.

---

### Post by psyke83 on 2009-08-23
> **miegiel said:**
> That's just FUD [-X

It really isn't. On my old laptop (Pentium M 1.5Ghz, 855GM chipset, 768MB ram), fullscreen Flash (particularly HQ content on Youtube, for instance) stutters quite badly in Karmic. I don't use compositing, and I've tried forcing hardware acceleration in the flash plugin (though not all Flash content takes advantage of this function anyway).

Using the same hardware on Windows 7 with XDDM drivers (XP drivers in compatibility mode for Windows Vista/7), the same flash content plays without stuttering.

Refusing to acknowledge the existence (or even possibility) of a bug means that it will never get fixed.

---

### Post by Kai Summers on 2009-08-23
Nothing but praise here for Flash video, I've noticed a big improvement over previous versions of ubuntu. I had just started a thread to say how pleased I was then went back to the forums and this was just next to my thread...
One persons luck is another persons sorrow...:lolflag:

---

