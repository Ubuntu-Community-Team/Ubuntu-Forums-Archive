---
title: "Gnome won't start if sound is working"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by patrac on 2005-04-14
Hi
I have a Pentium 2 with Matrox G100 and Soundblaster Vibra 16 ISA PNP. After I had installed Ubuntu 5.04 the sound didn't work. I wrote isa-pnp, soundcore, snd-sb16, snd-pcm-oss, snd-seq-oss, snd-mixer-oss to /etc/modules and when I rebooted the comuter a drumsound was played at the login-screen. But when I tried to login Gnome woudn't start. The splashscreen showed up and a sound played but it sounded like it stopped before it was finished. And then nothing happens, not even after 10min. If I remove the lines from /etc/modules gnome would start or if I login with a new user that don't belongs to the audio group. Gnome failsafe don't work either but I can log in with only a terminal and play some sounds through Gnome's sound-recorder. What can I do to make it work?

---

### Post by wrochal on 2005-04-14
Hello,

Look in article: [http://www.linuxit.com.br/blog/?p=54](http://www.linuxit.com.br/blog/?p=54) 

Or

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) 

 \\:D/ 

Tks,

---

### Post by patrac on 2005-04-14
Thanks for the information!
I've just wonder what can be wrong. Is it that I use alsa-modules insted of oss(is there oss for 2.6)? Is esd wrong configured?

---

