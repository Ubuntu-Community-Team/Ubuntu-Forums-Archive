---
title: "So, what makes Karmic different from Jaunty?"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by timmy334 on 2009-08-09
I ran Karmic in VirtualBox and I didn't see any difference except for the GDM, Empathy, Ubuntu One, and default Ext4. So, what is the big deal with Karmic? I see nothing new. There are newer versions of some apps, but that could be accomplished with an update in Synaptic. I'm not trying to be a jerk. I am seriously asking, what is the difference?

---

### Post by phenest on 2009-08-09
I think a lot of stuff is under the hood. As with every new release of Ubuntu, included is the latest cutting edge kernel, which provides improved hardware support.

---

### Post by snowpine on 2009-08-09
Hi Timmy, the main difference is that all packages/applications will be about six months newer. It is evolutionary, not revolutionary. :) Also keep in mind that Karmic won't be released until October, so some of the more noticable changes (like new artwork) haven't happened yet.

Read more here: [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

---

### Post by OliW on 2009-08-09
There should be some revolutionary improvements too. usplash is being dumped. Or that was the plan. It may have changed. Should be awesome.

[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot)


Pulseaudio improvements are also here (and still improving)


But yes, the wave of other changes may be small individually, but together they mark another big overall improvement. It's amazing the speed things are improving.

---

### Post by phenest on 2009-08-09
Especially when you consider previous alphas have been unstable, and I've seen lots of comments about how stable Karmic is already. That spells good news for Karmic when it's released.

---

### Post by wayne_cat on 2009-08-09
> **phenest said:**
> Especially when you consider previous alphas have been unstable, and I've seen lots of comments about how stable Karmic is already. That spells good news for Karmic when it's released.

+1

I'm using a Karmic installation that started as an Alpha 1 install ... never needed a new installation ... no big problems. I would like to know what they are doing better this time ... better project management ... better quality management ... more tests before they release fixes or new versions?

the specs list ... I would not say that there is no difference between Jaunty and Karmic:

[https://blueprints.launchpad.net/ubuntu/karmic/+specs](https://blueprints.launchpad.net/ubuntu/karmic/+specs)

---

### Post by OliW on 2009-08-09
> **phenest said:**
> Especially when you consider previous alphas have been unstable, and I've seen lots of comments about how stable Karmic is already. That spells good news for Karmic when it's released.

If they are still planning to overhaul the boot process, there is still significant scope for exciting quantities of breakage.

---

### Post by slakkie on 2009-08-10
For me the biggest change is KDE4.3 instead of 4.2

---

### Post by olskar on 2009-08-10
> **wayne_cat said:**
> +1

I'm using a Karmic installation that started as an Alpha 1 install ... never needed a new installation ... no big problems. I would like to know what they are doing better this time ... better project management ... better quality management ... more tests before they release fixes or new versions?

the specs list ... I would not say that there is no difference between Jaunty and Karmic:

[https://blueprints.launchpad.net/ubuntu/karmic/+specs](https://blueprints.launchpad.net/ubuntu/karmic/+specs)


Less changes equals less problems ;)

---

### Post by rajeev1204 on 2009-08-10
Empathy default IM instead of pidgin

super fast graphical boot with a beautiful usplash

newer applications including ff 3.5 as default

new artwork and UI(hopefully)

Improved kernel handling 

Some new nautilus tweaks(not sure about that)

Reworked notifications

IMproved sound preferences dialog and newer pulseaudio

EXT 4 is default

Encripted home directory option in installer

And a few more i probably forget.

Squeaky clean,shiny new :)

---

### Post by phenest on 2009-08-10
> **OliW said:**
> If they are still planning to overhaul the boot process, there is still significant scope for exciting quantities of breakage.

Not really. I'm using Grub2 on Jaunty as well, and it seems fine. I think the breakage comes when users that decide to tweak it, not fully understanding how it works.

And I've also found Ext4 to be reliable and stable, not to mention speed increase.

---

### Post by Seventh Reign on 2009-08-10
> **rajeev1204 said:**
> Empathy default IM instead of pidgin

super fast boot

newer applications including ff 3.5 as default

new artwork and UI(hopefully)

Improved kernel handling 

Some new nautilus tweaks(not sure about that)

Reworked notifications

IMproved sound preferences dialog and newer pulseaudio

EXT 4 is default

Encripted home directory option in installer

And a few more i probably forget.

Squeaky clean,shiny new :)

