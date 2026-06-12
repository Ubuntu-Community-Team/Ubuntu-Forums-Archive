---
title: "upgrade to 8.10 atheros driver issue"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by monk3y on 2008-07-13
i recently upgraded my hardy to the new 8.10 alpha to see how the new build is coming. i ran into a couple issues though that i need help with. on upgrade my atheros driver just stopped working, i dont know why but its not even there. i would go to the package manager and try help from there by using a network canble but i was an idiot and broke my ethernet port by dropping my laptop. so i need help installing this driver. iv tried madwifi but when i try "make" it comes up with to errors. "make clean" and "make install" dont help eather. any help would be really.... well helpfull.


ps. also for some reson if i try to install the ati propritory drivers, the install finishes and i reboot my pc, but when i reboot the driver still dosent install and under screens and graphics it says none. even if i change it there on reboot it says none again. help would be appreciated!  thx in advance

---

### Post by monk3y on 2008-07-13
anyone know a solution?

---

### Post by agentsmith23 on 2008-10-22
Do you have the driver that you used in hardy? I am not sure if it will work in intrepid. If you don't have it just download it from another computer and put it on a memory card or thumbdrive and then transfer it to your laptop and try to install as you did in hardy.

Good luck, I am anticipating problems with this same issue when I upgrade in about a week or so.

I guess I should have looked at the post date before replying!

---

### Post by Sef on 2008-10-22
Moved to Ibex forum.

---

### Post by maestrobwh1 on 2008-10-22
Um, yes, Intrepid is weak with wireless atheros; it is a card that has worked since Gutsy... I have been goofing around with it for about a week now... I even installed the madwifi drivers manually.

---

### Post by Cloud79 on 2008-10-22
> **maestrobwh1 said:**
> Um, yes, Intrepid is weak with wireless atheros; it is a card that has worked since Gutsy... I have been goofing around with it for about a week now... I even installed the madwifi drivers manually.

I also have problems with atheros, using the ath5k driver. When i run 2 or 3 torrents it disconnects and then reconnects again. Over and over. I hade to disable the atheros driver and compiled from madwifi

---

### Post by piotrwoj on 2008-10-22
with ath5k d'not work kismet, airodump-ng, soft-ap. This driver is rewrite from BSD, and is not stable and funktional.

---

### Post by maestrobwh1 on 2008-10-22
> **Cloud79 said:**
> I also have problems with atheros, using the ath5k driver. When i run 2 or 3 torrents it disconnects and then reconnects again. Over and over. I hade to disable the atheros driver and compiled from madwifi

Though I do have issues connecting even with the compiled madwifi driver, it is better than the ath5k.  I hope this gets resolved, because the purpose of a laptop is to be able to be wireless.  I could just go back to Hardy but I will hold out until Intrepid gets out of Beta to see if this is "fixed."

This morning, I could not connect worth a darn... rebooted, powered off and hard booted, etc, went to work, came home and it is connected now and has been for 30 minutes.

---

