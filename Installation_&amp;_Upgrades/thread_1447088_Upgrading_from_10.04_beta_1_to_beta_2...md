---
title: "Upgrading from 10.04 beta 1 to beta 2.."
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by simpleblue on 2010-04-04
So here's the schedule for 10.04:

April 8th, 2010 - Beta 2 release;
April 22nd, 2010 - Release Candidate;
April 29th, 2010 - Final release of Ubuntu 10.04 LTS.

My question is, If I have 10.04 beta 1, could I just continue to update and not have to burn another disk to install? Or do I have to burn the beta 2 and reinstall if I want it?

---

### Post by mikewhatever on 2010-04-04
You don't have to burn new isos or reinstall, at least not unless the existing installation is badly broken.

---

### Post by simpleblue on 2010-04-04
Great, thanx.

---

### Post by Baldrick_NZ on 2010-04-05
> **simpleblue said:**
> So here's the schedule for 10.04:

April 8th, 2010 - Beta 2 release;
April 22nd, 2010 - Release Candidate;
April 29th, 2010 - Final release of Ubuntu 10.04 LTS.

My question is, If I have 10.04 beta 1, could I just continue to update and not have to burn another disk to install? Or do I have to burn the beta 2 and reinstall if I want it?

It'll be really interesting to see what changes are made in Beta2 and the final LTS.
For me, I'll be happy if it stays just the way it is currently. What I'd like to see though is a few more 'options'. IE: Set the default of the buttons either left or right, but have the option to easily change if the user wishes. I like it on the left personally, because it reminds me less of windows. ;-)

---

### Post by sqr47 on 2010-04-08
How do you upgrade from beta 1 to beta 2? It's not showing up in the update manager... am I doing anything wrong?

---

### Post by Kaisersoze on 2010-04-08
> **sqr47 said:**
> How do you upgrade from beta 1 to beta 2? It's not showing up in the update manager... am I doing anything wrong?

I also do not have the option to update... weird...

---

### Post by sqr47 on 2010-04-08
> **Kaisersoze said:**
> I also do not have the option to update... weird...
it might be delayed, i know beta 1 was

---

### Post by ratcheer on 2010-04-08
You do not need to run a dist-upgrade from beta1 to beta2. If you are running beta1, just do an "sudo apt-get update", then a "sudo apt-get safe-upgrade" (I use aptitude, but use whichever one you usually use) and you will be at beta2. If nothing is found, you are already there.

Tim

---

### Post by sqr47 on 2010-04-08
> **ratcheer said:**
> You do not need to run a dist-upgrade from beta1 to beta2. If you are running beta1, just do an "sudo apt-get update", then a "sudo apt-get safe-upgrade" (I use aptitude, but use whichever one you usually use) and you will be at beta2. If nothing is found, you are already there.

Tim

im still not getting the option

---

### Post by ratcheer on 2010-04-08
> **sqr47 said:**
> im still not getting the option

I don't understand what you mean. There is no option to "upgrade" from beta1 to beta2. It is just a matter of installing all the updates. You can install the updates any time you want, no "option" is needed.

Tim

---

### Post by sqr47 on 2010-04-08
oh i thought there were actual updates to the operating system.

---

### Post by Slim Odds on 2010-04-08
From the version perspective Lucid is Lucid

Alpha X, Beta X, RC or Final release

Still all LUCID

I really don't understand why so many people are confused by this.

---

### Post by bshosey on 2010-04-08
Because with some Operating Systems that is not the case.

---

### Post by Slim Odds on 2010-04-08
> **bshosey said:**
> Because with some Operating Systems that is not the case.

Well.... with Ubuntu it is and always has been. 

And there are a million posts about it, like this recent sticky: [http://ubuntuforums.org/showthread.php?t=1450110](http://ubuntuforums.org/showthread.php?t=1450110)

Which includes information like this that no one reads:

[LIST]
[*] **If you install the Beta once it's released, you can upgrade to the final release without having to do a fresh install**. But there may be some drawbacks in certain scenarios; refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for details.
[*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their pre-decided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install Beta 2**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. Refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1343449") for further details.
[/LIST]

---

### Post by somethinginteresting on 2010-04-09
Is there a way to upgrade from a Beta 1 to Beta 2 by using the Beta 2 ISO. I know that's obviously not standard and you can use apt-get but with slow interent I figured it was worth asking.

---

### Post by ratcheer on 2010-04-09
> **somethinginteresting said:**
> Is there a way to upgrade from a Beta 1 to Beta 2 by using the Beta 2 ISO. I know that's obviously not standard and you can use apt-get but with slow interent I figured it was worth asking.

Yes, if you start the installer and tell it to use the same partitions and **not** to reformat them, it will replace the changed stuff. But, it really should be quicker and easier just to do the package manager update and safe-upgrade.

Tim

---

### Post by Slim Odds on 2010-04-09
> **ratcheer said:**
> Yes, if you start the installer and tell it to use the same partitions and **not** to reformat them, it will replace the changed stuff. But, it really should be quicker and easier just to do the package manager update and safe-upgrade.

Tim

No, the correct way is to use the alternate install CD.

---

### Post by Slim Odds on 2010-04-09
> **somethinginteresting said:**
> Is there a way to upgrade from a Beta 1 to Beta 2 by using the Beta 2 ISO. I know that's obviously not standard and you can use apt-get but with slow interent I figured it was worth asking.

Download the alternate install CD.

---

