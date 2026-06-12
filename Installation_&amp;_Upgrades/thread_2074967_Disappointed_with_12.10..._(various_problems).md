---
title: "Disappointed with 12.10... (various problems)"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by stbub on 2012-10-22
Major problems I have:

1) USB drives no longer get detected automatically when plugged in (it worked fine in 12.04)

2) VMPlayer 5.0.0 wrecks the video mode on startup (it worked fine in 12.04)

3) gnome shell overview's right side virtual desktop overview stops working almost immediately on startup (this mostly - but not always - worked in 12.04)

System:
64bits / ASUS EAH3650 (ATI) graphics card

I know 12.10 is not a LTS, but still...

---

### Post by VE6EFR on 2012-10-22
Out of curiosity, did you do an upgrade or a clean install?

---

### Post by stbub on 2012-10-22
> **VE6EFR said:**
> Out of curiosity, did you do an upgrade or a clean install?

an upgrade.

---

### Post by stbub on 2012-10-22
> **stbub said:**
> Major problems I have:

1) USB drives no longer get detected automatically when plugged in (it worked fine in 12.04)


Seems like a bug to me.  If I create /media/<user> manually, the automounting now works.

---

### Post by hamiljf on 2012-10-23
Still early days... but not too happy myself.  Downloaded the 'CD' image and it is too big for any CD that I have in stock (well over 700MB).  So copied to DVD: would have been helpful if the download page had said this is a DVD image, if it is; and my brand new laptop gives machine check error trying to boot the DVD.  Will try to do more experiments to localise problem (may really be broken hardware), but a bit worrying nonetheless.
Will definitely not try to upgrade my main machine.
update: 12.04 CD (real CD... 700MB) works just fine... installing that instead

---

### Post by mode7 on 2012-10-23
Well, for the heck of it:
1) On my desktop, the proprietary fglrx driver breaks compiz. (Apparently a common issue right now)
2) On my Macbook, I'm unable to get the wireless up and running. Previously I was able to add a PPA that had an updated firmware-b43-installer, but that doesn't have any Quantal versions, and I wish they'd *eventually* add support for the bcm4331 card by default.
3) The Unity launcher shortcut for Synaptic doesn't launch it as root, thus making it useless. You can launch it normally from the dash.
4) Personal taste, but I don't like the new look for the button widgets nearly as much as 12.04 :)

---

### Post by VE6EFR on 2012-10-23
> **stbub said:**
> an upgrade.

Try doing a clean install. From everything that I have been reading on the forum it seems like people are having problems after an upgrade. However once they do a fresh install a lot of the problems are corrected.

---

### Post by stbub on 2012-10-23
> **VE6EFR said:**
> Try doing a clean install. From everything that I have been reading on the forum it seems like people are having problems after an upgrade. However once they do a fresh install a lot of the problems are corrected.

Not a reasonable option for me at this point in time.

In any event, I suspect some of the problems I have would not be taken care of this way.

Other problems:

1) moving the mouse to the lower right corner causes the entire desktop to shift up to reveal a gray box (it should be a see thru panel without the entire desktop shifting up)

2) moving the mouse over TuxGuitars causes the window to be corrupted with black rectangles all over.

3) I do have an intermitent window poping up about this or that that crashed (at some point I'll have to look at it more closely)

4) eog displays some jpg with the wrong colors (that was also in 12.04) (I run the following to work around that problem: xprop -root -remove _ICC_PROFILE)

5) Cannonical not interested in gnome shell (Granted this is not a bug introduced in 12.10)

(I use the free ATI graphics driver.  not the proprietary driver)

---

### Post by Mark Phelps on 2012-10-24
> **stbub said:**
> ... (I use the free ATI graphics driver.  not the proprietary driver)

Might be the only "good news" at this point with 12.10.  Folks who have forced the installation of the AMD restricted drivers have posted lots of problems from doing that.

---

### Post by funicorn on 2012-10-24
Not useful to you, I have a point to propose though, that to upgrade right after the new release is not a wise choice. Either upgrade even earlier before official release, or just have a clean install after that.

The best timing I suggest is to upgrade after beta1 is released.

---

