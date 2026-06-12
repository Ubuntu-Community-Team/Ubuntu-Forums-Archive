---
title: "Tomboy file location"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2010-10-12
Hi All,

I would like to know where Tomboy keeps its notes.
I am doing a re-install of 10.04, but forgot to write down where the notes are kept.
Does anyone know?

---

### Post by hartl_vienna on 2010-10-12
This is the right path

```
~/.local/share/tomboy
```

---

### Post by dreamquartz on 2010-10-12
> **hartl_vienna said:**
> This is the right path

```
~/.local/share/tomboy
```

Tx. Much appreciated.

Does anyone know how to read old notes?
I've found them from a previous install, but Tomboy does not want to open them.

---

### Post by sharm on 2010-10-12
1) Make sure Tomboy is not running
2) Copy .note files from backup to new install's note directory ( ~/.local/share/tomboy/ by default)
3) Start Tomboy

That's all there is to it.  Your old notes should appear in Tomboy now.

---

### Post by gardara on 2010-10-12
I'd also recommend switching from tomboy to gnote after you've upgraded [http://en.wikipedia.org/wiki/Gnote](http://en.wikipedia.org/wiki/Gnote)

:)

---

### Post by sharm on 2010-10-12
> **gardara said:**
> I'd also recommend switching from tomboy to gnote after you've upgraded [http://en.wikipedia.org/wiki/Gnote](http://en.wikipedia.org/wiki/Gnote)

:)

That's not helpful.  dreamquartz had a simple question with a simple answer.  What's the point in berating his choice of software?  May as well suggest he switch from Ubuntu to Mac OS X so that he can use TaskPaper.

---

### Post by gardara on 2010-10-12
> **sharm said:**
> That's not helpful.  dreamquartz had a simple question with a simple answer.  What's the point in berating his choice of software?  May as well suggest he switch from Ubuntu to Mac OS X so that he can use TaskPaper.


Well, he'd already gotten a reply to his question. gnote is just like tomboy, looks and functions exacly the same but it's written in c++ and much lighter :)

---

### Post by sharm on 2010-10-12
> **gardara said:**
> Well, he'd already gotten a reply to his question. gnote is just like tomboy, looks and functions exacly the same but it's written in c++ and much lighter :)

Can you please define "much lighter"?  Tomboy uses ~5MB more RAM than Gnote, and starts up instantly.  Tomboy also takes up less disk space.

Gnote lacks several key features from Tomboy; the one most relevant to this thread is online note synchronization.

I'm happy for you that you're happy with Gnote, but you appear to be somewhat misinformed about it.  And now we are both off-topic, so I'll leave off.  Feel free to message me privately if you'd like to continue the discussion.

---

### Post by sgosnell on 2010-10-12
You can tell Tomboy to keep its notes anywhere you like.  I have mine in my Dropbox folder, so they're synced automatically to any computer that has Dropbox, and automatically backed up.  You can choose any folder you like, not just the default.

---

### Post by sharm on 2010-10-12
> **sgosnell said:**
> You can tell Tomboy to keep its notes anywhere you like.  I have mine in my Dropbox folder, so they're synced automatically to any computer that has Dropbox, and automatically backed up.  You can choose any folder you like, not just the default.

Yup.  This page might help: [http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

---

### Post by gardara on 2010-10-12
> **sharm said:**
> **Can you please define "much lighter"?**  Tomboy uses ~5MB more RAM than Gnote, and starts up instantly.  Tomboy also takes up less disk space.

Gnote lacks several key features from Tomboy; the one most relevant to this thread is online note synchronization.

I'm happy for you that you're happy with Gnote, but you appear to be somewhat misinformed about it.  And now we are both off-topic, so I'll leave off.  Feel free to message me privately if you'd like to continue the discussion.

I'm talking about dependencies too:

**gnote **
Depends On     : boost-libs>=1.43  gtkspell  libpanelappletmm  libxslt
Optional Deps  : None

**tomboy**
Depends On     : gtkspell  gmime>=2.4.19  ndesk-dbus-glib>=0.4.1  gnome-sharp>=2.24.1  mono-addins>=0.5  libsm  gnome-desktop-sharp>=2.26.0  hicolor-icon-theme
Optional Deps  : gnome-panel-bonobo: applet support

Just thought it would be worth mentioning gnote to the original poster since I just discovered it recently after using tomboy for a few years, but I guess it's always someone who has to disagree ;)

---

### Post by saldarji on 2010-10-12
I think Gardara's first post was flame bait.  I'm not sure why he insists on pushing his point-of-view that the user should switch to a different application.  Well, actually I suspect it is political in nature.

Anyways, please remember to add this Tomboy directory, wherever you have it, to your backup list.

---

### Post by dreamquartz on 2010-10-13
> **sharm said:**
> 1) Make sure Tomboy is not running
2) Copy .note files from backup to new install's note directory ( ~/.local/share/tomboy/ by default)
3) Start Tomboy

That's all there is to it.  Your old notes should appear in Tomboy now.

Tx Sharm

That worked.
Tx participants. Loved the input.

---

### Post by gpw1 on 2010-11-25
Hi, I don't want to get involved with the Mono issue...

Please let me know where Ubuntu 10.10 hides the "notes Folder" for Tomboy. It was, I think, in the /usr/local/share/ but I cannot find it any where now... in Ubuntu 10.10 64 bit. 

The same issue where is the Gnote Notes folder? In Ubuntu 10.04 it was in a hidden Gnote directory in the Home directory. 

I have installed, for the first time, Ubuntu 10.10 64 bit. Could that be an issue here? 

I have saved a folder with over 100 Gnotes and don't want to go back to Ubuntu 10.04...to use them.

---

### Post by directhex on 2010-11-25
> **gpw1 said:**
> Hi, I don't want to get involved with the Mono issue...

Please let me know where Ubuntu 10.10 hides the "notes Folder" for Tomboy. It was, I think, in the /usr/local/share/ but I cannot find it any where now... in Ubuntu 10.10 64 bit. 

The same issue where is the Gnote Notes folder? In Ubuntu 10.04 it was in a hidden Gnote directory in the Home directory. 

I have installed, for the first time, Ubuntu 10.10 64 bit. Could that be an issue here? 

I have saved a folder with over 100 Gnotes and don't want to go back to Ubuntu 10.04...to use them.

the location is identical on 10.04 and 10.10 - look in /home/username/.local/share/tomboy or gnote

---

### Post by gpw1 on 2010-11-26
Thanks...I appreciate your fast response. I missed the hidden "local"...

---

### Post by Neobuntu on 2011-05-31
Thank you. I have my note, from my deleted Tomboy app, now in gnote. :)

---

