---
title: "Grub vs Grub2?"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Riverglen on 2010-05-11
I've recently upgraded two machines to version 10.4, with no problems whatsoever.  Both machines were upgraded from version 9.10 from the package manager when it notified me that the new version was available.  Have done this through several consecutive versions on both machines, no fuss, no muss.  Both machines are set up to dual boot XP and Ubuntu.

My question is that, based on many postings in this forum, I learned that the world apparently moved on from Grub to Grub2, starting with version 9.10.  But it didn't happen for me, upgrading the existing installations as I did.  I'm still booting with the old Grub.  So, how come I missed the bus?  Do I care?  What does Grub2 do for (or to) me that Grub doesn't?

---

### Post by 2hot6ft2 on 2010-05-11
[Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")
Explains the differences better than I could.
:popcorn:

---

### Post by oldfred on 2010-05-11
I think as part of the update process the assumption is if it works do not break it. Some have customized their old grub menus and that was difficult to convert.

But old grub has not been maintained for years. Each distribution may have added fixes (Ubuntu added support for ext4 with 9.04) but to be able to handle all the new features a total new version was required. New features, more capabilities have added some complexity but part of it is us learning the differences.  

A few have had real issues for whatever reason (there are a few real issues still, but many of those are caused by other programs) and bad mouth grub2. Most of us that have it find it just works.

---

### Post by Riverglen on 2010-05-12
Well, I guess I'm a pupil of the "if it ain't broke, don't fix it" school of thought.  I certainly don't need a lot of "features" beyond the ability to boot either operating system from the menu.  I still am wondering why I never was offered the option or forced to upgrade to Grub2 during the overall upgrades to Ubuntu itself?
I'm not sure, but the last clean install I did (vs upgrading or installing over an older version) was probably 9.04, and didn't encounter Grub2 at that time.  Haven't read the suggested link explaining the differences, but will do so.

---

### Post by darkod on 2010-05-12
I'm not sure what the reason is, maybe because users are familiar with the old grub1, but the upgrade of grub is not forced when upgrading to 9.10 or 10.04.

There is a command to issue in terminal once the system is upgraded (and yours is now).

I think it was literary like

sudo upgrade-from-legacy

It might be in the grub2 links provided. If not, it shouldn't be difficult to find.

Personally, my first contact with ubuntu was 9.10 which came with grub2. Earlier, years ago, I had some limited experience with Mandrake and Fedora. I'm not someone customizing grub immediately and maybe because of that I didn't mind grub2 at all. The few basic things to customize like default OS, timeout, etc are very easy in grub2 also.
And the os-prober is definitely a nice feature.

So I'm not one of the people against this "change".

---

### Post by cj.surrusco on 2010-06-01
I have problems configuring grub2. They tried to make it easier by having it automatically detect partitions, but it is now hard to add/remove/customize all of the different OS's.

---

### Post by darkod on 2010-06-01
> **cj.surrusco said:**
> I have problems configuring grub2. They tried to make it easier by having it automatically detect partitions, but it is now hard to add/remove/customize all of the different OS's.

Not at all, depends what you want to do.

You could let the os-prober detect all of them, and to avoid syntax erros simply copy the entries you want to keep in /etc/grub.d/40_custom

Then disable the executive bit of os-prober, even adjust the titles if you want in 40_custom, etc.

This is just one example. There is a lot to play around.

---

### Post by oldfred on 2010-06-01
I did pretty much what darko suggests with a partial custom menu or you can create a totally customized version.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by cj.surrusco on 2010-06-01
> **darkod said:**
> Not at all, depends what you want to do.

You could let the os-prober detect all of them, and to avoid syntax erros simply copy the entries you want to keep in /etc/grub.d/40_custom

Then disable the executive bit of os-prober, even adjust the titles if you want in 40_custom, etc.

This is just one example. There is a lot to play around.

I was hoping someone would prove me wrong. I'll check that out.

---

