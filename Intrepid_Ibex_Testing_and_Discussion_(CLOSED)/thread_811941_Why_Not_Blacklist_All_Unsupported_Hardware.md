---
title: "Why Not Blacklist All Unsupported Hardware?"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2008-05-29
The release of 8.04 saw many graphics cards blacklisted* from using Compiz because of unfixed bugs in the drivers. Many other cards were blacklisted, too, because they were similar to the broken ones. Why stop there?

Many laptops are unable to suspend or hibernate correctly, and [will never be fixed](https://bugs.launchpad.net/ubuntu/+bug/34155). If a user is working on an important project, walks away from his or her machine for a minute, and comes back only to find the machine is hopelessly locked up, all the data is lost. Why not blacklist those machines from ever suspending in the first place?

Heck, why not have a check in the installer? "Sorry, nobody has reverse-engineered your machine's drivers yet, and Ubuntu will run horribly on your machine. The installation could not be completed."

Warning! This post may contain sarcasm.

(* Yes, I know that it's actually a whitelist of supported cards. The effect is the same.)

---

### Post by ajackson on 2008-05-29
Anybody happen to have a list of all available hardware? Don't forget to add hardware that was available say 5 years ago but isn't now. See the problem?

Whitelisting is different because it is hardware known to work, for some hardware it just hasn't been tested, who knows the first time it is tested it might work with no problem, so it can be added to the whitelist.

When new hardware comes out if the blacklist existed someone would have to add it to the list, with a whitelist it gets added if it works when tested. See which one is easier to implement?

---

### Post by ronacc on 2008-05-29
actualy something like your tounge in cheek suggestion wouldn,t be all that bad an idea . Atleast a list of hardware that is known to not play nice with Ubuntu might save us some embarassment . When someone installs Ubuntu and it runs like crap on their hardware or worse yet nukes their data  it does not give a good impression , and it matters not that it isn't Ubuntu's fault .

---

### Post by talkingwires on 2008-05-29
> **ajackson said:**
> Anybody happen to have a list of all available hardware? Don't forget to add hardware that was available say 5 years ago but isn't now. See the problem?Yup.> **talkingwires said:**
> Warning! This post may contain sarcasm.

---

### Post by 23meg on 2008-05-29
AFAIK this is already done in the kernel and HAL for machines with known suspend/hibernate problems. You won't see suspend / hibernate options in the GNOME "Quit" dialog by default when running them (you can manually enable them in gconf though).

---

