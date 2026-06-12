---
title: "Another Atheros AR242x Question"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by super.rad on 2009-03-30
Seems to be a lot of posts about Atheros AR242X lately, sorry to add another :P
Girlfriends laptop has an Atheros AR242X wireless card and the only way I have got it to work was by using [this guide]("http://ubuntuforums.org/showthread.php?p=6856294").
She's currently running Intrepid, I tried installing Jaunty on it a few months ago and followed the guide again but it didn't work (even says in the guide it works with jaunty).
Now that the beta is out I want to try installing it again but just wanted to check that the wireless would work this time, anyone know if it will?
Would rather not install it all just to find out the guide still doesn't work and have to reinstall intrepid again.
Thanks

---

### Post by andrewabc on 2009-03-30
Have you tried running livecd to see if it would connect without installing it?

---

### Post by super.rad on 2009-03-30
Yeah tried running the live cd, wireless didn't work out the box and couldn't try the guide as you have to create a file then reboot and if I rebooted the live cd the file I created would have gone

---

### Post by super.rad on 2009-03-30
it says in the guide that if using Jaunty skip steps 1 & 2, but when I try:
```
sudo modprobe acerhk
```
It can't find the module acerhk (or something along those lines)
and if I try
```
sudo modprobe ath5k
```
It makes no difference to the wireless.
Looks like I'll just have to try upgrading soon and hope for the best.
EDIT: Just had an idea, as the wireless is working now in intrepid if I just changed the repo's to jauntys and updated rather than doing a fresh install, would the wireless still work?

---

