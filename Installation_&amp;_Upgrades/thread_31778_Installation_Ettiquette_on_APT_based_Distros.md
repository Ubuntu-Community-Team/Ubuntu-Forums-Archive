---
title: "Installation Ettiquette on APT based Distros"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by kvidell on 2005-05-04
I've always been curious about something...

On these ever so lovely aptitude based distrobutions, with all of it's dependancy checking and version checking and what not... is it "bad ettiquette" to compile things by hand?
Do I run a risk of breaking things by doing so?

I had a friend who always told me, while I used Debian Testing, to compile things by hand only as a last resort, and if naught else, try to make it a deb package and install that, as opposed to compiling it straight.

Any thoughts? Because I don't know how to make deb packages, hah.

(And no, I don't have anything specific in mind I need to compile, I was just reminded it of it by another thread that's on the "New Posts" thinger, asking how to install software with his lack of intarweb.)

Thanks,
- Kev

---

### Post by 23meg on 2005-05-04
for personal use, there's absolutely nothing wrong with compiling from cvs/source even when there are binary packages available. distribution-wise, making .deb packages provides convenience, but releasing source tarballs alone has the advantage of platform independence, especially today when many distros have volunteers and/or workers who handle the job of building stable binaries from source. plus, for the end user, cvs is always the "bleeding edge", whereas distro-specific binaries are the "safe side" (roughly speaking).i think the middle ground here would be trying your best to build working binaries for software that isn't available as binary on your distro, and then sharing these binaries.

---

### Post by kvidell on 2005-05-04
Ah, okay :) Thank you.

He made it sound like apt would go supernova on me and implode in on itself out of jealousy if I compiled anything
(suffice to say I more or less took it with a grain of salt anyway and compiled a couple things here and there..)

---

### Post by 23meg on 2005-05-04
don't worry, apt is a mature, reasonable guy; he wouldn't get envious that easily :)

---

