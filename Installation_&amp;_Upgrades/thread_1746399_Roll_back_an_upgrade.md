---
title: "Roll back an upgrade?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by ubunwhat on 2011-05-01
Ok, I am in a bit of a pickle.  I foolishly upgraded to 11.04 today thinking that it would go smoothly.  I don't know why I thought that, but I did.  Needless to say it didn't.  I now have no wireless, among other problems.  The fix for the wireless is lost on me as I also seem unable to uninstall old drivers or install new ones.  So it seems that I am a bit on the hosed side of things here.  To make matters worse, I really need this machine working tomorrow.  I don't have days to spend tinkering and my problem seems to be one of a few hundred of similar nature in the wireless forum so specific help there is not expected.  What it boils down to is that I probably just need to roll back the upgrade if at all possible.  Can this be done?  If so, will my wireless work again?  I'm really in a spot here and help would be greatly appreciated.

---

### Post by Vaphell on 2011-05-01
there is only 1 way to perform a rollback - full installation of an earlier release, sorry.
Backup valuable data first.
If your wifi requires tinkering, expect exactly that.

---

### Post by ubunwhat on 2011-05-01
I can't begin to describe how frustrated ( and mildly panicked ) I am right now.  This type of thing is exactly why I walked away from Windows to Linux.  Judging by the number of people with this issue I would say that it was entirely premature to offer this release. I can't re-install as I have servers, development environments, and tons of other things that I simply cannot spend a week re-setting.  I know that the point of Linux is that it's a community that supports itself rather than having big brother overseeing everything.  I guess I trusted the system a little more than I should have.  I'll say again, no way should that update have rolled out.

---

### Post by ebasa on 2011-05-01
Simply restore from your backup. You do have a backup don't you?

---

### Post by mörgæs on 2011-05-01
> **ubunwhat said:**
> I can't begin to describe how frustrated ( and mildly panicked ) I am right now.  This type of thing is exactly why I walked away from Windows to Linux.  Judging by the number of people with this issue I would say that it was entirely premature to offer this release. I can't re-install as I have servers, development environments, and tons of other things that I simply cannot spend a week re-setting.  I know that the point of Linux is that it's a community that supports itself rather than having big brother overseeing everything.  I guess I trusted the system a little more than I should have.  I'll say again, no way should that update have rolled out.


I feel your pain, and I have for good stopped doing online upgrades. A fresh install 3-4 months after the release date works.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by wilee-nilee on 2011-05-01
> **ubunwhat said:**
> I can't begin to describe how frustrated ( and mildly panicked ) I am right now.  This type of thing is exactly why I walked away from Windows to Linux.  Judging by the number of people with this issue I would say that it was entirely premature to offer this release. I can't re-install as I have servers, development environments, and tons of other things that I simply cannot spend a week re-setting.  I know that the point of Linux is that it's a community that supports itself rather than having big brother overseeing everything.  I guess I trusted the system a little more than I should have.  I'll say again, no way should that update have rolled out.

I understand your frustration with having to do another setup, here is a open source cloner clonezilla. This is a awesome way of imaging the whole HD or partitions bit for bit onto a external just sitting in a folder, waiting to be reloaded. The clone is a medium speed job but sliding it back in goes really fast.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ubunwhat on 2011-05-01
@ebasa:

Really?  Did that one make you feel all smug and superior or something?

---

### Post by wilee-nilee on 2011-05-01
> **ubunwhat said:**
> @ebasa:

Really?  Did that one make you feel all smug and superior or something?

Yay another one on the block list.

---

### Post by ubunwhat on 2011-05-01
> **wilee-nilee said:**
> Yay another one on the block list.

Seriously?  You block me because I take exception to be sarcastic remarks about back ups when I'm trying to fix a problem?  Notice that every other post in this thread was not sarcastic or pedantic at all.  If, in your eyes, because someone makes a mistake and asks for help, that entitles people to take pot shots at them and they are just supposed to take it then hey, block me all you want.  I don't need friends like that.

On a side note, many thanks to Rifester for helping me get things up and running again and averting catastrophe.  You, sir, are a rock star.  You get to feel superior because you are superior.

---

### Post by Ni-el on 2011-05-01
I think they should have called this one Natty Dread. 
And, nope there's no going home once you take that step out the door. I just ended up re-installing the whole thing back to 10.10 after getting in a corner trying to fix the video (the upgrade wouldn't offer a workable resolution, and I didn't figure out how to fix it until too late and I couldn't see anything). But I wanted to say that the new Gnome and Ubuntu is quite a change and upgrading should only be done with caution and a little experimentation. Maybe make a virtual version first (virtualbox?).

