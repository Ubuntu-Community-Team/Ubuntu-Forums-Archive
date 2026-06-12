---
title: "The application Evolution has closed unexpectedly"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-24
Unreportable Reason -- This is not an official Ubuntu package.  Please remove any third party package and try again.  I thought that gnome was an official package.

I would like to have an explanation from the gurus of Ubuntu as to how I am suppose to run my business without the most important programs on my PCs: Evolution 3.13.3?

I never received this error with 12.04.  Also, what about all the other software I need to run my business for which Ubuntu does not provide an equivalent or a poorly functional equivalent.

Also, why is copy the whole text under "Report a problem" forbidden?

John

---

### Post by ubfan1 on 2014-07-25
On my pretty current 14.04 Ubuntu, evolution 3.10.4-0ubuntu1 is what is installed.  Where are you getting version 3.13.3?

---

### Post by cigtoxdoc on 2014-07-25
Evolution 3.13.3-fta1 comes from synaptic with gnome3 repository from launchpad.  No evolution in synaptic after I upgraded to 14.04 earlier this week.  

John

---

### Post by Elfy on 2014-07-25
ppa's can break things, nothing new there, don't use them unless you're sure of what's going to happen

the highest repo version of evolution is 3.12.2 and that's in utopic which doesn't release till October

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)

check the warning there

---

### Post by Elfy on 2014-07-25
> I would like to have an explanation from the gurus of Ubuntu as to how I am suppose to run my business without the most important programs on my PCs: Evolution 3.13.3?Stick to supported versions.

and I'm no guru - I'm just sensible

---

### Post by cigtoxdoc on 2014-07-25
A quick check of the gnome-evolution list shows that I am not the only adventurous one.  More importantly, going back to an earlier version is not advised.  So, I can live with the occassional problems.  Unfortunately, to make Ubuntu usable for my business, I have to use proprietary software such as Studio Pro 9 and Crossover as well as software from various ppa such as the one that provides Oracle Java 8.

John

---

### Post by bapoumba on 2014-07-26
It is not about being adventurous, it is about being aware of what ppas are about and what the risks are. I do use ppas, broken dependencies or failed upgrades are quite common. None of the ppas are "official", that is why they are not in the "official" repositories. You use them at your own risks.> Unreportable Reason -- This is not an official Ubuntu package. Please remove any third party package and try again
A vanilla install does not run into such problems. Had a quick look on Launchpad, which ppa are you using for Evolution 3.13.3 ?

---

### Post by buzzingrobot on 2014-07-26
Evolution 3.10.4 is the version in the Trusty repos. It's listed in Synaptic here. 

The latest version in the Gnome team PPA is 3.10.3.

The version in the Gnome team's staging PPA for 14.04 is 3.12.4.  Note this PPA displays this warning:> The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

---

### Post by bapoumba on 2014-07-26
Thanks buzzingrobot, that is also what I came up with :)
Being a production system for a business, I was surprised they would use the staging ppa. Maybe the OP used some other third party repo, and that was my question.

What the OP also needs to understand is once a third party repo or ppa is added, it will be part of the updates/upgrades packages managers see and offer, unless the working packages versions are pinned.

---

### Post by buzzingrobot on 2014-07-26
> **bapoumba said:**
> 
What the OP also needs to understand is once a third party repo or ppa is added, it will be part of the updates/upgrades packages managers see and offer, unless the working packages versions are pinned.

I kinda like Evolution. Annoyances:  It bounces up a "no network" error message when the machine wakes from sleep and the net link hasn't been instantly restored, and it also likes to complain about pings to my IMAP server timing out, after which it won't update at all, manually or otherwise.

Forgetting about PPA updates has burned me once or twice. Pinning can be confusing.  A on-off switch on an updating tool -- "Include PPA's - Y/N" -- would be interesting.

---

### Post by Elfy on 2014-07-26
closing thread, op error.

---

