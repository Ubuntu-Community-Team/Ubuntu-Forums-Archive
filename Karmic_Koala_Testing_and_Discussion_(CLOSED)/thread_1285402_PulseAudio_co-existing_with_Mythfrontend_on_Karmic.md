---
title: "PulseAudio co-existing with Mythfrontend on Karmic Beta"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Deborah Armstrong on 2009-10-07
Is it possible to get PulseAudio and Mythbuntu to co-exist on the same machine?
We're running the Karmic beta version of Mythbuntu because our hardware requires the latest MythTV fixes. When we 
install the ubuntu-desktop package, it breaks sound, a frequently reported bug.
We tried uninstalling Pulse-Audio  but synaptic is unable to do so. it appears PulseAudio is just too tightly 
coupled with most of gnome these days.
I looked in to just installing Gnome, but that also brings PulseAudio along for the ride. Currently, after 
restoring our backup, we have a working Mythbuntu without PulseAudio, but we really want to run the Ubuntu desktop 
on the same machine.
Electricity is expensive these days, and the goal is to have one home PC running all the tasks we need.
There are quite a few how-tos on getting PulseAudio to work well in Hardy, Intrepid and Jaunty,  but I don't know 
if these fixes would work for Karmic beta, or if they would actually fix the Mythfrontend sound.
Has anyone gotten the ubuntu-desktop to work in Mythbuntu Karmic? If so, which of the many available how-to 
documents is a reliable guide?
--Debee

---

### Post by markbuntu on 2009-10-07
I wrote some of those guides and I can tell you that they are pretty much inecessary in Karmic because pulseaudio has been so much improved and is highly integrated into the Ubuntu Desktop and Gnome that a few minutes of fooling around with the controls can give you total control of your sound. It is still possible to remove pulseaudio but it involves losing a lot and reinstalling a lot of packages that are removed with pulseaudio.

Nevertheless, I will be writing a little something up when karmic is released. A lot of stuff is still in flux and a ton of packages were recently broken and need to be rebuilt before a full update will be available, maybe you should just wait for that.

You could also try using the KDE desktop instead, KDE uses the phonon sound server instead of pulseaudio so it may work better with Myth, or it may not. 

If mythtv is still using the old and deprecated OSS api or some of the alsa api that has also been deprecated then they are in big trouble as many distros are no longer including anything oss and have removed a lot of the old ALSA functionality that has been replaced by the pulseaudio and phonon sound servers and udev. But they probably know this already.

---