---

### Post by ubunwhat on 2011-05-01
> **Ni-el said:**
> I think they should have called this one Natty Dread. 
And, nope there's no going home once you take that step out the door. I just ended up re-installing the whole thing back to 10.10 after getting in a corner trying to fix the video (the upgrade wouldn't offer a workable resolution, and I didn't figure out how to fix it until too late and I couldn't see anything). But I wanted to say that the new Gnome and Ubuntu is quite a change and upgrading should only be done with caution and a little experimentation. Maybe make a virtual version first (virtualbox?).

For what it's worth, I am absolutely HATING this new layout.  That god awful sidebar is the most annoying new feature to come along in any system since Windows installed that back door to HSA and Haliburton back in Vista.  And the way the windows size... ridiculous.  If I wanted a Mac I would buy a Mac.  The last thing I want is a poorly functional Linux version trying to look like a Mac.  I miss being able to have two or three things going at once and actually being able to just toggle back and forth.  I can't tell you how much I wish I hadn't upgraded.  But, having now gotten this mess working I don't dare risk going backwards.  I guess I'll have to get used to it.

---

### Post by Rifester on 2011-05-01
Ubunwhat,
At your login screen at the bottom you will see a drop down box that says "Ubuntu"  click it and choose "Classic".   It will be a better desktop experience for you.   I am glad to have been able to help you.   I have been battling with my Broadcom cards for years.   They are a pain, but hopefully with their open source driver for the 4311 card things will become easier.  Thanks again for your kind words!

---Rifester

---

### Post by perspectoff on 2011-05-01
> **mörgæs said:**
> I feel your pain, and I have for good stopped doing online upgrades. A fresh install 3-4 months after the release date works.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

+1

And I always do a side-by-side installation, to make sure all my apps work in the new version before getting rid of the old one.

In reality, I have 3 partitions. One is the stable version (my current stable version is Lucid because I didn't like Maverick).

In the second I copy the Lucid partition and try an upgrade (in this case to Maverick then Natty). Upgrades usually don't work for me, though -- there's always some app or dependency that isn't compatible with some other new app or module, or some configuration file that isn't compatible with a new app.

In the third I do a new installation of the newest version. I never get rid of the original partition with the old version for about 3-4 months, until I'm sure everything works properly in the new version. 

It's a lot of work, perhaps, but I've never lost data. Also, I can still get work done on the original partition while fiddling/troubleshooting the new one(s).

---

### Post by wilee-nilee on 2011-05-01
> **ubunwhat said:**
> Seriously?  You block me because I take exception to be sarcastic remarks about back ups when I'm trying to fix a problem?  Notice that every other post in this thread was not sarcastic or pedantic at all.  If, in your eyes, because someone makes a mistake and asks for help, that entitles people to take pot shots at them and they are just supposed to take it then hey, block me all you want.  I don't need friends like that.

On a side note, many thanks to Rifester for helping me get things up and running again and averting catastrophe.  You, sir, are a rock star.  You get to feel superior because you are superior.

Yep, my post was not sarcastic, nor do I see it in any others. The info had already been posted that you can't downgrade. If you are offended or feel the COC has been broken report it.;)

We are trying to help, you asked for a roll back, it appeared to me you just didn't want to use Natty. I was trying to give you some information that would have precluded you ever even having this thread or a problem ever.

---

### Post by ubunwhat on 2011-05-02
> **wilee-nilee said:**
> Yep, my post was not sarcastic, nor do I see it in any others. The info had already been posted that you can't downgrade. If you are offended or feel the COC has been broken report it.;)

We are trying to help, you asked for a roll back, it appeared to me you just didn't want to use Natty. I was trying to give you some information that would have precluded you ever even having this thread or a problem ever.

Oh... Now I see the problem.  Dude, I never said your post was sarcastic.  Look again at the post you found offensive.  It came after yours so you assumed it was directed at you, but the first line is "@ebasa:", which means that my comment was directed at ebasa.  If you look at ebasa's post it was indeed sarcastic.  Maybe not sarcastic, but certainly smug.  You know what I'm saying here.  Just go back and look.  I was never anything but appreciative for all of the other responses in the thread save the one from ebasa.

---

