---
title: "from 10.10 to 14.04"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by karel2 on 2014-11-08
I have a netbook still running ubuntu 10.10, it could not be upgraded because of some legacy application. Now that I am finally ready to upgrade, I type (as root, in a text screen ctl-alt-F2) do-release-upgrade but got only error messages, the last being that natty.tar.gz.gpg could not be found. Before that came something like "error: upgrade tool not found"

Other computers on the same network can and do upgrade regularly so connectivity must be ok.

What is wrong and what can be done about it?
Apologies if the question (or similar) has been posted before, I did try searching.

[[edited to add: if I need to first upgrade to an intermediate version, likely 12.xx, how to do that? ]]

---

### Post by Impavidus on 2014-11-08
You would have to upgrade 10.10&#8594;11.04&#8594;11.10&#8594;12.04&#8594;14.04. Only the last two of those are still supported, so that means fiddling with your software sources to get to the old releases server. Even then, it will take a long time (could be up to a day) and the chance that something doesn't work is quite large.

I really recommend a clean install of 14.04. That will be much easier, faster and more reliable. By doing a clean install you'll lose your current set of installed applications and settings, but many of those are no longer applicable anyway.

---

### Post by oldos2er on 2014-11-08
I would make a clean install of 14.04. The amount of upgrading (and upgrading to EOL releases such as Natty) you would need to do to bring your computer up to date is too painful to contemplate.

---

### Post by karel2 on 2014-11-08
Thanks, chaps, will have to clean install, then. Can't help feeling disappointed in Ubuntu, though - support for legacy versions is one point where an O/S can stand out from the crowd. HP-UX was always very good at it. But ok, enough whining, I'll gather my courage and will perform a clean install.

---

### Post by coffeecat on 2014-11-08
> **karel2 said:**
> Can't help feeling disappointed in Ubuntu, though - support for legacy versions

The release notes for 10.10 would have been clear - support for 18 months only. 10.10 was an intermediate release, really only for those who don't mind frequent upgrades or re-installs and who want the latest. LTS versions, released every two years, are for those who need support to last for years. The current 12.04 and 14.04 LTS versions will receive support for 5 years from release. No reason to be disappointed.

---

### Post by karel2 on 2014-11-08
Ah, thanks, that's a lesson learned. I do dislike upgrades, as I have indeed no requirement to be at the edge of progress. So I better remain on the xx.04 releases, from now on. One only learns from erring, I have been told.

---

### Post by coffeecat on 2014-11-08
Yes - just to be clear. If it's an *.04 release and the year number is even, it's an LTS. At least so far! Since 13.04 the intermediate releases have been supported for 9 months only, so another reason to stick with LTS if you don't like frequent upgrades or re-installs.

But please keep an eye on things. There are mutterings on the horizon about moving to a rolling release model. That will probably only affect intermediate releases, but whatever shakes out of those plans may affect the way LTS versions are released and supported.

---

### Post by karel2 on 2014-11-08
Sincere gratitude, sir/lady, for the background info. Keeping an eye open is indeed what I neglected and I will be paying the price for that.

---

