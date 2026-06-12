---
title: "How to stick with LTS Maverick?"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by ticket on 2010-10-31
I want to stay with release 10.10 (maverick) until the support expires.
So how should I configure 'software sources' so that I don't get offered to upgrade to the next release (11.04?).

When on 10.04, I had the 'show new distribution releases' set to 'Long term support releases only', but it didn't offer the upgrade from 10.04 to 10.10 unless I changed it to 'Normal releases'.

Should I now be setting it back to 'Long term support releases only' in order to stay with maverick?  What would I miss out on if I do that?

---

### Post by awam66 on 2010-10-31
Under the "Updates" tab click on the Release Upgrades and choose "Long Term Releases Only"

---

### Post by cpmman on 2010-10-31
10.10 is not an LTS - 10.04 is.

The next LTS will be 12.04

---

### Post by ticket on 2010-10-31
> **cpmman said:**
> 10.10 is not an LTS - 10.04 is.

The next LTS will be 12.04

oops - does that mean I should have stayed with 10.04?
I thought 10.10 was a bug fixing edition ...

---

### Post by cpmman on 2010-10-31
10.10 is only 20 days old with a few as yet unfixed bugs - 10.04 has had 6 months of bug fixes and is probably more stable - depending on hardware configuration.

Your choice whether to stick with 10.10 or re-install 10.04 - depends how much personal configuration you have done to it and how comfortable you are with waiting for fixes.

---

### Post by theozzlives on 2010-10-31
> **cpmman said:**
> 10.10 is only 20 days old with a few as yet unfixed bugs - 10.04 has had 6 months of bug fixes and is probably more stable - depending on hardware configuration.

Your choice whether to stick with 10.10 or re-install 10.04 - depends how much personal configuration you have done to it and how comfortable you are with waiting for fixes.

Rely on your self control. When the "upgrade" button appears, don't click it. If 10.10 is working, you don't have to upgrade until EOL.

---

### Post by ticket on 2010-10-31
This explains it quite well:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Just wish I had read it earlier!  Don't know how I got it in my head that *.10 fixed up *.04 releases.  Oh well.

I may revert to 10.04 after all.

Is there a way of altering the thread title to say 
"How to stick with LTS Lucid?"

---

### Post by coffeecat on 2010-10-31
> **ticket said:**
> I may revert to 10.04 after all.

If you find it stable, why not stick with it? It's supported for 18 months, right up until the next LTS release.

---

### Post by ticket on 2010-10-31
> **coffeecat said:**
> If you find it stable, why not stick with it? It's supported for 18 months, right up until the next LTS release.

The chart on [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) says support for 10.04 ends mid 2013, while that for 10.10 ends 1st quarter of 2012 ?

---

### Post by coffeecat on 2010-10-31
> **ticket said:**
> The chart on [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) says support for 10.04 ends mid 2013, while that for 10.10 ends 1st quarter of 2012 ?

Correct, and the next LTS will (most likely) be 12.04, which will be released in April 2012.

---

### Post by 73ckn797 on 2010-10-31
> **theozzlives said:**
> Rely on your self control. When the "upgrade" button appears, don't click it. If 10.10 is working, you don't have to upgrade until EOL.
This would be your best course of action to keep the LTS release or the current version you have.
If you want LTS then revert back to 10.04 and do not think that you "have" to upgrade to the latest version.

---

### Post by Cavsfan on 2010-10-31
I told myself I was sticking with 10.04 LTS until the next LTS, but when the RC was released for 10.10 on 10/10/10 
I could not resist and upgraded. That appeared to be fine, but I ended up backing stuff up and doing a clean install.

I tried, but I could not resist and I probably will not be able to resist the next one either. :)

I agree with the others, if 10.10 works, stick with it, unless you just want to go back to 10.04.

---

### Post by ticket on 2010-11-01
I noticed that 10.10 introduced newer versions of some packages.  E.g. avidemux was at version 2.5.2 on 10.04, but got upgraded to 2.5.3 in 10.10.

If I had stayed with 10.04, would there become a time when avidemux, mplayer, etc get upgraded, or would I be always stuck with the older versions of these packages?

---

### Post by coffeecat on 2010-11-01
> **ticket said:**
> If I had stayed with 10.04, would there become a time when avidemux, mplayer, etc get upgraded, or would I be always stuck with the older versions of these packages?

No and yes. The advantage of LTS releases is that you get stability. The disadvantage is that the only updates for repository apps are for bugfixes and security patches.

People complain about this but there is a reason - two reasons - for this.

Newer versions of apps may not be compatible with earlier versions of shared libraries. This is particularly a problem with different versions of the gnome desktop. The repository packages are designed and compiled to work with each other.

The LTS releases are partly (perhaps mostly) targeted at the enterprise. In a business environment you don't want the cost of retraining staff every time an app changes its interface, or adds new features.

So - if you want newer versions of apps, go for newer versions of Ubuntu. If you want tried and tested, but perhaps a version or three behind, stick with LTS.

---

### Post by ticket on 2010-11-02
Thanks for the good explanation, coffeecat.  I'll tread the new ground with 10.10 and upwards!

---

### Post by Old_Grey_Wolf on 2010-11-02
> **coffeecat said:**
> If you find it stable, why not stick with it? It's supported for 18 months, right up until the next LTS release.

+1

The support for 10.10 ends at the same time that 12.04 LTS is released. Upgrade then. In the meantime, just ignore the notification that an upgrade is available.

---

