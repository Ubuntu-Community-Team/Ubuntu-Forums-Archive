---
title: "Upgrade to Hoary?"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by silentstriker on 2005-03-28
I am using Warty, and I want to upgrade to Hoary.  Is there a simple way to do that besides reinstalling the system?

---

### Post by bored2k on 2005-03-28
[QUOTE=silentstriker]I am using Warty, and I want to upgrade to Hoary.  Is there a simple way to do that besides reinstalling the system?[/QUOTE]
 [Q: How to upgrade from Warty Warthog to Hoary Hedgehog (Beta)?](http://ubuntuguide.org/#upgradewartytohoary)

have fun ;)

---

### Post by silentstriker on 2005-03-28
Thank you.  That worked perfectly.

---

### Post by Psquared on 2005-03-29
[QUOTE=silentstriker]Thank you.  That worked perfectly.[/QUOTE]

I see you did this yesterday. How is the upgrade working for you? Any problems? I am thinking of doing this, but I don't want to screwup my box or lose any data.

---

### Post by Psquared on 2005-03-29
My own reply:

I tried these instructions and the download took about 1 hr, 47 minutes. At the end it ran some sort of check and gave an error message and then flashed a message about a sound problem and opened another terminal window. I tried to follow the instrutions (something about EMU ....conf) but nothing happened and the upgrade would not continue.

I closed the terminal window and restarted the machine and I still have Warty.

What did I do wrong?

---

### Post by silentstriker on 2005-03-29
I had no problems.  dist-upgrade downloaded it, and installed it.  I answered a few questions, and then rebooted.  Voila.  It saved all my settings and programs and so far I have had no problems.

In fact it fixed a problem with my laptop where the CPU would spike to 100% for no reason.  That was the reason I upgraded, and it worked.

---

### Post by Domecq on 2005-03-29
Since this new version 5.04 is currently "development", I would like to know if when it becomes "stable" we need to do another upgrade, like from "development" to "stable" or would it be enough if we simply change the apt sources from "development" (or "test") to "stable" and run some updates?

---

### Post by Psquared on 2005-03-29
[QUOTE=silentstriker]I had no problems.  dist-upgrade downloaded it, and installed it.  I answered a few questions, and then rebooted.  Voila.  It saved all my settings and programs and so far I have had no problems.

In fact it fixed a problem with my laptop where the CPU would spike to 100% for no reason.  That was the reason I upgraded, and it worked.[/QUOTE]

That is encouraging, but it didn't work for me. I've tried twice now and at the end, when it says it is checking the changelog it lists a file ..... data.tgz that it does not recognize and then says it will ignore it.

The install then continues with some text (the rest of the message from the upgrade is gone from the buffer) about fixing sound problems and a couple of others and then it gets to the end of the text and it just says "end" with no "OK" or "y" choice or anything.

I am just guessing but either I have something from backport it does not like or I am doing something wrong in the process.

---

### Post by jamaas on 2005-03-31
Hi Guys,

Thanks for this, great help.

It all worked great for me until I rebooted, did some new things and then tried to compile a new module for something and gave me a big long error.  Its a good description but as a newbie I still can't fix it.

It says

no prebuilt module
kernel version 2.6.10-mh-4
in /usr/src/linux/include/linux/version.h

and then goes on to mention something about needing the correct source code or something.  Is there an easy way to fix this?

Thanks a bunch, this is a great distro.

Jim



[QUOTE=bored2k][Q: How to upgrade from Warty Warthog to Hoary Hedgehog (Beta)?](http://ubuntuguide.org/#upgradewartytohoary)

have fun ;)[/QUOTE]

---

### Post by bored2k on 2005-03-31
You would have to look in synaptic for the kernel source apparently .

---

