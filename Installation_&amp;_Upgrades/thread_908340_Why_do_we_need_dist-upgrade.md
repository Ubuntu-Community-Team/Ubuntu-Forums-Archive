---
title: "Why do we need dist-upgrade?"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2008-09-02
Hello all,

I'm trying to advance my understanding of the way GNU/Linux works, that's why I ask this a bit weird question: why do we need dist-upgrade? What would happen if I take, for instance, Ubuntu 6.10 and do only "apt-get upgrade" every now and then. How would my system differ from Ubuntu 8.04?

Or, take this example: Fluxbuntu is based on Ubuntu 7.10 (+ fluxbox WM). What is the difference in the base system (i.e. Fluxbuntu/Ubuntu minus Fluxbox/GNOME, dunno how to call that) between fully upgraded Fluxbuntu and fully upgraded Ubuntu 8.04 (except for the WM, ofcourse)?

I hope my question is making any sence. :-)

---

### Post by LesFromWaldenVT on 2008-09-02
As I understand it, 'apt-get update' updates the /etc/ file that keeps track of what needs to be updated but it doesn't actually do any downloads or upgrade.

---

### Post by tribaal on 2008-09-02
Indeed, apt-get update only updates the indexes (it fetches the list of most up-to-date packages from the repositories).

The actually upgrading of packets is done with apt-get upgrade.

Hope this answers your question :)

- Trib'

---

### Post by mellowd on 2008-09-02
I think he's asking the difference between apt-get upgrade and a full apt-get dist-upgrade.

The difference is that the latest bleeding edge versions of software are not always going to be in the latest distro. There are a variety of changes, including major version numbers that older versions of the distro won't upgrade into.]

That's the basics

---

### Post by dijxtra on 2008-09-02
Thanks for pointing out the typo :-D I meant "upgrade", not "update". There, I fixed it. Sorry for the confusion.

---

### Post by dijxtra on 2008-09-02
> **mellowd said:**
> I think he's asking the difference between apt-get upgrade and a full apt-get dist-upgrade.
Exactly
> **mellowd said:**
> The difference is that the latest bleeding edge versions of software are not always going to be in the latest distro. There are a variety of changes, including major version numbers that older versions of the distro won't upgrade into.]

That's the basics
Thanks for the basics. Do you have an idea where to look for more detailed explanation?

If I understood correctly what I just googled, my question can be rephrased as "what is the difference between rolling release distros and those which use versions?"

---

### Post by snowpine on 2008-09-02
> **dijxtra said:**
> Hello all,

I'm trying to advance my understanding of the way GNU/Linux works, that's why I ask this a bit weird question: why do we need dist-upgrade? What would happen if I take, for instance, Ubuntu 6.10 and do only "apt-get update" every now and then. How would my system differ from Ubuntu 8.04?

Or, take this example: Fluxbuntu is based on Ubuntu 7.10 (+ fluxbox WM). What is the difference in the base system (i.e. Fluxbuntu/Ubuntu minus Fluxbox/GNOME, dunno how to call that) between fully upgraded Fluxbuntu and fully upgraded Ubuntu 8.04 (except for the WM, ofcourse)?

I hope my question is making any sence. :-)

Hi Dijxtra, each distro of Linux has its own procedure for upgrades. There's no one "best" way, it's just a matter of personal preference. There are distros (Arch comes to mind) with what's called "rolling upgrades;" in other words, upgrades happen as needed and there is no distro release number.

Ubuntu, on the other hand, is designed to update every 6 months on a regular schedule. The main reason for this (as I understand) is so that everyone who's using "Hardy Heron" has a specific set of packages that's distinct from the people using "Gutsy Gibbon." This makes community support easier, which is one of the great things about Ubuntu. If you are using an outdated release (6.10 for example), your packages will be "stuck" at the 6.10 version--you'll never get Firefox 3.0 unless you specifically install it, for example. 

To answer your specific question about Fluxbuntu, you can in fact dist-upgrade it to 8.04 (this is an "unofficial" solution). 
```
sudo nano /etc/apt/sources.list
```
Change every place it says "gutsy" to "hardy". Ctrl+O, Enter to save, Ctrl+X to quit. Then,
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Having done this myself, I can tell you there is no noticable improvement in performance or stability over Fluxbuntu 7.10. Unless you have a very specific need for 8.04, my recommendation is to stick with Fluxbuntu 7.10--it works fine.

---

### Post by mellowd on 2008-09-02
> **dijxtra said:**
> Exactly

Thanks for the basics. Do you have an idea where to look for more detailed explanation?

If I understood correctly what I just googled, my question can be rephrased as "what is the difference between rolling release distros and those which use versions?"


Look at it this way. You have Windows 2000 and you have Windows XP. Microsoft still released updates for Windows 2000 even when Windows XP was being used. In fact, parts might even be the exact same version  (for example, Internet Explorer and so on) but certain fundamentals are different (An example being DX10 on Vista, no DX10 on XP)

---

### Post by dijxtra on 2008-09-02
SO, the *only* difference between fully upgraded Edgy and fully upgraded Hardy is that Hardy has some applications installed by default which Edgy doesn't? And if I install those new applications which Hardy has and Edgy hasn't, I'd get de facto Hardy, with out dist-upgrade, right?

---

### Post by snowpine on 2008-09-02
> **dijxtra said:**
> SO, the *only* difference between fully upgraded Edgy and fully upgraded Hardy is that Hardy has some applications installed by default which Edgy doesn't? And if I install those new applications which Hardy has and Edgy hasn't, I'd get de facto Hardy, with out dist-upgrade, right?

No, the packages (including applications) with Edgy are "locked in" at that version number. Check out [www.distrowatch.org](www.distrowatch.org) for more info; for example, Hardy uses OpenOffice 2.4 and Edgy uses OpenOffice 2.0. If you are in Edgy and you 'apt-get upgrade' you get the latest version of Openoffice 2.0, not 2.4.

---

### Post by dijxtra on 2008-09-02
> **snowpine said:**
> No, the packages (including applications) with Edgy are "locked in" at that version number. Check out [www.distrowatch.org](www.distrowatch.org) for more info; for example, Hardy uses OpenOffice 2.4 and Edgy uses OpenOffice 2.0. If you are in Edgy and you 'apt-get upgrade' you get the latest version of Openoffice 2.0, not 2.4.
Aham! So it's applications and their major versions. I get it now. Thanks!

---

