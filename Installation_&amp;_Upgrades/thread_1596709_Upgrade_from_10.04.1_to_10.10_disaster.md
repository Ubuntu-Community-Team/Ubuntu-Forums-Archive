---
title: "Upgrade from 10.04.1 to 10.10 disaster"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2010-10-14
I've been a relatively happy user of Ubuntu since 6.10, but 10.10 has left me cold and ticked off. I've installed Ubuntu enough times to know what I'm doing, and I can usually fix Canonical's generally minor mistakes on my own or with a little forum help.:)

I've never been completely successful with "upgrade-manger -d", and yet I try it every time just to see if it will ever work 100%. I think not. My upgrade from 10.04.1 to 10.10 took several hours longer than  normal and when finished I rebooted into the most sluggish version of Ubuntu I ever used. Everything was totally slow and my OC'd  i7 920 cpu was  running at 80%+ with no apps running except for default system processes. According to system monitor, "gnome system monitor" was hogging most of  my cpu cycles. I then installed the Nvidia driver and upon reboot was met with a terminal prompt to log in! No pretty gui log  in screen. I let the cursor blink to see what would happen and after about 1-2 minutes or so the system decided it was going to  display a gui log in screen and I was able to log in. Now, with the Nvidia driver, everything was even slower! I couldn't believe it.

After this pain, I decided on a clean install (my /home is on a separate partition). I downloaded, checksumed and burned a 32 bit and 64 bit version of 10.10 and did separate clean installs of each. They both gave me the exact same molasses responsiveness.

I then perused this forum, to find that other are complaining of similar problem of slowness for many different reasons. I also understand there is a know problem with anyone using a Display port type monitor (I don't).

Anyway, I then downloaded and installed Linux Mint LMDE (Linux Mint Debian Edition). It installed in about 15 minutes with no issues and I have to say it's lightning fast and with a little more work will be a Distro to reckon with. I really like the concept of a "rolling release" that you install once and get continually upgraded without having to go through an often buggy repeated 6 month release cycle for the latest software. There's simply not enough time/money/personnel at Canonical to do this well on a 6 month cycle, IMO. Unfortunately, Mint LMDE still needs work and had enough issues for me that I  decided to reinstall 10.04.1 LTS.

After 3 days of major annoyance I'm back where I began and I think I'm going to skip 10.10 altogether; or, at least, until Canonical explains what's causing some of us to experience this super slow performance problem with 10.10. I know it not me or my hardware.

---

### Post by davidmohammed on 2010-10-14
sounds like you, like many others, have to manually install the 2.6.36rc7 kernel.  Don't know if someone has posted the bug report on launchpad - hopefully the kernel team will take note and backport a fix in the next point release for the 2.6.35 kernel used in maverick.

---

### Post by union two levers on 2010-10-14
It's great isn't it, i started using dapper drake i think and installation of a new version is a mixture of dread and excitement...using 10.04 lts at the moment and it is okay on my geriatric compaq evo n1015v laptop but 9.10 was a disaster , now 10.10 won't get past the 'try ubuntu without installing' screen .also got a desktop that is so old it uses a zimmer frame that runs xubuntu 9.04 fine but anything after that, well forget it...well it runs the live cd's fine and will install ubuntu 10.10 and xubuntu 10.10 but both just have big problems after installation. i can't understand how things can be so different from release to release to cause so many problems. i dual boot with XP on the compaq and many times i think why am i putting myself through this after all i need my XP to update my Tom Tom sat nav and it looks good and is user friendly.

---

