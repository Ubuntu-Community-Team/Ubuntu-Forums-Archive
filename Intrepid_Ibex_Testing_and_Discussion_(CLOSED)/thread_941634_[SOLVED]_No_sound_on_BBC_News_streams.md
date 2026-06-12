---
title: "[SOLVED] No sound on BBC News streams"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-10-08
Just upgraded to Intrepid and lost sound on BBC News steams. Sound when using vlc player works fine with wmv files and dvds.

Any clues as to how I recover sound for BBC News streams please?

---

### Post by alienexplorers on 2008-10-08
> **bwallum said:**
> Just upgraded to Intrepid and lost sound on BBC News steams. Sound when using vlc player works fine with wmv files and dvds.

Any clues as to how I recover sound for BBC News streams please?

You need Real Player to play the BBC streaming video.  It is available in the medibuntu repositories.

---

### Post by philinux on 2008-10-08
You dont need realplayer for bbc the default install plays them fine. Or I should say did. todays updates have lost me sound. 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

This error appears when you try to Test sounds.

---

### Post by philinux on 2008-10-08
Update. Reboot fixed sound. All bbc flash and radio streams play fine. This is a screenshot of my default plugins. I'm using the default flash non free plugin from synaptic.

---

### Post by plun on 2008-10-08
I have no problem with BBC...

Its BBC Player and Abobe.

Running Adobe 10 **RC version** from psyke83's repo  (PulseAudio thread)
32 bit

[[img]http://ubuntu-pics.de/thumb/4218/bbc_TqDz2m.jpg[/img]](http://ubuntu-pics.de/bild/4218/bbc_TqDz2m.jpg)

---

### Post by bwallum on 2008-10-08
Exactly the same problem Phil, same approach with default flashplugin-nonfree but no fix. Puzzled......

---

### Post by philinux on 2008-10-08
Post what you got in ```
about:plugins
```

---

### Post by bwallum on 2008-10-08
Here's my about:plugins report...

---

### Post by philinux on 2008-10-08
I think you need to get rid of the gecko media player plugin then try the bbc.

Notice in my post #4 I have only default plugins and I've not found anything yet that I cant play.

---

### Post by jfernyhough on 2008-10-08
Works fine for me with Flash 10 RC and gecko-media-player installed - all on Firefox 3.1b2pre.

---

### Post by philinux on 2008-10-08
How come your not on FF 3.0.3?

---

### Post by craggsy on 2008-10-08
I had a similar issue, this worked for me !

[http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/)

---

### Post by bwallum on 2008-10-08
> **craggsy said:**
> I had a similar issue, this worked for me !

[http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://www.derekhildreth.com/blog/how-to-fix-the-no-sound-issue-in-firefox-flash/)

It tells me that I have the wrong architecture (for i386, I have 64bit)

---

### Post by bwallum on 2008-10-08
> **philinux said:**
> I think you need to get rid of the gecko media player plugin then try the bbc.

Notice in my post #4 I have only default plugins and I've not found anything yet that I cant play.

Tried disabling gecko media player but no joy. I can listen to BBC podcasts (i think they are MP3). What technology is the sound on BBC streaming video?

---

### Post by bwallum on 2008-10-09
Now resolved with download today flashplugin-nonfree 10.0.12.10ubuntu1.

---

### Post by philinux on 2008-10-09
Good news. Maybe it was reinstalling the flash player that helped too. I've noticed since this latest update that full screen flash is smooth at last.

---

### Post by AlexBellisBrown on 2008-10-09
BBC videos are streamed in Flash, the radio streams, however, are in Realplayer format, you need the Mplayer plug-in, or realplayer installed to use it.

Check if BBC radio 1 plays here; [http://www.bbc.co.uk/iplayer/console/radio1](http://www.bbc.co.uk/iplayer/console/radio1)

---

### Post by bwallum on 2008-10-09
> **AlexBellisBrown said:**
> BBC videos are streamed in Flash, the radio streams, however, are in Realplayer format, you need the Mplayer plug-in, or realplayer installed to use it.

Check if BBC radio 1 plays here; [http://www.bbc.co.uk/iplayer/console/radio1](http://www.bbc.co.uk/iplayer/console/radio1)
Curiously, your link did not work for me [http://www.bbc.co.uk/iplayer](http://www.bbc.co.uk/iplayer) works fine however, both sound and video as appropriate. Something to do with the 'console'???

---

### Post by bwallum on 2008-10-09
Thanks for sticking with it Phil, rgds, Bob

---

### Post by AlexBellisBrown on 2008-10-09
> **bwallum said:**
> Curiously, your link did not work for me [http://www.bbc.co.uk/iplayer](http://www.bbc.co.uk/iplayer) works fine however, both sound and video as appropriate. Something to do with the 'console'???

Dont know, it worked for me when i tried it just then, it opens the iplayer console inside of your current browser window, instead of a new window. Can you listen to radio streams though?

---

### Post by bwallum on 2008-10-09
> **AlexBellisBrown said:**
> Dont know, it worked for me when i tried it just then, it opens the iplayer console inside of your current browser window, instead of a new window. Can you listen to radio streams though?

Another update, another regression for me I'm afraid. Now back to no sound for streaming or iPlayer. That's the joy of riding the beta, you do get to find out a few things.

---

### Post by bwallum on 2008-10-11
All back again with another upgrade. Guess the sound issue is best left alone until Release. There seems to be a tussle going on between packages control of sound but I can't identify them. All default packages are working ok at the moment.

---

### Post by jfernyhough on 2008-10-11
> **philinux said:**
> How come your not on FF 3.0.3?Nightly build from ftp.mozilla.org :D Means I can have fun with the new JIT javascript engine (Tracemonkey).

---

