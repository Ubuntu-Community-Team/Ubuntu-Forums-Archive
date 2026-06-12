---
title: "Synaptic updated my system to an X-windows malfunction."
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by phm on 2005-10-02
Hi,

I installed Ubuntu Linux 4.10: The Warty Warthog about a month ago. (I used that version because I had the CD I burned to test it last year but couldn't get it to start under Windows ME.) I'll not dwell on the initial installation problem, suffice it to say that the system ran for about 2 weeks. I would regularly get other packages through the net, and would at the same time also get any updates that were available. Friday afternoon 16th of september, I suddenly got a massive download took long enough to prepare and eat dinner, and after a reset (I can't recall whether I was asked, wether the update hung, or whether it was automagical) it announced itself as Hedgehog and told me my X-windows wasn't configured correctly, and was switched off for now. "For now"!
Not having anything to go on I had to reinstall the system, and am again running OK for 2 week, but I've yet to install a single package or update, as I would like to know what happened, whether it will happen again, and how I can carry on regardless.

BFN,
                                                                                                                          PHM

---

### Post by jasmuz on 2005-10-03
Did you try running from the console :

sudo dpkg --configure xserver-xorg

---

### Post by phm on 2005-10-03
[QUOTE=jasmuz]Did you try running from the console :
sudo dpkg --configure xserver-xorg[/QUOTE]Nope. Was there a way I could have known to?
- If I do that, now that the system is more or less sane, what would happen?
- If I do that when the same thing happens again, what shoud happen?
BFN, 
........................................................................................... PHM

---

### Post by darkmatter on 2005-10-03
Since the update identified itself as 'Hedgehog', you had obviously dist-upgraded to 5.04 (willingly, I'd assume. I've never heard of apt forcing a dist-upgrade before)

Unfortunately, things can (and will) break during a dist-upgrade. Usually a simple dpkg-reconfigure xserver-xorg will fix the problem, but not always.

The best advice I can give without more info on the situation is to download the hoary cd and install that, since it seems that the updates you have been getting are for hoary.

---

### Post by phm on 2005-10-03
> **darkmatter]Since the update identified itself as 'Hedgehog', you had obviously dist-upgraded to 5.04 (willingly, I'd assume. I've never heard of apt forcing a dist-upgrade before)[/QUOTE]
Nope said:**
>  Unfortunately, things can (and will) break during a dist-upgrade. Usually a simple dpkg-reconfigure xserver-xorg will fix the problem, but not always.
That is indeed unfortunate, considering that we get these regularly. It would be more Ubuntu to provide a migration path.
- What does ' dpkg-reconfigure xserver-xorg' do? (Darkmatter solution)
- What does 'dpkg --configure xserver-xorg' do? (Jasmuz solution)
- How does the desktop user know to try these?
> The best advice I can give without more info on the situation is to download the hoary cd and install that, since it seems that the updates you have been getting are for hoary.
Well, my original intention was to test Warthog, then wait for Badger and install that. After my experiences so far I'm not so sure I want to do another install from scratch, though. Warthog was adamant about being installed to a clean partition, but that partition now holds home directories, mail, documents, settings, scripts and whatnot.  I wouldn't want to wipe all that for an update, or an upgrade. (Then there's also the matter of the distributions not being available in an install-archive, but requiring a CR-writer.) So if these two commands are likely to help me migrate, and I can find out how to do so on purpose, that might be preferable.
BFN,
.................................................. ......................................... PHM

---

### Post by Mustard on 2005-10-03
You could backup the majority of your custom settings and then make a clean install, followed by a restoration of your custom settings ( ie reinstalling your home directory from the backup.).

I noticed you are often asking the question, how would a user know to do such and such.  The answer to that question is that they would need to find out by researching it themselves or asking someone else what to do.  So far you are going fairly well with the asking someone else what to do part.  Knowledge of an operating system is not imprinted in our brains at birth.  It is acquired through study.  I imagine you have a good working knowledge of the Windows operating system, because you have tried it, worked out the kinks and are now proficient with the operating system.   With time and patience I think you will learn to be proficient in this operating system as well, if you are so inclined.

The question of whether the system will do this to you again is a difficult one to answer.  99.99% of people using Ubuntu don't have any issue with the system suddenly deciding it wants to upgrade from Warty to Hedgehog.  Some user action must have taken place to make this event come about.  The user could have been you, or someone else who uses your computer (either with or without your knowledge).  Whatever the case may be, somebody made it upgrade to Hoary.  So next time, make sure nobody does it again. :D

If I was to guess what might cause such a problem, I would say a potential cause would be that someone running Warty could accidently copy a Hoary sources.list to there /etc/apt/ directory and Synaptic was using the hoary repositories instead of the Warty repositories.

---

### Post by phm on 2005-10-04
> **Mustard]You could backup the majority of your custom settings and then make a clean install, followed by a restoration of your custom settings ( ie reinstalling your home directory from the backup.).[/QUOTE]
OK. I tried that last time and lost basically everything not written by a user. I've since determined some pittfalls in case I have to do this again. What I do not know, however, is whether there are settings outside /Home that need paying attention to.
> I noticed you are often asking the question, how would a user know to do such and such.  The answer to that question is that they would need to find out by researching it themselves or asking someone else what to do. So far you are going fairly well with the asking someone else what to do part. 
The reason I ask is: If it's my own ignorance that got me into trouble, that's a matter of preparedness. But if it's a flaw in the information flow, then it ought to be improved upon. Yor anwer suggests desktop users are indeed left hanging when the gnome desk top doesn't load. I don't find that acceptable. (Yes, now(!) I can ask someone else, since the system is OK now said:**
> I imagine you have a good working knowledge of the Windows operating system ... With time and patience I think you will learn to be proficient in this operating system as well, if you are so inclined.  My knowledge of the AMIGA OS is indeed more than sufficient. Unfortunately I've also been forced to force Microsoft Windows into performance, and I'd rather not go that same way on Linux. As I see it: If I need to ask, then the implementation is less than perfect.
> The question of whether the system will do this to you again is a difficult one to answer. ... I would say a potential cause would be that someone running Warty could accidently copy a Hoary sources.list to [their] /etc/apt/ directory and Synaptic was using the hoary repositories instead of the Warty repositories.
(And this is something the system doesn't guard against? )
OK, so:
- Backup the /Home. (Move /Home away from the system partition?) Any others?
- Take care to use a Warthog sources.list only.
- Should it happen again anyway, (scream, punch any available soft item and) use one of the commands given before to reconfigure X-windows. Is there a preference/difference?
- When happening across a CD-writer, write a CD for a later OS version, since for some reason the ISO-s can't be used to install an OS with. (Then again, mayby unpacking the ISO to a bootable partition might?)
Thanks,
........................................................................................................... PHM

---

