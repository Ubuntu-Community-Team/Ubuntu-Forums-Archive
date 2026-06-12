---
title: "Unable to isntall with 8800GTS"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by psikys on 2007-07-22
Okay, so I have seen a few posts on here with people having similar issues but not the same. Most of them have 1. A working knowledge of Linux, 2. Are already installed and are having video problems, or 3. Aren't using my video card.

Here is my problem. I am fairly new to linux, I have installed a few times before but the only thing I managed to do was hose the install, and instead of fixing it, I got bored and just uninstalled and went back to good ol' winders. Anyway, I have an 8800GTS, 680i Mobo, 2 gigs of Corsair xms2 ram and an e6300. I only list this because I figure a hardware profile is a good starting point. Now onto the actual issue - when I boot up from the dvd - I select the first option - start and install Kubuntu - it starts up - then takes me to a Command Line interface, no GUI. Which I wouldn't really care except I have no idea how to configure xorg.conf (or where it's located for that matter). I currently have 7.04 installed however I have no GUI because I am assuming it is not seeing my video card properly. I can use my old 7900GS and it boots to a GUI for install - but the card is toasted - overclocking for the lose - so I know theres not really an error on the OS side, it just has no idea what video card I am using.

So, if anybody has any idea how I can fix my issue, I would REALLY like to have a GUI :) I am not even super concerned about gaming right now. Wine is a whole other day of learning. 

Somebody help a noob out! Thx!:guitar:

---

### Post by Pumalite on 2007-07-22
At the command line you can try: sudo dpkg-recomfigure xserver-xorg. Most defaults will be OK. But choose 'vesa' as your driver. When finished: startx. Once you are IN the system you can worry about most appropiate driver for your card. 'vesa' is a generic driver, a jack of all trades. If that doen't work, try Alternate CD ( text mode)

---

### Post by psikys on 2007-07-22
Thx Puma - running through the wizard right now.

---

### Post by Pumalite on 2007-07-22
Glad it worked. Enjoy!

---

### Post by psikys on 2007-07-22
Now it will not use the proper driver. I installed using the nVidia Driver package, no bueno. It still uses VESA and when I edit x.conf - it doesnt matter.

Any ideas?:confused:

---

### Post by Pumalite on 2007-07-22
Do what you did before with my advise. Get IN the system. Then go to NVIDIA's site. Check the drivers for linux. Download the appropiate one. Place it in /home/<username>. Now download 'build-essential'. Make sure you have kernel-headers matching your kernel, make, automake, autoconf and latest gcc. ( you can get them all through Synaptic>Search). Once done hit Crtl-Alt-F1. Login with username and password. Then: sudo /etc/init.d/gdm stop. Then: sudo sh /home/<username>/NVIDIA-Linux-xxxxxx.run. Agree to the license. Let it compile your module. Let it reconfigure your xorg file. Once back at the command line: sudo /etc/init.d/gdm start. Voilá!

---

### Post by psikys on 2007-07-22
WOOT! I have a pretty desktop and working drivers now!

I are happy.

Now to get the sound card installed :):popcorn:

---

### Post by wdster on 2007-07-22
I used **ENVY** to get my 8600 card installed.

---

### Post by Pumalite on 2007-07-22
> **psikys said:**
> WOOT! I have a pretty desktop and working drivers now!

I are happy.

Now to get the sound card installed :):popcorn:

Glad it worked for you. Your driver will match any LCD you throw at it.

---

