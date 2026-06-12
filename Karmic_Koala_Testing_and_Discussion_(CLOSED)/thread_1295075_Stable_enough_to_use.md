---
title: "Stable enough to use?"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gerbil.paste.sandwiches on 2009-10-19
Is it ready to use yet, or should I wait for the RC?

---

### Post by fjosh on 2009-10-19
RC?  The final version is going to be out in 10 days.

I haven't had any stability issues.

---

### Post by FuturePilot on 2009-10-19
> **fjosh said:**
> RC?  The final version is going to be out in 10 days.

I haven't had any stability issues.

Yes the RC. It's due out Thursday. See [https://wiki.ubuntu.com/KarmicReleaseSchedule]("https://wiki.ubuntu.com/KarmicReleaseSchedule")

---

### Post by fjosh on 2009-10-19
> **FuturePilot said:**
> Yes the RC. It's due out Thursday. See [https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)
Thanks, I was unaware.  *forehead smack*

---

### Post by gerbil.paste.sandwiches on 2009-10-19
Sweet I'll install the RC. Fank oo (y)

---

### Post by KrazyPenguin on 2009-10-19
I'd stick with Jaunty, Karmic is the buggiest beta i have used yet!!!
It also has the slowest boot time on my laptop.
Really, i think people upgrade just out of curiosity ( i know i do).
If you're system is working then why **** with it???

-1

---

### Post by jbslaw on 2009-10-19
Your experience may vary from mine.  The only problems I have had with Karmic are as follows:

1. The computer locked up when resuming from suspend or hibernate.  It was resolved by disabling desktop effects.  This is actually a substantial improvement over Jaunty on my Toshiba laptop, since it didn't suspend or hibernate at all under Jaunty.  It suspends and resumes very reliably now.

2. DNS lookup is seriously broken out of the box.  I edited /etc/nsswitch.conf per instructions found elsewhere on this site and specified the openDNS servers in Network Manager.  It's still a little slow, but it's usable.  

3. Networking with Windows computers didn't work because the "winbind" package wasn't installed by default.  After installing winbind, it works well.

4. Even with the installation of the proper codecs, Totem will not read a DVD movie.  This was resolved by installing VLC.  Totem is still broken today.

That's it.  Not a single lockup beside the one specified above.  Aside from Totem, no broken apps.  But read others' stories in this forum.  There's still breakage with some upgrades and with some hardware.

---

### Post by Seventh Reign on 2009-10-19
I would say, if you are TRULY worried about Stability you should probably not even consider trying an Alpha or a Beta or even the RC at any time.  If you cant risk it, wait.

---

### Post by SeanBlader on 2009-10-19
Yeah I've been holding out for the Release Candidate myself. My sound card is a little newer and has had some problems under Jaunty with PulseAudio, but everything else has been just fine. I have been getting intermittent crashes more recently with it though, which I think might be a network manager issue when switching wireless networks during the same session, but it's tough to narrow down. Otherwise my laptop doesn't have a lot of the newer high end features, like a touch screen to fingerprint reader. It does have a display port, but since it doesn't output analog, I hardly ever use it.

In any case, I'm going to get the RC running Thursday I hope. And I'd like to add that avoiding progress because of a fear of challenges can't be a fun way to go through life. And even if it's not fear but caution, sometimes you just have to throw it to the wind and give it a shot.

---

### Post by mperry on 2009-10-19
I am using it daily but then again I am not that stable myself. I tend to think of myself somewhere between the beta and the RC stage so using an OS which is there perhaps just suits me :). I have had a few issues which I relate:

Virtual Terminals would not work on my thinkpad T60. Found a fix thanks to the great company on these forums. Had to edit a file and then got it working.

Sound was a'popping. Had to edit an alsa file or something and then it was okay.

I have used it on a daily basis as a primary work laptop for some days now and not had any serious issues using it. But then again, what's serious for me may be a joke for you. You may need a bunch of stuff that I don't. I do email, wordprocessing, create openproject GANTT files, track projects online, etc. I'm a engineering manager type for a software company.

So my advice is to wait. Wait for it to reach the end game. Or, don't wait and just install it in vmware or virtualbox if you feel the need to play. I just bought a new laptop sata drive and installed it on that.

I like it. But remember the stability thing with me :)

---

### Post by kvdbreem on 2009-10-19
I think I found a bug. Scenario:

1.  Open up a tar.gz file using file roller
2.  Open up Home Folder in places (that is, get an instance of nautilus going)
3.  Drag a file inside the tar.gz file over to your opened up home folder (naultilus instance)

Expected Result:

File roller extracts the file out to your nautilus instance

Actual Result:
Naultilus instance closes unexpectedly.  Looked around in /var/log directory for any recently updated logs and couldn't find anything.

Anybody else getting this error?

Kevin

---

### Post by ikt on 2009-10-20
been extremely stable on mine since beta.

---

