---
title: "Lucid Lynx and stability"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blueshiftoverwatch on 2010-02-06
So, the next release this April is going to be an LTS. Which theoretically means that most of the development will be focused towards providing a stable platform by fixing existing bugs rather than testing out new features. I have two questions about Ubuntu and stability:

1. How much more stable are LTS releases on average than standard releases?

2. By how much does enabling all of the updates in Synaptic (like proposed updates) decrease the stability of Ubuntu overall?

I generally use the most up to date version of Ubuntu as well as enable all possible updates. But, I think that when Lucid comes out in April I might just do a fresh install, play it safe with updates, and attempt to enjoy a more stable OS rather than living on the bleeding edge.

---

### Post by OrangeCrate on 2010-02-06
> **blueshiftoverwatch said:**
> So, the next release this April is going to be an LTS. Which theoretically means that most of the development will be focused towards providing a stable platform by fixing existing bugs rather than testing out new features. I have two questions about Ubuntu and stability:

1. How much more stable are LTS releases on average than standard releases?

2. By how much does enabling all of the updates in Synaptic (like proposed updates) decrease the stability of Ubuntu overall?

I generally use the most up to date version of Ubuntu as well as enable all possible updates. But,** I think that when Lucid comes out in April I might just do a fresh install, play it safe with updates, and attempt to enjoy a more stable OS rather than living on the bleeding edge**.

After what seems to be a never ending series of problems for many with Karmic, I think a lot of people will agree with your decision.

[http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html](http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html)

Frankly, I may do the same.

---

### Post by arnab_das on 2010-02-06
question to people who have 'upgraded' to lucid lynx: how did the upgrade go?

---

### Post by blueshiftoverwatch on 2010-02-06
Also, if I overwrite my currently existing Ubuntu partition with a new release. Will my other two OS's (XP and 7) continue to be properly detected by default?
> **arnab_das said:**
> question to people who have 'upgraded' to lucid lynx: how did the upgrade go?
I don't think it's fair to judge the quality of a final product based on the alpha versions people are currently only using halfway through the release cycle.

---

### Post by LowSky on 2010-02-06
> **arnab_das said:**
> question to people who have 'upgraded' to lucid lynx: how did the upgrade go?

well my nvidia drivers wont work for nothing, but I know what to expect from a alpha (I've been alpha testing since 7.10).

Don't install unless you like looking for problems

---

### Post by MasterNetra on 2010-02-06
> **blueshiftoverwatch said:**
> Also, if I overwrite my currently existing Ubuntu partition with a new release. Will my other two OS's (XP and 7) continue to be properly detected by default? ...

It should. After all when you install a new release it usually reinstall grub and as long as grub can reconize XP and 7 it will keep providing the boot option to them. Although if you had custom placed say one of the windows entries to be first on grub's list, you may have to redo that. Otherwise yes when you install a new release it should still properly detect it by default.

---

### Post by XubuRoxMySox on 2010-02-06
> **arnab_das said:**
> question to people who have 'upgraded' to lucid lynx: how did the upgrade go?

They warn against doing that. But I went and did it anyway (brave or foolish, I dunno, but I'm definitely lucky). Most folks I heard from that are using Ubuntu who tried it were unsuccessful and had to do a re-install of Karmic and download the CD instead. I'm using Xubuntu - I dunno if that's a factor - and had a flawless upgrade to Lucid. Beginner's luck? :D

Lucid is more stable for me, and *much* faster. No update has borked my system yet (fingers crossed), but watch out for PulseAudio. Xubuntu doesn't ship with it, but I had it installed as a dependency of Skype and it got messed up in an update. Completely removing it, then re-installing it from the new repo seems to fix it for most of the folks who have written about it.

-Robin

---

### Post by RiceMonster on 2010-02-06
They aren't anymore stable than the other releases. They just have a longer support life, which means more time for bug fixes. Hardy Heron was the first release to ship with Pulse Audio, which caused all kinds of problems, and shipped with firefox 3 beta 5. I guess the idea is "stable over time", not "release stable".

---

### Post by OrangeCrate on 2010-02-06
> **arnab_das said:**
> question to people who have 'upgraded' to lucid lynx: how did the upgrade go?

I never have much luck with upgrades, though others do, I guess. I downloaded and installed Lucid at Alpha 2 (a week or so ago).

For an Alpha, it runs pretty smooth and stable (frankly, I was a bit surprised, having run every dev version since 6.06).

My experience doesn't mean that most should jump on it now though. If a person doesn't know how to back out of, and fix a situation, after something borks, they should leave Lucid alone, at least until the first Beta is released.

But, if you, or anyone else feels lucky...

[http://cdimage.ubuntu.com/releases/lucid/alpha-2/](http://cdimage.ubuntu.com/releases/lucid/alpha-2/)

[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

---

### Post by blueshiftoverwatch on 2010-02-06
> **RiceMonster said:**
> They aren't anymore stable than the other releases...the idea is "stable over time", not "release stable".
I didn't know that.

---

### Post by chriswyatt on 2010-02-06
> **RiceMonster said:**
> They aren't anymore stable than the other releases. They just have a longer support life, which means more time for bug fixes. Hardy Heron was the first release to ship with Pulse Audio, which caused all kinds of problems, and shipped with firefox 3 beta 5. I guess the idea is "stable over time", not "release stable".

Though, saying that, they're probably less likely to introduce too many new features that might reduce the overall stability.  Firefox 3 Beta 5, yes it was a beta but it was a stable enough beta and it's not like Firefox is core to the OS.

If people had any stability problems with Firefox Beta they could've easily just installed another browser.

EDIT: I don't know this for a fact though, I might be wrong.

---

### Post by XubuRoxMySox on 2010-02-06
I'm not sure if any such assumption is truly justified, BUT...

Lucid is being built on Debian _Testing_ instead of the usual Debian _Unstable_ base. So, um... perhaps it will be at least "less unstable" than others.

-Robin

---

### Post by aaaantoine on 2010-02-06
Yeah, LTS is not going to be "stable" -- as in fewer bugs -- when it releases.  The idea is you get Long Term Support.  You get support for 3 years past the release date, so you'll have fewer bugs down the line.

The other half of that is you keep using the same software for up to 3 years, which in a production environment means fewer surprises.  Fewer new shiny things, yes, but you get a more predictable system.  That's "stable" as in no major changes.  No major changes *also* means fewer bugs over time.

...Boy, let's see how many other ways I can say the same thing. :p

---

