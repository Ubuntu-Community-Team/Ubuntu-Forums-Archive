---
title: "What's with this firefox version?"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2013-02-19
I installed  kubuntu 12.04 lts a few days ago, replacing xubuntu 12.10 with kde-desktop installed as well.

There was a firefox install button listed in Favorites, so I hit it.

But ... with this, if I go into Preferences->Applications,. there is an *extremely* limited list of file types/programs.  Missing a couple that I did not want to open with the program kde wants me to.  I can't seem to find a workaround.

Also, I have some web pages saved, and if I double click the file, it opens them in  rekonq instead.  Actually, half the time rekonq won't open them, so I have to use "open with".  Despite I have told dolphin that firefox is the default ap for html files.

Need I mention at this point that rekonq is a rubbish piece of software?

So what am I supposed to do here?  Yanking rekonq seems obvious.  It stinks.  Do I also need to purge firefox and reinstall a decent version from synaptic and then reconfigure it?

Frankly, I've installed kde-desktop over xubuntu, and I have mint 13 KDE installed on a netbook that had hardware support issues.  Using KDE with kubuntu has caused me more problems than either.

---

### Post by csillva on 2013-02-20
> **Rob Sayer said:**
> But ... with this, if I go into Preferences->Applications,. there is an *extremely* limited list of file types/programs.  Missing a couple that I did not want to open with the program kde wants me to.  I can't seem to find a workaround.

This is what's called a list of mimetypes, and it's how the system knows what program to use to open what file extension. KDE has a brilliant mimetype editor in the system settings, called "file associations".

> Also, I have some web pages saved, and if I double click the file, it opens them in  rekonq instead.  Actually, half the time rekonq won't open them, so I have to use "open with".  Despite I have told dolphin that firefox is the default ap for html files.

Ok, so use the file association mime editor I mentioned above, and filter by html, and change the preference order on the right side, moving rekonq down and firefox up. 

> Need I mention at this point that rekonq is a rubbish piece of software?
```

sudo aptitude purge rekonq

```
> So what am I supposed to do here?  Yanking rekonq seems obvious.  It stinks.  Do I also need to purge firefox and reinstall a decent version from synaptic and then reconfigure it?
Sure to the first, no to the second.

---

### Post by Rob Sayer on 2013-02-21
I have been using firefox to configure such things for years.  I don't care if kde has a brilliant mime editor.  Why should it supersede firefox?

---

### Post by csillva on 2013-02-21
> I have been using firefox to configure such things for years.  I don't  care if kde has a brilliant mime editor.  Why should it supersede  firefox?

Either there is a good reason for it and the people who have designed KDE, Gnome, Windows and Mac have thought it through and decided that is how it should be, or everyone but you is an idiot. In either case, this is how it is. 

> Also, I have some web pages saved, and if I double click the file, it  opens them in  rekonq instead.  Actually, half the time rekonq won't  open them, so I have to use "open with".  Despite I have told dolphin  that firefox is the default ap for html files.

If you're not willing to use the mimetype editor to change that, you can try removing rekonq, or try using debian's update-alternatives from the command line.

Good luck.

---

