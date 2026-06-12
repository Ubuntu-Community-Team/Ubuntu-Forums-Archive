---
title: "Some Pod Casts will not play..."
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-08-29
Some pod casts play just fine using MPlayer but some just try and use a tiny player and the sound skips... Here is one that will not work for me.

[http://linuxcrazy.com/podcasts/LC-62-zach.ogg](http://linuxcrazy.com/podcasts/LC-62-zach.ogg)

It' seems that pod casts that use ogg are not working but ones that use mp3s do. Any ideas?

---

### Post by taavikko on 2009-08-29
Opened via firefox, it plays nicely. Kept segfaulting arora.

```
mplayer http://linuxcrazy.com/podcasts/LC-62-zach.ogg
```
Plays just fine.

---

### Post by exploder on 2009-08-29
Would someone post the command they have used to set up multimedia because I can not get some pod casts to play using the instructions from the multimedia thread in the forum...

I must be missing something or doing something wrong.

---

### Post by taavikko on 2009-08-29
> **exploder said:**
> Would someone post the command they have used to set up multimedia because I can not get some pod casts to play using the instructions from the multimedia thread in the forum...

I must be missing something or doing something wrong.

Most codecs can be obtained via
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by exploder on 2009-08-29
> 
Code:

sudo aptitude install ubuntu-restricted-extras



I have that installed, still can not play the above posted pod cast...

---

### Post by taavikko on 2009-08-29
> **exploder said:**
> I have that installed, still can not play the above posted pod cast...

What does mplayer print when opened via it?
command is at my first post.

ps. u-r-e is just a meta-package.

.ogg as a file format doesn't need restricted codecs, since it's free.

---

### Post by exploder on 2009-08-29
Here is what I get when I try and play the above mentioned pod cast.

[http://img530.imageshack.us/img530/2705/screenshotlc62zachoggmo.png](http://img530.imageshack.us/img530/2705/screenshotlc62zachoggmo.png)

Other pod casts open in the browser in MPlayer like they should. I can copy the url from the pod cast in question into MPlayer and get it to play but I can not get it to play within Firefox. I don't get it...

---

### Post by taavikko on 2009-08-29
Then it's a malfunction in mozilla-mplayer.
Or what the plugin is called nowadays...

I tested with default gstreamer-backend and plugin, it worked as it should.

---

### Post by exploder on 2009-08-29
> Then it's a malfunction in mozilla-mplayer.
Or what the plugin is called nowadays...

You must be right because I used the command you provided in the terminal and the pod cast would play. It is not an issue of codecs but the way Firefox is handling them.

---

### Post by taavikko on 2009-08-29
> **exploder said:**
> You must be right because I used the command you provided in the terminal and the pod cast would play. It is not an issue of codecs but the way Firefox is handling them.

Well, then you just have to->
```
ubuntu-bug mozilla-mplayer
```

---

### Post by exploder on 2009-08-29
I tested the problem pod cast on my back up copy of Mint 7 with an earlier version of Firefox and it played in the browser just fine. I also tested with Mint 7 using Firefox 3.5 and it has the same problem as Ubuntu 9.10.

This is a Firefox issue.

Edit: If I use the user agent add on and select IE8 the pod cast works as it should in Firefox 3.5.

---

### Post by taavikko on 2009-08-29
> **exploder said:**
> I tested the problem pod cast on my back up copy of Mint 7 with an earlier version of Firefox and it played in the browser just fine. I also tested with Mint 7 using Firefox 3.5 and it has the same problem as Ubuntu 9.10.

This is a Firefox issue.

Edit: If I use the user agent add on and select IE8 the pod cast works as it should in Firefox 3.5.

Whatever the underlying cause is firefox/mplayer, report it.

---

