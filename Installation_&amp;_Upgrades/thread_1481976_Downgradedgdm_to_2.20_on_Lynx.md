---
title: "Downgradedgdm to 2.20 on Lynx"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by JohannesD on 2010-05-13
Hi!
I am trying to downgrade gdm to Version 2.20 because I want to create a multiseat setup. I already did this with Ubuntu 9.10, but with Lynx, I get an error...

What I did:
- Downgrade gdm: Since gdm 2.20 seems not to be in the repositories anymore, I downloaded the deb-Package from the website. First I removed gdm. When installing 2.20, I get an error, that libdmx1 is not there. So I installed it, and after that installation of gdm 2.20 works.

- I replaced xorg.conf and gdm.conf by the files, that I used on my previous multiseat (on Ubuntu 9.10). 

Now, when I boot up I get a message, that there is already a X-Server running on Device :0 (This is my original message in german: "Anscheinend läuft bereits ein X-Server auf Anzeige :0. Soll eine andere Anzeigenummer ausprobiert werden? Falls Sie mit nein antworten, wird erneut versucht, den Server auf :0 zu starten."). 

Even if I disable the second server setup in gdm.conf (so only one X should be started), I get the same error. The error is shown on Terminal 8, while on 7 there is still the Ubuntu logo with the read dots going from left to right.

Does anybody know what I can do to get the thing working? Strange thing: I upgraded the Ubuntu 9.10 multiseat system and it works! Only on the clean install, I get this problem.

Thanks in advance,
Johannes

P.S. I attached my xorg.conf and gdm.conf

---

### Post by dino99 on 2010-05-13
i really dont know if you can do that with lucid: 2.20 is quite old now as we have 2.30, so that mean lot of issues with dependencies (directs an recursives ones)

need to know which distro was using 2.20, then maybe temporarely change the sources.list, update [COLOR="Blue"]but only force the gdm 2.20 package[/COLOR], then revert back to lucid with the sources.list and update again the cache.

trying this after booting in recovery mode should be better.

---

### Post by JohannesD on 2010-05-13
.- change the sources.list, update but only force the gdm 2.20 package

Ok I will try that. I think it was in 9.04

I just had another idea. On the second seat, I have an autologin. Do I really need gdm to autologin this user? Can I instead directly start the X sesstion on one screen with a startup skript, while the other shows the gdm? Then I could use the new gdm because it would not be necessary to start it twice.

Thx,
Johannes

---

