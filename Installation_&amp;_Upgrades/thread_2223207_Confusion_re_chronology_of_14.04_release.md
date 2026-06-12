---
title: "Confusion re: chronology of 14.04 release"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by Kurt_Alan on 2014-05-09
**[COLOR="#000000"][SIZE=5][/SIZE][/COLOR]**

When I upgraded from 12.04 LTS to 14.04 LTS I used: ```
 sudo update-manager -d 
```

I understand that "-d" means development.  TT came out on April 14.  I thought it was out of beta then.  Now I hear it is coming in July.

I don't understand this grey area interim period.  Is this equivalent to Window's Release Candidate?

---

### Post by bruce-hyatt on 2014-05-10
As I understand it, 14.04 was released in April as the new LTS release. If you have 12.04, the last LTS release, the upgrade to 14.04 will be available via the update manager without the -d option in July. If you add the -d option as you did, it upgrades now. It is not considered beta in the interim but I don't know why they delay the upgrade for 12.04 (without the -d option). [See this page]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule").

---

### Post by grahammechanical on 2014-05-10
So, you upgraded using the command sudo update-manager -d. What happened? Did the upgrade succeed? What version of Ubuntu is on your system. Run this:

```
lsb_release -a
```

It should say Ubuntu 14.04 LTS and not 14.04 (development branch). It is possible that you have upgraded into 14.04 LTS and then into the Utopic Unicorn (14.10 development branch). I do not know.

Once a version of Ubuntu is released the code in the ISO image is fixed which is why we tick to install updates at the same time as installing Ubuntu. The OS is then up to date with security and bug fixes. Things are done slightly different with LTS releases. They get what are called point releases. This used to happen every six months for the first two years by which time the next LTS version would be available. Ubuntu 14.04 LTS will get its first point release in July (24th). Then it will become 14.04.1. You will also notice that 12.04 gets its 5th point release in August - 12.04.5. These point release are all slightly different ISO images to the earlier images.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

These point releases keep the LTS release up to date with more recent hardware improvements by the Linux developers.

If you are indeed on 14.04 LTS then do not run update-manager -d or you will be upgrade into Utopic Unicorn (14.10 development branch).

Regards.

---

### Post by deadflowr on 2014-05-10
> **Kurt_Alan said:**
> 

When I upgraded from 12.04 LTS to 14.04 LTS I used: ```
 sudo update-manager -d 
```

I understand that "-d" means development.  TT came out on April 14.  I thought it was out of beta then.  Now I hear it is coming in July.

I don't understand this grey area interim period.  Is this equivalent to Window's Release Candidate?

It just means the upgrade channel hasn't been officially added yet for LTS upgrades is all
14.04 is an officially released distro.

However, because someone running an LTS is more likely to be in need of a super stable system, they hold off the ability to upgrade them until they are as rock solid as they can be.
Typically, if you look at the overall scheme of Ubuntu, you might notice that 3 or 4 months after release, the system's are normally quite polished, as compared to the initial release.
Even though the initial release might be very stable, an even more stable/rock solid release is even better.

Besides, someone running an LTS is more likely to be in no big hurry to upgrade.

---

### Post by Kurt_Alan on 2014-05-10
[SIZE=5][/SIZE]****

Thanks for the page reference.  Strangely, between the April 17 Final Release of Ubuntu 14.04 LTS and the July 24 "final" release, there are no notes of explanation.

However, there's a clue.  The July release is noted as 14.04.1 and the April's as 14.04.

It seems like in the interim three months Ubuntu will receive bug reports, run updates, and make a final selection of changes to incorporate in 14.04.1.  I'm assuming that if I do a sudo apt-get update from 14.04 that I'll receive these new items.

For the purposes of companies like osdisc.com, I suppose they'll wait for 14.01.

---

### Post by Kurt_Alan on 2014-05-10
[SIZE=5][COLOR="#000000"]****[/COLOR][/SIZE]

I ran ```
 man update-manager 
``` to check the meaning of "-d" and, yes, it does refer to --devel-release.

If so, then how come when I upgraded from 12.04 LTS to 14.04 LTS it outputted this: ```
 Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty 
``` which is NOT the dev release?

***
Re: the other half of your metaphor, what's the tock?

---

### Post by Kurt_Alan on 2014-05-10
[SIZE=5][COLOR="#000000"]****[/COLOR][/SIZE]

O.K., so you are saying that 14.04 LTS is now official.  However, it awaits its upgrade channel to 14.0.1 AND its appearance when running sudo apt-get update without any flags?

---

