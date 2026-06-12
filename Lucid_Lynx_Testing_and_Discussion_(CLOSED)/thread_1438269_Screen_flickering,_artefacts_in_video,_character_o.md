---
title: "Screen flickering, artefacts in video, character offsetting."
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2010-03-24
Lucid is working pretty well for me except for a few oddities that have cropped up recently.

My screen flickers occasionally. It generally flickers to black, and does it about every 5 minutes (it's not very noticeable and very quick). When it does flicker, the sound sometimes cuts for a second, or a click is heard.

Also, when watching youtube video, occasionally green dotted lines will appear down the video. This doesn't happen very often and will be fixed with a reboot (or even just waiting for a while).

Lastly, when running open office writer, some of the letters will be jumbled. They will overlap. It's usually the same letter that does it, for instance on my attachment the letter c is doing it.

My first guess is that this is a problem with the Nvidia video drivers, or my card itself. Is anyone else experiencing something like this?

I have an Nvidia GTX260. Is it worth filing a bug report maybe?

---

### Post by pressureman on 2010-03-24
I see similar symptoms to what you describe (particularly the random, infrequent flicker/corruption), although I'm using an Thinkpad 500 with Intel GM45 integrated graphics.

I don't recall having this problem with kernel package 2.6.32-15... ie. it seemed to be introduced by 2.6.32-16. It may have been something else that was updated around that time however.

---

### Post by Jacob111 on 2010-04-05
This is a longstanding issue with the Nvidia video drivers for Linux.  Of course, they're closed-source so we can't do much about it.  The flicker happens when the mobile GPU tries to switch from low to high power mode.  In the past, you could "overlock" it in the nvidia-server-settings by pegging the card to the max performance, but now that doesn't seem to work as of Lucid.

---

### Post by themusicalduck on 2010-04-05
This is strange since I didn't have the problem until I started using Lucid. Particularly the strange character offsetting.

I didn't change any of the default options to do with performance in nvidia-settings either when I was Karmic.

---

### Post by cariboo on 2010-04-06
Do you have the same problem when using the nouveau drivers?

---

