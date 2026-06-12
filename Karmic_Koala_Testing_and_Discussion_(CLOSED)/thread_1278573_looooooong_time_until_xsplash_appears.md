---
title: "looooooong time until xsplash appears"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-09-29
I am not sure if this is how it should look like, but I stare at a blinking cursor for 45 seconds until I see xsplash. Should this be considered normal? Heres my bootchart - maybe someone with more knowledge sees something.

---

### Post by zacbarton on 2009-09-29
Yea I'm still wondering if we are waiting for X to be started earlier or not?

---

### Post by barrieluv on 2009-09-29
Running Alpha 6 (all updates applied) on an Eee 900 Celeron 8GB Class 6 SDHC.

I don't know how to get a bootchart, but when GRUB comes up, it goes through the ten second countdown and then it stays on that screen for a good twenty seconds longer before anything else happens.  If I hit enter to skip the countdown, it still waits twenty seconds before proceeding.  I assume it will be sorted eventually, though...

Eveything, and I mean everything, else works. :)

---

### Post by | MM | on 2009-09-29
Yea, I spend most of my boot looking at the console printing stuff about fsck and keymaps and fonts and the like.  Xsplash starts but only really shows for a short while until gdm.

---

### Post by gagnon88 on 2009-09-29
Same issue here, a bootchart as long as my arm,

EDIT: Over 85 seconds boot-time

---

### Post by gagnon88 on 2009-09-29
> **barrieluv said:**
> I don't know how to get a bootchart...

Sorry about the double-post, but it would be nice if people could confirm there is a serious issue with boot duration.

For those interested, just "apt-get install bootchart", reboot and get the chart(s) from /var/log/bootchart.

---

### Post by Technoviking on 2009-09-29
Seeing the same thing also, has anyone check to see if there is a bug filed?

T-V

---

### Post by screaminj3sus on 2009-09-29
same problem here, really annoying.

---

### Post by Squonk07 on 2009-09-29
Yep. Same here. Is there a bug report? Or should we just wait until the beta on Thursday?

---

### Post by barrieluv on 2009-09-30
@ gagnon88, thanks for that.
Here's my bootchart for those interested:

---

### Post by moviemaniac on 2009-09-30
Same here too. Except that I've got usplash mingled into the whole thing :D
At least my machine boots into tty7 instead of tty1 per default again

---

### Post by Eversmann on 2009-09-30
Yeah, same problem here too... i'll check to see a bug report.

---

### Post by Tibuda on 2009-09-30
Off-topic: Have you guys noticed that now bootchart displays login manager and user session processes?

---

### Post by Elfy on 2009-09-30
> **danielrmt said:**
> Off-topic: Have you guys noticed that now bootchart displays login manager and user session processes?

Hadn't noticed that - all I can see at the moment are the extra 60 secs I have now:)

Not sure if anyone else is also seeing the GRUB loading message for 20-30secs before the actual menu appears?

If I knew enough about the bootchart output I would sit down and compare them, see if there was a common thing.

---

### Post by jocko on 2009-09-30
> **forestpixie said:**
> Not sure if anyone else is also seeing the GRUB loading message for 20-30secs before the actual menu appears?
That's probably bug [420933]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933").

---

### Post by Elfy on 2009-09-30
> **jocko said:**
> That's probably bug [420933]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933").

That was my thinking, after reinstalling grub2 so that it is on the same partition and drive as / there was no change.

Not that in the long run I am that worried - so boot is longer for me - once a day ;) of course I understand also that might be more of an issue for other people.

---

### Post by mick222 on 2009-10-01
Really annoying grub takes ages to load then i get some error messages before xsplash appears.

---

