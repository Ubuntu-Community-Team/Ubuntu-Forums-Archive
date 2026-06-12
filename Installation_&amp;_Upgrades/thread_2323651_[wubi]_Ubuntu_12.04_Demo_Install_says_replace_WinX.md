---
title: "[wubi] Ubuntu 12.04 Demo Install says replace WinXP with Ubuntu"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by EoflaOE on 2016-05-07
I know that it will delete my Windows XP programs, documents, pictures, music, and any other files. So I woke up and turn on my computer when I realized that Ubuntu is appeared on my Windows boot loader, so I go to Ubuntu.

After my computer is making the rumbling noise it will say Completing Ubuntu installation so I press ESC and go to Demo Install, My computer booted into Ubuntu 12.04 Wubi installation and everything looks great, no distortions, no problems at all.

Then I open the "Install" program and selected my language and pressed Enter when my Ubuntu displays That the hard disk /dev/sda is mounted, so I select Yes and it dismounted my /dev/sda when I see the only option was "Replace Microsoft Windows XP Professional with Ubuntu" and the spacer and "Something else"!](*,)

I am confused so is replacing Microsoft Windows XP Professional with Ubuntu affect my Windows XP or just format my primary drive and install Ubuntu on it?

If it formatted my drive and installed Ubuntu will I receive the error message when installing?

---

### Post by mörgæs on 2016-05-07
Hi, welcome to the fora.
Wubi installs Buntu within windows. Better to erase the entire hard disk and install only Buntu, as seen [here]("http://blog.linoxide.com/wp-content/uploads/2015/04/Installation-Type.png").

I recommend X/Lubuntu 16.04 and not Ubuntu 12.04 for old hardware.

---

### Post by Bucky Ball on 2016-05-07
Welcome. Forget Wubi. No longer supported. No longer included on the latest release. Redundant, obsolete and you will get little help with it if you decide to go that way (as VERY few people now use it or remember much about it, although there are one or two out there). It also doesn't work with UEFI, not that XP is necessarily using that.

Boot to XP, create some free space to install Ubuntu, boot from the install media, choose 'Something Else' when you get to the partitioning section, install. Post back if you have issues/questions. ;)

PS: I wouldn't advise 12.04. While it is LTS and still supported until next year, stable and nothing wrong with it, there has been two long-term support releases since. 14.04 LTS, which is rock solid, and 16.04 LTS, which was released a few weeks ago and still a little buggy for some. That will be cleaned up as time goes on and teething problems are ironed out. I will add that I have 16.04 on three machines and it runs fine for me for day to day stuff.

I'd suggest 14.04 LTS or 16.04 LTS. 14.04 can be upgraded to 16.04 directly via the net, perhaps after a few months when the first point release arrives, the dust has settled and things are a little more stable. Good luck.

---

### Post by hakuna_matata on 2016-05-07
> **yazanalhabal said:**
> go to Demo Install
The "Demo mode" runs a kind of [Live_CD]("https://en.wikipedia.org/wiki/Live_CD"). It is NOT a special Wubi live system and the included installer doesn't use a customized Wubi configuration. So good news if you don't want Wubi, you can use the included installer to install Ubuntu with all options of a non-Wubi installation.
> **yazanalhabal said:**
> is replacing Microsoft Windows XP Professional with  Ubuntu affect my Windows XP
If it works as the installer said, it deletes Windows XP. But probably, it is not possible to unmount all partitions for installation because the installation iso, which provides your live system, is located on one of the partitions which should be erased.
> **yazanalhabal said:**
> so I press ESC
If you don't press ESC, "Normal mode" is used. "Normal mode" uses the installer with a customized Wubi configuration.

---

