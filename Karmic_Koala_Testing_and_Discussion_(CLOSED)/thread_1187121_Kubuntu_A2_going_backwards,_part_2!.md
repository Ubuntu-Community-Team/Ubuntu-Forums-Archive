---
title: "Kubuntu A2 going backwards, part 2!"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-06-14
I do get incredibly infuriated with the ubuntu community sometimes. You try to take part, to contribute, only to get shot down by someone for not already knowing everything. Either that or they miss the point entirely as in this case.

I'd like to thank whoever closed my thread down dispite not having resolved my issue (by determining it a bug, or not a bug). There is always talk of regressions, I just wish I knew what that meant, however regression or not that does not change the fact that ubuntu 9.04 Jaunty Jackolope gets the resolution wrong on HD TV's on multiple machines, as does Kubuntu, as does Karmic.

This is not a result of mid development issues, this is ubuntu getting it wrong, over multiple flavours over multiple versions. One of the last messages in my previous thread was from someone else having the same issue.

If this message gets swept aside by some dismissive comment or someone shoots me down by saying 'you should expect problems with a development version' I swear I'll just give up!

---

### Post by super.rad on 2009-06-14
Have you reported this as a bug or checked if it's already reported on launchpad. If it's not reported on launchpad then chances are the developers don't know about it

---

### Post by macroshaft on 2009-06-14
> **super.rad said:**
> Have you reported this as a bug or checked if it's already reported on launchpad. If it's not reported on launchpad then chances are the developers don't know about it

When trying to ascertain if a problem is a bug, or by design, or just me being an idiot I have always tried to obtain a second opinion on here. Usually to be greeted by a brick wall!

---

### Post by macroshaft on 2009-06-14
Reported on launchpad as bug 386949

---

### Post by PmDematagoda on 2009-06-14
> **macroshaft said:**
> When trying to ascertain if a problem is a bug, or by design, or just me being an idiot I have always tried to obtain a second opinion on here. Usually to be greeted by a brick wall!

If that is really your intention, then please use a topic that is more descriptive rather than a dramatic one which does not work out at all and makes one wonder if you should be using the development version of Ubuntu at all(which 23meg seems to have covered with the message which he closed your previous thread with). And I support 23meg in his decision to close the previous thread, that's what I would've done as well.

---

### Post by macroshaft on 2009-06-14
> **PmDematagoda said:**
> If that is really your intention, then please use a topic that is more descriptive rather than a dramatic one which does not work out at all and makes one wonder if you should be using the development version of Ubuntu at all(which 23meg seems to have covered with the message which he closed your previous thread with). And I support 23meg in his decision to close the previous thread, that's what I would've done as well.

Thanks, I do wonder if you guys are this much fun at parties!

---

### Post by 23meg on 2009-06-14
> **macroshaft said:**
> When trying to ascertain if a problem is a bug, or by design, or just me being an idiot I have always tried to obtain a second opinion on here.

And the best way to do that is to start **separate threads** with **descriptive titles** for each issue you've encountered. If you start one thread with a sweeping generalization as a title and try to discuss multiple unrelated issues in it, as you did in that thread, it gets out of hand quickly.

[QUOTE=macroshaft]If this message gets swept aside by some dismissive comment or someone shoots me down by saying 'you should expect problems with a development version' I swear I'll just give up![/QUOTE]

Your previous thread did not get swept aside with a dismissive comment. It was closed with a genuine recommendation, which you'll find useful in accomplishing what you want to do.

---

### Post by PmDematagoda on 2009-06-14
> **macroshaft said:**
> Thanks, I do wonder if you guys are this much fun at parties!

This kind of attitude isn't going to achieve anything, both for you and for us, if you really want to help out with the development of Ubuntu then you need to collaborate with others and listen to what they are saying carefully, what you are doing here is the opposite.

---

### Post by taavikko on 2009-06-14
> **macroshaft said:**
> Reported on launchpad as bug 386949

Please read [http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)
For how to contribute on bugs, ATM the bug reports you send is incomplete in any way :(

Especially this on X bugs: [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting)

these things aren't documented just for fun...

---

### Post by jerrylamos on 2009-06-14
I got a good step forwards on the A2 Grub2 (1.96, really) multi-boot option from these forums.  Both my A2 pc's now multi-boot O.K. without having to fiddle with grub.cfg editing.  See "help test grub2" forum for details about re-installing installer4.  On one pc I had to reinstall os-prober as well.

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub

My multiboots are all ubuntu versions, intrepid, jaunty, various karmics.  If you've got suse and or fedora there may be some editing required.

Cheers to the forums - they came thru again.

Jerry

p.s. karmic A2 CD doesn't boot on this pc with i845 graphics, classic black screen hang losing keyboard, mouse, and video bug# 385947 and have supplied the bug-shooter with some more info.

---

### Post by iggykoopa on 2009-06-14
As for your question about HD TV's there could be several issues with it. Some TV's have incorrect EDID information, on some of those TV's you can work around it but it can be a painful process and didn't work on the TV I had with the issue (I had just bought it so was able to return it). Also it's not resolution per se but make sure you set the TV to pixel-for-pixel on the aspect ratio (may not be called that exactly) instead of stretch or fit or whatever the other options are. From what I've seen the TV's with the most issues are ones that aren't 720p or 1080p (it's 1360x728)

---

### Post by caryb on 2009-06-14
I must confess I too think the Forum staff are correct. I only opened this post because the Kubuntu reference but usually if the title is obscure I ignore the posts.


Cary

---

