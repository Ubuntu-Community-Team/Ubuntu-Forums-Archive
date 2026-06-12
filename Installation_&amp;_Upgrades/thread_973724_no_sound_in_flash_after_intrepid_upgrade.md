---
title: "no sound in flash after intrepid upgrade"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by malixor on 2008-11-07
Since upgrading to Intrepid I've found my alsa audio system completely hosed. I had to change settings in audacious and mplayer to get them to play audio again through alsa. Now I find that flash doesn't have sound. I uninstalled my old flash plugin and reinstalled the new one through the reop and that didn't help. My system sounds also do not work, and the test buttons don't play anything except when OSS is selected. However my system sounds did not work for the past version or two of ubuntu as well... I just didn't notice or care at the time. But flash audio is a must! Anyone figure this out correctly yet? I haven't seen a proper solution.

---

### Post by Partyboi2 on 2008-11-07
Maybe try installing flashplugin-nonfree-extrasound from the ubuntu repo.

---

### Post by malixor on 2008-11-10
Tried it and didn't work. From the description, that tries to get flash to fall back on esound or OSS for audio. Looking at the problem further, it seems Pulse has really screwed up audio everywhere that uses it and I get crackling sounds as a result. So I have more problems instead of less.

---

### Post by tedemang on 2008-11-10
Hi all,

This is exactly what I'm getting as well.  Trying to put together a new AMD X4 Phenom 9850 machine and while I can get sound when playing an .mp3 or a video file, I can't get any sound at all from Flash in Firefox or Youtube.  Also, as noted about, I can't get any System Sounds.

Here are the sound cards tried so far:

(1.)  Soundblaster Live! 5.1 
(2.)  Soundblaster PCI Express X-Fi Extreme Audio
(3.)  Motherboard/Integrated ECS8200A (Nvidia-based)
(4.)  Xitel Hi-Fi Link AN1 (USB)

Of these 4, I'm really shocked right now that Ubuntu 8.10 doesn't seem to recognize the SB cards at all.  Also, I'm seeing the same behavior with Linux Mint 5R1 and DreamLinux 3.5 RC4 (they are debian-based too).

Anyone else have an idea for either System Sounds or Flash in Firefox?  If I can figure this out, I won't have to install Windows on this machine at all. (yea!)

thanks,
Garrett

---

### Post by tedemang on 2008-11-11
Update - Have actually just had a couple of bits of success on getting audio to work.  Here are a couple of things that I've learned:

(1.)  The X-Fi cards have (amazingly) had very poor driver support.  So bad that Phoronix just reported on 11/06/08 that they have been "forced to capitulate" and have open-sourced their driver.  ...This is amazing to me since, as far as I know, that is basically the leading line of audio cards in the U.S. if not the world.  ...The source code was released this past weekend and we can expect some good updates soon, but they aren't here yet.  Also, my card was one of the new ones that is PCI Express (~$60).

(2.)  So, since it became apparent that the best strategy to get sound in Linux was to go with the older/more mature products, I swapped in an old Soundblaster Live! 24 card and that was detected during the initial install and did work.

(3.)  In fact, when I first heard the familiar bongo-drums and login System Sound, I was pleasantly surprised.  This got better when I ran through a script of the "[Ubuntu 8.10 Perfect Desktop]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10")" from HowTo Forge.  ...Specifically, there's a big blob of code on the 3rd page that installs most of the minor app's & plug-in's.  

You need to copy-paste that into your Terminal, edit out a few app's that don't have updates in the repositories (Opera was one for me), and execute it.  Once I did that, I even had Flash working for Google Videos, etc.

(4.)  However this morning, I got re-grounded after running some of the updates from Update Manager.  Something changed how Ubuntu detected the Soundblaster Live! or maybe the card is malfunctioning.  Now, it doesn't detect even the card and I get the red cross through the speaker on the notification area with a message that no devices are present.

p.s. One last note:  A big question has always been, what's a good card to get to use with Linux?  From a lot of googling, it sounds like the Audigy and Audigy2 cards might have the best support at this time.

Has anyone else also found this to be true?

---

### Post by malixor on 2008-11-11
To prevent from getting the 2 second crackling noise at login, on my laptop I muted the PC-Speaker channel using gnome-alsamixer. After logging in, if I then "killall pulseaudio" I can get proper sound from flash again. But I don't get any benefit of having sound sources mixing from flash and audacious simultaenously. This is just a temp fix but hardly a solution. I hope the devs come up with proper updates for this pulseaudio cludge soon!!!

---

### Post by psyke83 on 2008-11-11
Follow steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide to ensure you have a clean PulseAudio configuration.

Afterwards, ensure that your PCM mixer is not muted or set to 0% volume:
```
$ alsamixer -Dhw
```

---

### Post by malixor on 2008-11-11
Did exactly what you said psyke83 and I have audio playing but with the loud crackling sounds. Any other ideas?

---

### Post by malixor on 2008-11-20
bump... still not fixed

---

