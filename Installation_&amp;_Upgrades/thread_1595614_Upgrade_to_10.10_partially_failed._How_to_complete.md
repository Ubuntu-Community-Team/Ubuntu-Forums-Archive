---
title: "Upgrade to 10.10 partially failed. How to complete?"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by smooth_dudes on 2010-10-13
Hi

I just tried to upgrade from 10.04 to 10.10, but since update-manager did not show the upgrade button (for some reason it did not know that there was a new release?), I tried upgrading using sudo do-release-upgrade.
This only worked partially though, and now when I run lsb_release -a it says that I am running maverick, but when I try to run update-manager, it says that the upgrade was only completed partially, and it suggests that I try to finish the upgrade, but it then gets the following error:
"An upgrade from "maverick" to "lucid" is not supported with this tool"

When I look at the terminal, the error looks like this:
ERROR:root:Bad upgrade: 'maverick' != 'karmic'

Is there any way to complete the upgrade?

---

### Post by mori64 on 2010-11-30
i have exactly this problem :cry:  .

no one have  any idea to solve  this problem!

---

### Post by mori64 on 2010-12-04
I'm waiting yet for your help .

---

### Post by Lyos on 2011-01-13
Still nothing from anyone?  I'm having the same problem and I started with upgrading through the Update Manager.

---

### Post by Quackers on 2011-01-13
Did you try to upgrade from Karmic to Maverick in one go?

---

### Post by Lyos on 2011-01-13
Well first off what's wrong with an upgrade from Lucid to Maverick in one go?

Second, how do I revert to Karmic from Lucid to even attempt a Karmic to Maverick?

---

### Post by Quackers on 2011-01-13
Nothing! I said from Karmic to Maverick.
If you have had problems upgrading from Lucid to Maverick it would be better to start your own thread giving details of what has happened, rather than resurrecting a 5 week old thread, which may have had a different cause to your own problems.

---

### Post by Lyos on 2011-01-14
> **smooth_dudes said:**
> 
 I just tried to upgrade from 10.04 to 10.10
 
 This is the same attempt, Lucid to Maverick.  He did upgrade via  terminal which is slightly different, because he was having trouble  getting Update Manager to notify of upgrade, but our end problem became  the same:
 
 > **smooth_dudes said:**
> 
 when I try to run update-manager, it says that the upgrade was only  completed partially, and it suggests that I try to finish the upgrade,  but it then gets the following error:
 ```
An upgrade from "maverick" to "lucid" is not supported with this tool"
``` When I look at the terminal, the error looks like this:
 ```
ERROR:root:Bad upgrade: 'maverick' != 'karmic'
``` Is there any way to complete the upgrade?

I receive the same error when attempting to use Update Manager, it says I'm running Maverick when i run ```
lsb_release -a
``` even though About Ubuntu still says I'm in Lucid and I'm fairly certain no upgrade was made, and no resolution was made for this thread.  I was simply trying to find a thread that seemed to address the same problem to avoid reposting the same problem and provide some resolution to this one.

The error doesn't even make sense because we aren't going from "maverick" to "lucid"; we were going from "lucid" to "maverick".  The terminal error is even more confounding because "karmic" gets introduced when it wasn't involved in the first place.  It looks like  to my untrained eye Update Manager was confused in the partial upgrade and is now thinking the upgrade is from "karmic" to "lucid".  It also thinks its running "maverick" so it complains when "maverick" doesn't equal "karmic".  There's probably more to it than that and that's what we need help on.  That and how to fix what screwed up.

Any ideas?

---

