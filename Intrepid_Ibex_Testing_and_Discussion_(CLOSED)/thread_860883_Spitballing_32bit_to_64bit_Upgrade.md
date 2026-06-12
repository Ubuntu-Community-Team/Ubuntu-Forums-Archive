---
title: "Spitballing: 32bit to 64bit Upgrade"
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TimothyLuke on 2008-07-16
This is new functionality concept and am pretty sure this is not the right place to put it need to start somewhere.  The more I read the 64bit forums there is always a request to convert from 32bit to 64bit or to downgrade.  My guess is that long term more people are going to start wanting to convert to 64bit and will want the "easy method" of ```
apt-get -i386toX86_64 dist-upgrade
``` or something similar.  While Ubuntu is not Windows and am not trying to compare apples to oranges, I can convert my 32bit Vista install to 64bit Vista keeping all my current configuration and installed applications.

I'm just thinking outside the box but a lot of packages are built and stored in both 32bit and 64bit repositories.  I know there are a ton of dependencies etc that need to be considered but how hard would it be to read in the existing package list, bootstrap to / install 64bit kernel and toolchain and then install the 64 bit versions of the package list - reverting to the getlibs script for things that do not have a 64bit version.

A post I saw the other day advised a user to back up /etc and /home and save the package list (apt-get savepackagelist > packagelist), install a base 64bit install then reinstall the package list apt-get install < packagelist, then reinstall the /etc and /home directories.

(I know i am not using real apt-get commands here - on my Windows PC at work - hoping you understand what I mean though)

---

### Post by caryb on 2008-07-16
Not possible! totally different kernels applications it would have to replace everything! It would be easier to keep a couple of setting files & scrub then start again.


Cary

---

### Post by Nullack on 2008-07-16
spitballing ??!!?

---

### Post by Gina on 2008-07-16
> **Nullack said:**
> spitballing ??!!?I wondered what it meant too!  Never heard of it.

---

### Post by TimothyLuke on 2008-07-16
@Caryb
Its not possible to do an "upgrade" - Im not suggesting it is - what I am suggesting is that we identify what information do we need to keep from a i386 install that we can use to "scrub and start again" in an automated, non-interactive manner that seems like an upgrade-type process to the user - possibly something they can choose to do from say update manager.

If you had someone using only repository apps, like multiverse et al, and were not building stuff manually (no ./configure, make, make install) and the same apps were available in 32bit and 64bit flavours (Yes I know a lot of conditions) would we have enough information to be able to do a conversion?

Spitballing: Take a bunch of ideas through them at the wall (like a spitball) and see which ones stick. "What if we could do X - what would we have to do to be able to do X?", "theorycrafting", "brainstorming"

---

### Post by Nullack on 2008-07-16
R i g h t :) I was beginning to think of my wife :lolflag: Moving along :KS

---

### Post by philinux on 2008-07-16
> **Nullack said:**
> R i g h t :) I was beginning to think of my wife :lolflag: Moving along :KS

Management speak. As outlawed by the plain English speaking campaign.

---

### Post by Gina on 2008-07-16
If you have a 64 bit computer I would have thought the logical thing to do was to install the 64 bit version of Ubuntu.  If you then find something doesn't work because it needs to run in a 32 bit system you might want to "downgrade".

---

### Post by Gina on 2008-07-16
> **philinux said:**
> Management speak. As outlawed by the plain English speaking campaign.This is not really the place for such expressions then - Ubuntu is the plain English, user-friendly type OS :)

---

### Post by caryb on 2008-07-16
:lolflag:

---

### Post by RAOF on 2008-07-16
This should almost work right now.  Installing from the LiveCD allows you to not wipe your /home, and that's where almost all the user settings are.

Writing a script to dump the currently installed packages and add those to the install is left as a (reasonably easy) exercise for the reader.

---

### Post by BwackNinja on 2008-07-16
This makes me think of installing ubuntu from ubuntu. Technically it should be possible and not that hard to do (especially considering that it is done on a liveCD whose system as far as I know is almost identical to a user's. How I see it, it should already be able to be done, just no one has put the finishing touches on yet.

---

### Post by Gina on 2008-07-17
I haven't tried it but you can do an upgrade from an install CD/DVD if you insert it while running Ubuntu.  Also, you can mount an ISO as CDROM so you should be able to run the upgrade from there I would have thought.  Details of ISO mounting are in another thread.

---

### Post by McDuff on 2008-07-17
> **caryb said:**
> Not possible! totally different kernels applications it would have to replace everything!

isn't the kernel the same since 2.6.24?
the package description for linux-image-2.6.24-19-generic says: > This package contains the Linux kernel image for version 2.6.24 on
x86/x86_64.

---

### Post by TimothyLuke on 2008-07-17
I was just reading the 64bit forum and noticed this post:

[http://ubuntuforums.org/showthread.php?t=859565]("http://ubuntuforums.org/showthread.php?t=859565")

It seems that there is a post every week or so on "Can I upgrade from 32bit to 64bit"

---

### Post by DizzyTech on 2008-07-17
No, the kernel *packages* are the same.  APT downloads a list of packages, and all of their descriptions and such, from the repositories.  However, the mechanism for downloading packages picks the 64-bit package.

---

### Post by xebian on 2008-07-18
Shouldn't this be moved to the 64-bit section?

---

