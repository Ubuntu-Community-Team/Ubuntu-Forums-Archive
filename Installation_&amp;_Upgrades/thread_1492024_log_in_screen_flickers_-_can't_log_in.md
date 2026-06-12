---
title: "log in screen flickers - can't log in"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by mlykke on 2010-05-24
Hi all

I'm kind of new to Ubuntu but have been along since 8.04 - and recently updated to 10.04 - everything went smooth (except maybe my machine got a bit slower...).

So, one day I was playing around with the screen saver options and decided to set it to something like an ant crawling around with a flashlight. Still, everything works fine.

But then, after first time the screen saver activated, I wasn't able to re-log in - the log in box (or unlock box) was flickering and I couldn't type anything into it. So I had to reboot the system and now, when the log in box appears, it is still flickering and I still can't type anything into it.

I've searched high and low all over these forums and there are many posts describing similar problems but they all seem to have something to do with screen resolution. And this is not the case with me. The background image shows perfectly and is still - it is just the login box that flickers.

Maybe, if I could just do an automatic log in procedure? But it'll have to be done via the command line and I'm no genius there...

Another option is to go back to 9.10 with a new install but then I would need to back-up my documents which I'm not sure how to do via the command line.

Please, can anyone help?

---

### Post by mlykke on 2010-05-24
After doing a failsafe recovery boot-up I entered *startx* in the command line and now its like a slow-motion action: now I'm actually able to see what looked like a flashing box during normal boot: pointer turns to "loading"-icon, then back to pointer and every now and then a grey box flashes in the background and there's lots af hd-activity.

Will let it continue a while to see what happens.

How can I access any error logs?

---

### Post by Senretsu on 2010-06-17
I'm getting this too now.

I was trying to make the switch from Ubu to Xubuntu with 
```
sudo apt-get install xubuntu-desktop
```Which worked just fine. Install went smooth. I was running on Ubu 9.10 (Koala) which I had freshly installed on a partition, I got win xp on the other half of my HD.

So I wasn't entirely concerned with updating my system just yet, I just wanted to be running Xubuntu. I logged off, logged back in under Xubuntu, and the desktop ran good.

Then I restarted, and played with Windows for a bit, logged back into Xubuntu, or at least tried to; I got past the glowy Icon and then got this flickering login screen. It flickers so bad I can't type in my username and password to get past it.

I'm pretty sure it's because I updated my Nvidia drivers to the old version 173 or whatever, because I was getting errors trying to install the up-to-date drivers. But now that I did that, I can't undo it! Argh.

So can anyone walk me through fixing this?

I've dipped around in the forums here a bit and found it has something to do with the /etc/x11/xorg.conf file apparently. The only instructions I've read so far on this tells me to take that file, back it up, and then replace it with the xorg.conf file from the live CD (which I am currently writing this from) but the problem is my Live CD doesn't have an xorg.conf file in it's /etc/x11/ directory. O.o?

Right now, I'm attempting to install the proper drivers thru live CD, I'm gonna reboot and see if it fixes the flickering skreen of death. Will report back later. Hope one of you can help me =)

---

### Post by mlykke on 2010-06-20
I never managed to fix this. Had to do a new clean install...

---

### Post by technocp on 2010-06-20
you can go to recovery mode from grub selection and try with fixing xserver

---