You forgot the most important addition.

[U]Wont lock up when Deleting large/large numbers of files.
[/U]
I doubt we'll see a new UI until Gnome 3 is introduced officially for 10.04/10.10

---

### Post by OliW on 2009-08-10
> **phenest said:**
> Not really. I'm using Grub2 on Jaunty as well, and it seems fine.In order to get X starting *right* at the beginning of the boot process, there is going to have to be a LOT of juggling.

It's a lot more work than what has been done so far. And a lot more complicated than just using GRUB2.

---

### Post by fjosh on 2009-08-10
Don't forget the (hopeful) improvement for those running integrated Intel video chipsets.

---

### Post by OliW on 2009-08-10
> **rajeev1204 said:**
> super fast boot

**This is not in the specs for Karmic. This is for Karmic+1.**

---

### Post by phenest on 2009-08-10
> **rajeev1204 said:**
> Encripted home directory option in installer

I haven't seen this. But it would be nice

---

### Post by meborc on 2009-08-10
> **phenest said:**
> I haven't seen this. But it would be nice

i guess it only appears when you have specified a /home partition in the partition manager in installer

---

### Post by rajeev1204 on 2009-08-10
> **meborc said:**
> i guess it only appears when you have specified a /home partition in the partition manager in installer


Hmm yes that true, only the home directory can be encrypted.Which is where we are going to store our important files anyways so makes sense.But i got annoyed with it asking for password for mounting the home so i reinstalled.

**Keep in mind,the encryption is very difficult to remove manually,so i had to reinstall as i didnt want to mess up my data.**This feature is for those who want secure setups so in case the hard disk is stolen,the data cant be recovered if you dont know the passphrase.So dont forget the passphrase(this is not password) and its recommended to write it down someplace safe.Or its impossible to login.(For regular users like me) :)

I did that with the alternate installer btw,so probably someone with a live cd can confirm if its there too.

---

### Post by rajeev1204 on 2009-08-10
> **OliW said:**
> **This is not in the specs for Karmic. This is for Karmic+1.**

It is there for karmic too,an improvement from jaunty incremental.

---

### Post by OliW on 2009-08-10
> **rajeev1204 said:**
> It is there for karmic too,an improvement from jaunty incremental.

I don't want to get too wound up in this but it's just prep (getting X loaded in the first 2s) for real boot optimisation in J+1. 

I'm sure they won't sidestep any low hanging performance improvements but the real work is just going into the boot order for now.

---

### Post by inportb on 2009-08-11
KDE 4.3.0 is pretty awesome. The new default theme (Air) is immediately apparent upon KDM load :P

---

### Post by novafluxx on 2009-08-11
> **inportb said:**
> KDE 4.3.0 is pretty awesome. The new default theme (Air) is immediately apparent upon KDM load :P

KDE 4.3 is finally available in Karmic now?! Awesome!

---

### Post by wayne_cat on 2009-08-11
> **novafluxx said:**
> KDE 4.3 is finally available in Karmic now?! Awesome!

it is available for Jaunty and Karmic ... so it is not a difference ;)

---

### Post by inportb on 2009-08-11
> **novafluxx said:**
> KDE 4.3 is finally available in Karmic now?! Awesome!

Yes, and it's been the default; for me, this is the single most obvious visual change. But most of the improvements are still under the hood and affect the core Ubuntu setup.

---

### Post by PRGUY85 on 2009-08-12
I'm waiting for my video card to work again with Compiz effects on Karmic before trying KDE 4.3 and its supposed "awesomeness".  Every time I try KDE, I last a day or so.  Just don't like widget-centric desktops.

---

### Post by Kareeser on 2009-08-12
*skipped 3 pages*

Kernel mode setting, bwarrr! This is the single feature I've enjoyed the most in Karmic.

Seriously, switching from text to GUI and back instantly. Still can't get over that.

---

