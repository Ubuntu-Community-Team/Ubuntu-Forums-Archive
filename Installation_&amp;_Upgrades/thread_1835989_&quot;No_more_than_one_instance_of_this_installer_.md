---
title: "&quot;No more than one instance of this installer can be running at a time&quot; error"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by lolwhites on 2011-08-30
I am trying to install the driver for Polyvision interactive whiteboards. After downloading and unzipping the setup file from their website, when I try to run it, I get the error message *No more than one instance of this installer can be running at a time*. According to their documentation, it should work for 10.10+, and I'm running 11.04 with Unity 2d.

I have tried running it in a terminal, just to be sure I wasn't clicking multiple times by mistake, but the same thing is happening. A Google search for the phrase returns one hit for an unrelated installer, reporting the problem in Fedora but not Ubuntu.

The setup file can be downloaded by going to [http://downloads.polyvision.com/support/downloads](http://downloads.polyvision.com/support/downloads) and searching for Product=eno classic, Type=drivers OS=Linux, Language=English

---

### Post by dino99 on 2011-08-30
Maybe try without their driver. (in case they are using a wildly opensource distributed driver included as a kernel module).

What if I have additional questions?

For additional information please send all inquiries to: PolyVision Customer Service at [email]customerservice@polyvision.com[/email] or call 1-800-620-POLY (7659).

---

### Post by lolwhites on 2011-08-30
Turned out I had to run it in a root terminal.

---

### Post by frogotronic on 2012-08-20
> **lolwhites said:**
> Turned out I had to run it in a root terminal.

Did you ever get your Polyvision board working?

Thanks,
CH

---------------------------------------------------------

Yep, installed the drivers (put them in /opt/PolyVision/PolyVisionDriver) and the ENO board works perfectly!

- CH

---

