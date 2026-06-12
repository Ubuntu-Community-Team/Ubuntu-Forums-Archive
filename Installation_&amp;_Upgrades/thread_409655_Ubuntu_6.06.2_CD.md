---
title: "Ubuntu 6.06.2 CD?"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2007-04-14
Is there an Ubuntu 6.06.2 CD (similar to the way an Ubuntu 6.06.1 CD was released after hundreds of updates)?

If so, where can it be downloaded from?

If not, I think that it is about time to have one. There have been (approximately) a zillion updates since the release of 6.06.1... :)

Thanks,
Alex

---

### Post by zvacet on 2007-04-14
Of course you get many updates,bacause your version is 8-9 months old and will be suported until 2009.Do you realy belive that you can live without updates for 3 years?

---

### Post by meng on 2007-04-14
OP seems a reasonable request, not quite sure why it deserved the dismissive response.  If 6.06.2 is not out yet, it does seem as though it's due!

---

### Post by xp_newbie on 2007-04-15
> **meng said:**
> OP seems a reasonable request, not quite sure why it deserved the dismissive response.  If 6.06.2 is not out yet, it does seem as though it's due!

Thank you for understanding the meaning of my post as it seems that zvacet misunderstood me: The more updates the merrier, but if I am reinstalling Ubuntu 6.06 on a **new** system, I would like to be able to do it from a CD that minimizes (as much as possible) the time that it takes to bring the system up-to-date over a slow download Internet connection.

Regards,
Alex

---

### Post by mgmiller on 2007-04-15
> If 6.06.2 is not out yet, it does seem as though it's due!

This does seem to be a reasonable request.  Especially for the LTS version.  I would think every 6 months or so, (maybe even sooner, like 3 months), they should upgrade the .iso you download so it's at least up to date at that point.  With a slow internet connection, it could easily take much longer to do the upgrades after the install than it took to install and configure the OS to begin with.

---

### Post by zvacet on 2007-04-15
If you want to install dapper on new comp and be up  to date you can use AptonCD
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by xp_newbie on 2007-04-15
> **zvacet said:**
> If you want to install dapper on new comp and be up  to date you can use AptonCD
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

Thank you for this link - I didn't know about the existence of such tool. This can indeed be a solution in the case I described above.

Still, I think Ubuntu 6.06.2 CD is better as creating my own APTonCD is more error prone than a CD created by the Ubuntu professionals.

Do you happen to know whether it relies on a cache of downloaded updates? Or does it re-download all updates based on the current snapshot of the system?

What happens if my current system has Evolution uninstalled? Will the APTonCD contain the latest updates for Evolution (as in the 6.06.2 CD)?

Regards,
Alex

---

### Post by xp_newbie on 2007-04-15
OK - got the answers to my questions (based on the [User's Manual]("http://aptoncd.sourceforge.net/doc-manual.html")):

> **xp_newbie said:**
> Do you happen to know whether it relies on a cache of downloaded updates?

Yes, "By default, all packages saved in /var/cache/apt/archives/ directory are listed and checked". 

> **xp_newbie said:**
> Or does it re-download all updates based on the current snapshot of the system?

No.

> **xp_newbie said:**
> What happens if my current system has Evolution uninstalled? Will the APTonCD contain the latest updates for Evolution (as in the 6.06.2 CD)?

Yes. It's possible to add other deb packages inside the APTonCD media, even those that weren't installed using the apt-get tools. 

Good to know. :)

Regards,
Alex

---

### Post by xp_newbie on 2007-05-26
Well, I just re-installed Ubuntu 6.06.1 and the update manager had **125 updates** for me... It took a while to download **160MB**...

It's definitely time for a 6.06.2 CD.

I will try to use APTonCD next time.

---

### Post by SgtDude on 2007-05-29
I'm trying to get aptoncd installed on 6.06.  Does anyone know which repo it's hiding in?  I've got "dapper main restricted universe" and "dapper-backports main restricted universe" in my sources.list and no luck.

---

### Post by zvacet on 2007-06-03
You can download it from here

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by ccw on 2007-06-07
> **meng said:**
> OP seems a reasonable request, not quite sure why it deserved the dismissive response.  If 6.06.2 is not out yet, it does seem as though it's due!

Yes, periodic point releases/revisions/roll ups/service packs/whatever is a reasonable request for LTS releases. Debian released 6 such revisions to sarge after its original release.[http://www.us.debian.org/News/2007/20070407](http://www.us.debian.org/News/2007/20070407) . Its nothing out of the ordinary.

---

### Post by reckless2k2 on 2007-06-07
i thought the rumble out there was that a 6.06.2 was supposed to come out around the time of 7.04 or maybe it'll be by 7.10. i thought it was supposed to have their "SP" updates every other distro to keep up with package updates and kernel changes.

---

