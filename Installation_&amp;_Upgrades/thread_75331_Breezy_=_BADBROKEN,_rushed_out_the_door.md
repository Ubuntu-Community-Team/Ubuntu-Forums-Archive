---
title: "Breezy = BAD/BROKEN, rushed out the door"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by koua on 2005-10-13
This version should not have been the FINAL version.  It is full of show-stopping and unresolved bugs.

Issue 1: Can't install on machines with adaptec raid (i2o).  Kernel panic before install begins!

Issue 2: Does not run on MPC X3100 latpop.  Stuck at "Starting hotplug subsystem..."

Issue 1 has been reported to bugzilla a while ago - obviously, not resolved.  FYI, this issue did not exist in Hoary.

Issue 2 can probably be resolved by going into rescue mode and stoping the hotplug subsystem from loading - but that will defeat the purpose of Ubuntu being the easiest/friendliest Linux distro to use/run.

What are the odds of having both of my systems not work with Breezy? I hope the NEXT version of Ubuntu gets it right. :(

---

### Post by epedersen on 2005-10-27
I don't want to badmouth the new version, as *most* ... OK ...  TWO of my four upgrades went fairly well.  Otherwise I've had problems with:

1) A DELL PowerEdge 1400 using a PERC 2/SC I2O controller (made by AMI) doesn't recognise the logical drives, so I've had to downgrade to Hoary.  Luckily it's only a testbed server at work, but still...

2) A IBM Thinkpad with a Linksys WPC11 V.3 wireless card can no longer connect to the network.  Haven't downgraded yet, but it's getting tempting.

:???:

---

### Post by Bastaard on 2005-10-28
I can't install Ubuntu Breezy because it doesn't support my SATA controller (nor does it detect my onboard ethernet adapter, even though I have the Asrock 939S56-M motherboard which is a quality one) and from what I've read I think this is Ubuntu's biggest downside: it lacks hardware support.

---

### Post by Xian on 2005-10-28
Please assist the devs by [reporting](http://bugzilla.ubuntu.com/) your bugs about any hardware issues.

---

### Post by Kyral on 2005-10-28
1) Checkout the boot options by tagging F3 at the boot screen. I know for a fact that most of the time you have to add an option to the bootline to enable Adaptec Raid. So if it doesn't work, take a look at the options in F3. This is almost universal across distros that I have seen.

2) See 1, but for Hotplug


To the guy with the Wireless card. I will admit that Wireless support is one of Linux's biggest drawbacks, espcially with Linksys. By anychance were you using NDiswrapper in Hoary?

---

### Post by epedersen on 2005-10-28
re: Wireless problems

No, when I installed Hoary my card was recognized right off the bat.  (Other than having to modify the /etc/network/interfaces file to add my WEP key...)

You're correct - I should be posting this in the other forum.

---