### Post by qamelian on 2012-10-24
> **stbub said:**
> 1) moving the mouse to the lower right corner causes the entire desktop to shift up to reveal a gray box (it should be a see thru panel without the entire desktop shifting up)
This is the default style and behaviour for the notification area in Gnome-shell 3.6. What you describe is exactly how it is supposed to work now.

---

### Post by kansasnoob on 2012-10-24
> **funicorn said:**
> Not useful to you, I have a point to propose though, that to upgrade right after the new release is not a wise choice. Either upgrade even earlier before official release, or just have a clean install after that.

**The best timing I suggest is to upgrade after beta1 is released**.

What do you mean by "after beta1 is released"? Quantal/12.10 is final! And it is a mess :(

---

### Post by kansasnoob on 2012-10-24
> **kansasnoob said:**
> What do you mean by "after beta1 is released"? Quantal/12.10 is final! And it is a mess :(

Or ............. maybe I'm not understanding :confused:

But it is getting harder to use 'gnome-shell' or 'gnome-panel' from an Ubuntu install or upgrade, not only because of Unity, but because the Metacity window manager has been dropped by default, etc, etc.

OTOH there is a new Ubuntu GNOME Remix that's gained enough momentum to be included in the Ubuntu repos:

[http://ubuntuforums.org/showthread.php?t=2073181](http://ubuntuforums.org/showthread.php?t=2073181)

But IMHO this is a good time to stick with LTS unless you're adventurous :)

---

### Post by stbub on 2012-10-24
> **qamelian said:**
> This is the default style and behaviour for the notification area in Gnome-shell 3.6. What you describe is exactly how it is supposed to work now.

Weird, but I'll take your word for it.

I'll throw in a replacement issue then :-)

No keyboard switcher icon (for gnome shell).  I like to switch to a French keyboard when I write in French.  But evidently, that's a low priority problem for ubuntu (judging from the fact that this bug was brought up through the proper channels weeks ago)

---

### Post by VE6EFR on 2012-10-24
> **stbub said:**
> Not a reasonable option for me at this point in time.



What about booting from a live CD as a test? I wonder if the problems would still be there or if you would be having the same issues?

---

### Post by stbub on 2012-10-24
> **VE6EFR said:**
> What about booting from a live CD as a test? I wonder if the problems would still be there or if you would be having the same issues?

Booting from a live CD will not give a full environment anyways.

At this point, I'm hoping that a new official version of vmplayer will be released with the fix.  I'm not interested in grabbing a patch from the net.  So, I'm waiting for an official fix on this one.

Some other issues (like no keyboard switcher in gnome shell) are already in the bug tracker.

etc.

None of this is good.  But it is what it is.

---

### Post by qamelian on 2012-10-25
> **stbub said:**
> Weird, but I'll take your word for it.

It took a bit for me to get used to the new behaviour, and I'm still not sure if I find it better, worse, or whatever. I have to admit that I find it aesthetically less appealing.

---

### Post by alan tam on 2012-10-25
> **VE6EFR said:**
> Try doing a clean install. From everything that I have been reading on the forum it seems like people are having problems after an upgrade. However once they do a fresh install a lot of the problems are corrected.

No not at all a clean installation solve all the problems.
My upgrade experienced began with everything perfect initially except the start up screen seems getting abit messy unlike what was in the 1204 case smooth and free of garbage.
I thought subsequent updates will provide solutions to this messy start up screen however, this is not true! In my case, updates bring disastrous where my dedicated Nvidia NT570 was completely disabled and no way i can activate it back.
THen I tried a clean installation with live DVD disc (look! no live CD!)  thought it would bring my ubuntu back to usable state but to my dismay it was not despite 4 or 5 times trying without success, my system just got knock out completely. Leaving me with a blank screen missing of side and top bar.
I do not know what went wrongwith this upgrade but no doubt it was crab!
Now i am running back my 1204. It was great! I do not think upgrade is a good option for 1210 better think twice before doing it.

---

### Post by ljonesj on 2012-10-25
this is why i left canonical's ubuntu as i ve had nothing but trouble with crashes on several computers running 12.04 and this mess with the amazon thing with 12.10 and now the secrecy of 13.04 is the kicker for me i am using linux mints version of ubuntu with no problems and even peppermint 3 which is lubuntu/linux mint together based 12.04 if it uses unity for me it gives me issues

---

