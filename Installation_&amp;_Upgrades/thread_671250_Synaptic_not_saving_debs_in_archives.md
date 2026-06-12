---
title: "Synaptic not saving debs in archives"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by gilf on 2008-01-18
I've installed a lot more applications through Synaptic than are visible in the /var/cache/apt/archives as debs.

I found this out when I wanted to use apt-move to distribute downloaded apps to 4 other computers. I only have a dialup, and this represents a couple months of downloads. There were only a few debs in there.

I realize there are workarounds for this, like creating a liveCD, etc.

But I want to know why Synaptic is not saving debs.

I've looked at the Synaptic Preferences  (which has been set at the default installed value) for saves:

"Only delete packages which are no longer available."

What does this mean?? 

Does it perform a delete action of an older package upon download of a new package?
Does it delete ALL older packages when a single new package is downloaded
Does it delete ALL older packages when a refresh occurs?

These are completely different actions -- does anybody know what is happening with this default option?

I have a feeling that the only debs in my archive are those I downloaded directly outside of Synaptic, and then installed -- not sure about this.

I have since changed the Synaptic Preferences> File>  to:

"Leave all downloaded packages in the cache."

That also is a little unclear -- are we talking about /var/cache/apt/archives or the /var/cache?

---

### Post by Pumalite on 2008-01-18
Packages in archives have a time limit.

---

### Post by gilf on 2008-01-18
How is that limit established?
How long is it 
Where is it kept?

I've had this installation for only a couple months -- do you mean an "archive" is cleaned automatically? within weeks?

How is it an "archive"?

Throughout this forum, people are giving advice to others to do things like check /var/cache/apt/archives for re-installations.

Or use apt-move to install applictaions on other computers.
[https://help.ubuntu.com/community/AptMoveHowto/simple?highlight=%28Apt-move%29](https://help.ubuntu.com/community/AptMoveHowto/simple?highlight=%28Apt-move%29)

Or Apt0nCD Even Ubuntu official documenttation:

[https://help.ubuntu.com/7.10/add-applications/C/offline.html#APTonCD](https://help.ubuntu.com/7.10/add-applications/C/offline.html#APTonCD)

All of this advice is pointless if the persistence of debs in the archives is a few weeks.

What do you mean by a time limit?

---

### Post by gilf on 2008-01-21
I hope someone will answer these questions.

---

### Post by gilf on 2008-01-27
bump

---

### Post by robertbub on 2008-06-10
I added
> APT::Clean-Installed "off";
to a new /etc/apt/apt.conf.d file, but it still does not seem to prevent the cached files from getting trashed.  (Thankfully, I created a backup because I didn't want to lose 4 hours of download time.)

Is there a cron job or something which cleans/removes/deletes the .deb files in /var/cache/apt/archives ?  I would like to forever keep my packages.

---

### Post by robertbub on 2008-06-17
I finally figured this out.  I needed to change **/etc/apt/apt.conf.d/20archive** to > APT::Archives::MaxAge "0";
APT::Archives::MinAge "0";
APT::Archives::MaxSize "0";If this wasn't done, a cron job would start erasing various cached packages.  There doesn't seem to be a synaptic setting to stop this.

---

