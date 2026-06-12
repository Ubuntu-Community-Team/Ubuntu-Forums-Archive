---
title: "upgrade"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaphodbblx on 2009-03-30
ok so to install the jaunty beta(or the final release) I need to upgrade from 8.04 to 8.10 first right?
will this nuke everything I have on my system(like bookmarks,applications ect)
or should they be ok?
is there an EASY way to backup prior to trying it?:)

---

### Post by northern lights on 2009-03-30
Which version/release are you actually trying to upgrade to?

Version numbering is by YEAR.MONTH

8.04 - "Hardy", April 2008
8.10 - "Intrepid", October 2008
9.04 - "Jaunty", April 2009

If you're on Intrepid and wanting to upgrade to Jaunty, I'd recommend waiting till the final release is out.
If you're running Hardy and want to upgrade, you theoretically could go for Intrepid simply by running ```
sudo apt-get dist-upgrade
```I'd recommend waiting a few weeks and then going directly for Jaunty - if you're current Hardy is stable, it should do for a few more weeks.

And, yes, on the way from Hardy to Jaunty you'll have to upgrade to Intrepid first.

Further, as for backing things up, there are several options.
Unless you have a highly modified system though, backing up your personal data (i.e. the home folder) should suffice - I'd keep /home on a separate partition anyhow.

---

### Post by zaphodbblx on 2009-03-30
> **northern lights said:**
>  I'd keep /home on a separate partition anyhow.

I've seen that mentioned a lot how do you go about doing that?

but as for whats in my home folder..lets say for example I dont back it up in theory should everything be ok?
and yes I was going to wait till the 24th when the final comes out

---

### Post by halitech on 2009-03-30
> **zaphodbblx said:**
> I've seen that mentioned a lot how do you go about doing that?

but as for whats in my home folder..lets say for example I dont back it up in theory should everything be ok?
and yes I was going to wait till the 24th when the final comes out

In theory, yes your data *should* be safe but unfortunately things can and do happen so unless you have things you don't care about, I would highly recommend backing things up before you try to upgrade.

---

### Post by zaphodbblx on 2009-03-30
now is that if i update from the software sources or if I update from the disk?

---

### Post by Therion on 2009-03-30
Simply put, if you want to keep it, you back it up.

Period.

---

### Post by Chemical Imbalance on 2009-03-30
I do not recommend you upgrade your current install to jaunty beta.  If anything, install Jaunty next to your current install on a separate partition *after* backing all your data up on external media.  Please do not upgrade your current install unless you know the risk.

---

### Post by halitech on 2009-03-31
> **zaphodbblx said:**
> now is that if i update from the software sources or if I update from the disk?

either way, things happen. The only disk you can upgrade from is the Alt install cd (unless they've recently changed that) but I would recommend you have the newest install cd in case something happens.

---

### Post by zaphodbblx on 2009-03-31
well everything went well although it took forever to download! I had to re grab a few programs to get them to work but no major problems EXCEPT rhythembox seem to be unable to connect with most of the podcasts that I was using it to aggregate..a few work but most of them say unable to connect and I have no idea why. I even un-and reinstalled and re inputed the rss feeds

---

