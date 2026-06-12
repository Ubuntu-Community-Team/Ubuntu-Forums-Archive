---
title: "Is there something wrong with the ISOs?"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by joflow on 2006-06-08
I've never had any problems installing Ubuntu before.  I've installed 5.10 twice and various dapper alpha/beta versions numerous times from downloaded ISOs.  But every since 6.06 went official I have been unable to install from ISOs.  First, I tried using the alternative install CD at work.  The install just randomly stops and I'm left with a black screen and an incomplete install.  At home, I tried installing via the live CD.  The usplash screen hangs at "setting up keyboard support" then I get some IO error.

I've checked my ISOs..I've downloaded from different locations.  I've re-downloaded, re-tried and I've failed everytime.  I can't get this to work.  Whats going on?

---

### Post by aysiu on 2006-06-09
> I've checked my ISOsHow exactly did you check the ISO? This way? ```
md5sum -c *nameofiso.iso.md5*
```

Did you try burning them at a slow speed--4x, for example?

---

### Post by joflow on 2006-06-09
[QUOTE=aysiu]How exactly did you check the ISO? This way? ```
md5sum -c *nameofiso.iso.md5*
```

Did you try burning them at a slow speed--4x, for example?[/QUOTE]

I checked my CD with the "Check Your CD for Errors" option on the install menu.  And I burned at 4x.

---

### Post by wpshooter on 2006-06-09
joflow:

Are you trying to install to machines that already have existing O/Ss on them or are the machines/hard drive blank ?

What I have found, is that it is helpful if you **wipe** the hard drive clean before trying the installation.

---

