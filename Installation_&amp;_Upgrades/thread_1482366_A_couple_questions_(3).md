---
title: "A couple questions (3)"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by vampiremind on 2010-05-13
Hi dudes :)
I use ubuntu from a couple of year but still a newby :) 

Okey I have several questions :)
(My questions are probably kind of strange but... anyway)
Okey #1:
I've just upgrade my distro from 9.04 to 10.** and I have a problem with the sound... well my english is bad so i don't know how to explain it but its like (when you turn the volume 'over max' its sounds like sh*t... same here... but the volume its not configure as loud (... at 9.04 have no problem) 'hope you understand what I am talking about... yes?'
#2
After the update to ubuntu 10 I have problems with libraries... I've try to install 'Phun' -game and 'Algodoo'- the same sh*t but new one... okey the problem is missing libraries ... I've installed them 'no problem' but when I try to run the installation again the same error 'missing libraries' I chack symnamptic and its there installed... What is the problem ??
#3
I am looking for a program to download a mp3 from a video from youtube... any ideas ?

(And sorry again if this thread is not in the right place but as you can see the questions are very different from each other... )

---

### Post by lemming465 on 2010-05-14
> I've just upgrade my distro from 9.04 to 10.** and I have a problem with the sound
I'm not sure what the problem is.  Have you tried changing some of the settings under "Sound Preferences ..."?

> I've try to install 'Phun' -game and 'Algodoo' ... missing libraries
3rd party binary programs (if these are coming from [www.algodoo.com](www.algodoo.com) and [www.phunland.com](www.phunland.com)) can be a challenge.  They may be looking for _older_ versions of the libraries.  You may be able to figure out what they are specifically looking for by running "ldd" against them.  The first and easiest way to satisfy them would be if Ubuntu also packages older versions for you; try searching for -compat versions of your problem libraries in synaptic.  Otherwise you may have to resort to installing from older source packages which you compile yourself, or waiting for the vendor to release a newer version compatible with Ubuntu 10.04.

> I am looking for a program to download a mp3 from a video from youtube
I haven't tried it myself, but would [youtube-dl plus ffmpeg]("http://ubuntuforums.org/showthread.php?t=855433") help?

---

