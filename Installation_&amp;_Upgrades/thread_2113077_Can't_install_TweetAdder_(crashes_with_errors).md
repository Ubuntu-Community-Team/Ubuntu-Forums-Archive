---
title: "Can't install TweetAdder (crashes with errors)"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2013-02-06
Hey folks,

I'm just trying to install the Linux version of tweetadder on Ubuntu 32 bit. Their readme says:
> 
Make sure that TweetAdder3 is executable!


Tweet Adder Requires the following dependencies:

x86-based Linux distributions with GTK+ 2.8 (or higher)
glibc-2.4
CUPS (Common UNIX Printing System)
libstdc++.so.6
libstdc++.so.5
libcurl with all external dependencies ([http://curl.haxx.se/docs/libs.html](http://curl.haxx.se/docs/libs.html))


*On 64-bit Linux installations the ia32-libs package must be installed

so I set the binary as executable and did:
sudo apt-get install libc-bin cups libstdc++5 libstdc++6 libcurl3

Is this right? When I try to run it, I just get masses of errors repeating:

```
(TweetAdder3:17095): Gdk-CRITICAL **: IA__gdk_gc_set_rgb_fg_color: assertion `GDK_IS_GC (gc)' failed

(TweetAdder3:17095): Gdk-CRITICAL **: IA__gdk_draw_layout: assertion `GDK_IS_DRAWABLE (drawable)' failed

```

The window comes up, but immediately crashes. Any ideas?

---

### Post by sprintexec on 2013-05-02
I don't know how you got on with Tweetadder 3? I've just tried to install Tweetadder 4 under ubuntu 12.04LTS and found that this crashes all over the place. There do not seem to be very many people commenting on using this software when run under 'nix. I'm not sure what to make of this?! :(

---

### Post by Ubuntiac on 2013-05-26
Ironically, I found I got much better results with the Windows version in wine, than with the Linux version :-|

---

### Post by Ubuntiac on 2013-06-28
Ok, so I'm banging my head on the wall with this one again (this time with TweetAdder4). The culprit seems to be TweetAdder not finding libwebkit and libgtkhtml as the first output in the console when it runs is:

> Could not load libWebKit
Could not load libGtkHTML

Now I'm pretty sure that this is probably because TweetAdder is a 32 bit binary and I'm on a 64 bit system and it's looking for 32 bit versions of these binaries. I thought installing lib-ia32 or whatever it's called should cover missing 32 bit libs, but maybe it doesn't have those specific ones... I have every likely looking candidate installed, which in libgtkhtml's case is pretty obvious.

Any ideas, anyone?

---

