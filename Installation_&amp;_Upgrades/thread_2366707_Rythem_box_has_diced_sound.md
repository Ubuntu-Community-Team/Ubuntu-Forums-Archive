---
title: "Rythem box has diced sound"
date: 2017-07-21
forum: Installation &amp; Upgrades
---

### Post by jaxom98 on 2017-07-21
Up graded Ubuntu from 14.04 to 16.04 yesterday.
Today I tried to ply an audio cd , nogo,   It sounds as if the sound has been cut inti slices and every 2nd slice removed for the first couple of songs and it rapidly get worse over the next 1 or 2 songs and then goes silent. The progress curser telling you how much of the song is left continues to the end of the song and stops.

This happens on 2 separate computers(other 1 is a clean install 16.04) and I used 3 different cd's. 2 of the cd's are old units that have run on this(main PC) computer with earlier versions of the ubuntu OS (14.04.1 and earlier) and run text book perfect.
The up grade was from 14.04.5 to 16.04.
The new cd wouldn't run on 14.04.5. I didn't think try older cd's.
The music program is "Rythembox" (default option) , I also down loaded "banshee" music player and got the same trouble.
Any ideas?
Please keep it simple, command line is a foreign language to me.

---

### Post by BenginM on 2017-07-21
Salutations!

you want to import the audio cd first and check again:
[https://help.ubuntu.com/community/Rhythmbox](https://help.ubuntu.com/community/Rhythmbox)

lets test this to check it's not a system wild sound issue ..

do you get the same issue playing this mp3 within the browser :

[https://drive.google.com/file/d/0B8DOQR3H7mnzamhHM1FvenM5eDg/view?usp=sharing](https://drive.google.com/file/d/0B8DOQR3H7mnzamhHM1FvenM5eDg/view?usp=sharing)

another test is to download that mp3 track place it in the  Music directory and use cmus ..

[http://manpages.ubuntu.com/manpages/precise/man7/cmus-tutorial.7.html](http://manpages.ubuntu.com/manpages/precise/man7/cmus-tutorial.7.html)

sudo apt install cmus

launch cmus interminal , $ cmus

prees 5 , browse to the music directory , and play the mp3 track .. do you get the same sound issue with audio cd!

---

### Post by jaxom98 on 2017-07-22
Hello BenginM, I imported the cd and it plays text book perfect.
I followed your mp3 link and it played text book perfect.
I followed the cmus tutorial link, it was confusing and things did not happen.
The cmus has been down loaded but I don't know how to make it run. I tested the cd and no change. Still diced sound.

---

