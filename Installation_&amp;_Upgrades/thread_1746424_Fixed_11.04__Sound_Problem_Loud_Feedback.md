---
title: "Fixed 11.04  Sound Problem Loud Feedback"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by RustyWyatt on 2011-05-01
Howdy Folks,

After upgrading my Lenovo T60 to 11.04 I had one problem; loud, high pitched feedback overwhelming any sound playback.  To fix this I adjusted sound related levels using "alsmixwe". In my case I turned off the "Mic Boos" input in the sound system.

To fix this problem:

1 - To learn how to navigate and make changes in alsamixer go to:  [http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)

2 - In a terminal window run " alsamixer "

In my case I did not know that the T60 even had a microphone.  I turned "MIC" way down and turned "Mic Boos" completely off.  You may want to play with your setting to tune your system for your needs.

Good Luck!

Tom

---

### Post by pandhari.gorde on 2011-05-07
hi,
i also have T60. 
what are they changes u did to solve the problem ........ i am still not figured out the problem.....](*,)

---

### Post by olyerickson on 2011-12-31
I have this exact problem: fresh install of Ubuntu 11.04 on ThinkPad T60, experiencing audio feedback when mic boost and mic volume set to "usable" levels via alsamixer.

The original poster's "solution" is not *really* a solution. The core problem is that the mic is on ALL THE TIME; setting the mic boost to 0 as suggested merely disables the mic for all use, but doesn't make it usable. 

This problem has the related effect of making the output sound "noisy" when the mic level is just below the feedback level. 

I've tried many potential solutions (so far) including (and esp.) disabling pulseaudio. Any thoughts/pointers? Seems like there is some kind of a duplex problem happening, but I don't know how to twiddle that in alsa, Maybe I should restore pulseaudio...

---

