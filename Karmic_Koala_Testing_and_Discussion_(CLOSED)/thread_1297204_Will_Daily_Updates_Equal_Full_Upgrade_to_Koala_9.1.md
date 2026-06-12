---
title: "Will Daily Updates Equal Full Upgrade to Koala 9.10?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by winotree on 2009-10-21
If, after downloading and installing the new Koala 9.10, I accept the daily updates in Synaptic Package Manager will I have the completed upgrade?  :???:

I've tried alpha and beta versions before *but never followed one as completely as I am now* -- and I'm sure I read that if this method was used the result would be the same as doing a full download of the finished product.  

The problem is I can't find that post to confirm my memory.  Would someone be good enough to point me to it or verify it for me.  Many thanks ahead of time.  :-D

---

### Post by philinux on 2009-10-21
> **winotree said:**
> If, after downloading and installing the new Koala 9.10, I accept the daily updates in Synaptic Package Manager will I have the completed upgrade?  :???:

.  :-D

Yes. :P

---

### Post by FuturePilot on 2009-10-21
[http://ubuntuforums.org/showthread.php?t=1280021]("http://ubuntuforums.org/showthread.php?t=1280021")

> If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the beta, 

The same goes for the final release.

---

### Post by psyke83 on 2009-10-21
Yes. An alpha, beta and release candidate release is a snapshot along the development (and points in which the developers make an extra effort to stamp out show-stopping bugs, to ensure that it can install successfully).

Just make sure to approach Partial Upgrades with caution - read the sticky.

Also, there is a slight possibility that some user configuration may be outdated. For example, I installed an Alpha release and it created a "Download" folder in the Home folder, and a bookmark in the Places menu. A bug was filed that requested for "Download" to be renamed to "Downloads" - this bug was fixed, but this change only happens when you create a new user account (old accounts aren't updated properly).

---

### Post by winotree on 2009-10-21
That was fast!  [What, no one working today?]  Thanks to all three of you, especially **FuturePilot **who linked me to *the* thread -- the same one I'd read and re-read this morning and still didn't see what I was looking for.  :rolleyes:

EDIT ->  Just make sure to approach Partial Upgrades with caution - read the sticky.  Read *it* twice, too!!

---

### Post by ranch hand on 2009-10-21
If you have recently installed I would say that you are going to have the Final Release just fine.

I have installs that go back to A1 and I would not keep them.  There has been too much "work around" editing done.  It would work fine but I don't even remember some of those filesand they are a mess.  Why keep all the junk?

---

### Post by novafluxx on 2009-10-21
As long as you don't do an erroneous partial-upgrade, you'll be fine!

---

### Post by sports fan Matt on 2009-10-21
I actually think after I receive my karmic cd I will just reinstall to trim the fat from the upgrade and start fresh.  Anyone else thinking like this?

---

### Post by winotree on 2009-10-21
> If you have recently installed I would say that you are going to have the Final Release just fine.Thanks for the encouragement.  ;)  I've tried about a dozen different distro this summer but come back to Xubuntu again and again, though not for the reason that *everything just works* [which it does] because I've found that to be true of many of the others.  In fact, almost everything seems to work on this little device -- either I got lucky and got a good one or I'm learning something.  :o  I just like the way this distro feels.  

> I actually think after I receive my karmic cd I will just reinstall to trim the fat from the upgrade and start fresh. Anyone else thinking like this? Trimming the fat is something I seem to want to do right away -- there's so much that comes installed on most distros that I'll never need, want or use though I realize someone else may not be able to get by without them.  Whether I do it again or not is something I still need to consider.  :D

EDIT - > ...erroneous partial-upgrade... Oh, no!  Not that!

---

### Post by zefew on 2009-10-21
No upgrades on "apt-get dist-upgrade" today. I usually get about 40-60 upgrades per day.

Is this due to the RC release? Why no updates today?

---

### Post by ranch hand on 2009-10-21
> **zefew said:**
> No upgrades on "apt-get dist-upgrade" today. I usually get about 40-60 upgrades per day.

Is this due to the RC release? Why no updates today?
Freeze before RC release.  They want the bugger to be as stable as possible so no new stuff thrown in at the last minute.

---

### Post by philinux on 2009-10-21
> **ranch hand said:**
> Freeze before RC release.  They want the bugger to be as stable as possible so no new stuff thrown in at the last minute.

How come we got potential show stoppers like this then. Guess I'm getting frustrated with this. Not a stability issue more of a papercut for newbies. The boot experience should be good.

[http://ubuntuforums.org/showthread.php?t=1292711](http://ubuntuforums.org/showthread.php?t=1292711)

---

### Post by novafluxx on 2009-10-21
> **sox fan Matt said:**
> I actually think after I receive my karmic cd I will just reinstall to trim the fat from the upgrade and start fresh.  Anyone else thinking like this?

I might do that once final is out, just to get rid of any potential issues that may arise.

As long as I can remove Empathy and get Usplash and XSplash working as intended I'll be a happy man

---

### Post by ikisham on 2009-10-21
To trim this fat maybe the computer janitor is enough. Remove the old kernels, clear the logs and if wanted to save space 'apt-get clean'.

---

### Post by ranch hand on 2009-10-21
> **ikisham said:**
> To trim this fat maybe the computer janitor is enough. Remove the old kernels, clear the logs and if wanted to save space 'apt-get clean'.
That does a great job but not on renamed or moved files/folders that you saved in case you need them after the next update (it happens).

---

### Post by VMC on 2009-10-21
> **sox fan Matt said:**
> I actually think after I receive my karmic cd I will just reinstall to trim the fat from the upgrade and start fresh.  Anyone else thinking like this?

Yes, this is exactly what I will do, but I'm in no hurry to do so. Maybe a few weeks after the final release. I started out late, with alpha 3 and kept updates current. But I experimented along the way. Remove xplash, re-install xplash. Removed OO, then did this dance several times on countless programs.

I had issues with one of my finance sites that only allowed download of pdf files using Windows only. They thought they could fix it. They couldn't, so I tried installing every pdf driver, javascript, java programs I could thing of, all to no avail. At any rate I don't want all that cruft staying around, so in the end I will do a complete re-install. But after the "xmas" rush is over.

---

### Post by scradock on 2009-10-21
+1

---

### Post by 3rdalbum on 2009-10-21
When they say "Don't do a partial upgrade":

Does that mean that when it warns you about the partial upgrade, that you shouldn't click the "Partial Upgrade" button? Or does it mean that when it warns you about the partial upgrade, that you shouldn't click "Close" and then "Install Upgrades"?

Because there is a difference. I've done both during Karmic beta without any problems (yet).

---

### Post by scradock on 2009-10-21
> **philinux said:**
> How come we got potential show stoppers like this then. Guess I'm getting frustrated with this. Not a stability issue more of a papercut for newbies. The boot experience should be good.

[http://ubuntuforums.org/showthread.php?t=1292711](http://ubuntuforums.org/showthread.php?t=1292711)
Yes, I'm still waiting for the magic fix to several reported problems:

slow boot, with random switches from console to usplash to xsplash to gdm......

failure to correctly locate symlinks on restarting Desktop;

failure to resume after suspend or hibernate (HP Pavilion zv6000);

failure to pass mouse clicks to Flash in web pages;

.......

---

### Post by ikisham on 2009-10-22
> **ranch hand said:**
> That does a great job but not on renamed or moved files/folders that you saved in case you need them after the next update (it happens).

Yep, sorry, I just came in with Beta and I'm taking care with it (since it's behaving really well). So I haven't been a hardcore tester..

---

### Post by ranch hand on 2009-10-22
I would not be keeping an of mine anyway because the (12 variations, one even running the pae kernel) are all on "test" drives.  My main drive is off line when I am "playing" I mean "testing".

I will backup all data on all of them (a folder for each) and sort through it on my clean install of Kinky Kitty (9.10) and keep what may still be useful.

The next testing I do will be more compact and use fewer variants.  I am a noob and learning so I used each one for some particular types of abuse (testing).

---

### Post by winotree on 2009-10-22
> **ranch hand said:**
> I would not be keeping an of mine anyway because the (12 variations, one even running the pae kernel) are all on "test" drives.  My main drive is off line when I am "playing" I mean "testing".

I will backup all data on all of them (a folder for each) and sort through it on my clean install of Kinky Kitty (9.10) and keep what may still be useful.

The next testing I do will be more compact and use fewer variants.  I am a noob and learning so I used each one for some particular types of abuse (testing).
That sounds like it'd keep you busy.  :D  I'm happy to open mine and have  it work, and as I mentioned earlier this device seems to do just that.

I just did a *sudo apt-get update* and *sudo apt-get dist-upgrade* but there was nothing at the site.  Or at least nothing I needed.  Go make some coffee now then try again early this afternoon.  ;)

---

### Post by qamelian on 2009-10-22
> **3rdalbum said:**
> When they say "Don't do a partial upgrade":

Does that mean that when it warns you about the partial upgrade, that you shouldn't click the "Partial Upgrade" button? Or does it mean that when it warns you about the partial upgrade, that you shouldn't click "Close" and then "Install Upgrades"?

Because there is a difference. I've done both during Karmic beta without any problems (yet).
Clicking "Close" and then "Install Upgrades" is pretty much always safe because it doesn't try to agressively resolve dependancy issues. That isn't a "Partial Upgrade". A "Partial Upgrade" is when updates are listed and Update Manager leaves them unselected because not all of their dependancies have been met yet, among other reasons. Sometimes it is because a package is being deprecated and replaced with something else. In that case, the partial upgrade is safe. If a package is unselected because of unmet dependancies and you run a partial upgrad, that's when things often turn nasty because packages tend to get removed that you really want to keep.

---

### Post by 3rdalbum on 2009-10-22
> **qamelian said:**
> If a package is unselected because of unmet dependancies and you run a partial upgrad, that's when things often turn nasty because packages tend to get removed that you really want to keep.

Thanks for the clarification, that's what I thought happened. I'm always careful with checking what's marked to be removed anyway.

---

### Post by linusr on 2009-10-22
> **psyke83 said:**
> Yes. An alpha, beta and release candidate release is a snapshot along the development (and points in which the developers make an extra effort to stamp out show-stopping bugs, to ensure that it can install successfully).

Just make sure to approach Partial Upgrades with caution - read the sticky.

Also, there is a slight possibility that some user configuration may be outdated. For example, I installed an Alpha release and it created a "Download" folder in the Home folder, and a bookmark in the Places menu. A bug was filed that requested for "Download" to be renamed to "Downloads" - this bug was fixed, but this change only happens when you create a new user account (old accounts aren't updated properly).

anyway to update these 'old' accounts? I didn't notice the 'Download' folder!!

---

### Post by ranch hand on 2009-10-22
Yes you can update them, or delete them.

System>Administration>Users and Groups

It is unlikely but they may be lost in limbo somewhere you can't get to them.  I would not worry too much about that until it happens, really not likely.

---

