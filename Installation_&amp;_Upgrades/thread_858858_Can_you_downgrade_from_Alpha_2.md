---
title: "Can you downgrade from Alpha 2?"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by VexVishnu on 2008-07-14
I upgraded to Intrepid Ibex Alpha 2 (the second alpha release of Ubuntu 8.10) with the instructions here:
[http://www.ubuntu.com/testing/intrepid/alpha2](http://www.ubuntu.com/testing/intrepid/alpha2)

I had reported my "no sound" bug on Launchpad they suggested I upgrade to Alpha 2. I did that, but now I can't log on normally or after I enter my screen name and password the screen goes white and stays that way. My mouse moves across it but it just doesn't work in any other way. I have to log in using a Gnome default session. When I upgraded, it asked me to remove approx. 30 packages that were "obsolete" and now when I try to do some things, like watch videos it tells me that I can't but doesn't tell me why. My custom theme doesn't work anymore either.

Is there a way to undo the upgrade or am I s.o.l.?

---

### Post by overdrank on 2008-07-14
> **VexVishnu said:**
> I upgraded to Intrepid Ibex Alpha 2 (the second alpha release of Ubuntu 8.10) with the instructions here:
[http://www.ubuntu.com/testing/intrepid/alpha2](http://www.ubuntu.com/testing/intrepid/alpha2)

I had reported my "no sound" bug on Launchpad they suggested I upgrade to Alpha 2. I did that, but now I can't log on normally or after I enter my screen name and password the screen goes white and stays that way. My mouse moves across it but it just doesn't work in any other way. I have to log in using a Gnome default session. When I upgraded, it asked me to remove approx. 30 packages that were "obsolete" and now when I try to do some things, like watch videos it tells me that I can't but doesn't tell me why. My custom theme doesn't work anymore either.

Is there a way to undo the upgrade or am I s.o.l.?

Hi and first question is why are you using intrepid? Intrepid is in the testing stage and is not recommended for a everyday system. Have you tried to boot into a previous kernel if you updated from Hardy?

---

### Post by Sef on 2008-07-14
> Is there a way to undo the upgrade or am I s.o.l.?

You can't undo an upgrade.  You need to reinstall.

---

### Post by xarquid on 2008-07-14
> **Sef said:**
> You can't undo an upgrade.  You need to reinstall.

There should be some spiffy ways around this by booting up using a LiveCD (or another Linux boot CD) and chrooting your main partition. Then perhaps editing your /etc/apt/sources.list , changing all of your lines back to hardy's repositories and then performing a:

sudo apt-get update

then:

sudo apt-get install
or sudo apt-get upgrade

Would this not work?

Are we sure there are no work arounds?

IF NOTHING ELSE, by all means PLEASE remember to login to your system via a Linux/other bootdisk and grab your /home/* directory/directories so that you can restore these easily (or if they are on a seperate partition -- even better!).

Sincerely,

Craig Huffstetler

P.S. - They really should have a way to downgrade ;-)

---

