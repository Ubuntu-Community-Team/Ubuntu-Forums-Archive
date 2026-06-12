---
title: "Upgrade to 18.04.1 still not available"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by martago on 2018-07-27
I posted a similar message two months ago, I got a reply that the upgrade from previous LTS release (16.04 to 18.04) using the command "sudo do-release-upgrade" would only be available after the release of version 18.04.1 which happened yesterday.  Anyone has any information regarding the availability of the upgrade of previous LTS release to the current one?  Thank you.

---

### Post by PaulW2U on 2018-07-27
The [Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") for Ubuntu 18.04 say:
> Upgrading from Ubuntu 16.04 LTS

Upgrades from 16.04 LTS will not be enabled until a few days after 18.04.1's release expected in late July.
I'm sure that next week you will get a notification to say that an upgrade to Ubuntu 18.04 is now available.

---

### Post by missmoondog on 2018-07-27
next week? next release came out today here.

i can understand a day or 2 before getting it, but next week? wow!!

---

### Post by martago on 2018-08-03
The working week arrived at the end, no new release available using do-release-upgrade.  Just reminding your words "I'm sure that next week you will get a notification to say that an upgrade to Ubuntu 18.04 is now available".

I could comment on this delay as well as recent problems with a recent kernel upgrade, something less positive is happening with the ubuntu team.  Let's hope it is a temporary situation.

---

### Post by kansasnoob on 2018-08-03
I assure you that nothing nefarious is underway - the sky is not falling :)

18.04.1 was released July 26th:

[https://lists.ubuntu.com/archives/ubuntu-release/2018-July/004533.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-July/004533.html)

16.04.5 was released yesterday August 2nd:

[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004542.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004542.html)

Now testing must be performed to ensure that upgrades to Bionic work from both Xenial with the GA kernel and also Xenial with the Bionic HWE stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Believe it or not some of us actually do test things :)

And no, even in spite of testing there is no 100% guarantee that upgrades will work for everyone, but we do try.

---

### Post by PaulW2U on 2018-08-03
> **martago said:**
> Just reminding your words 
I'm sorry if the words that I used misled you into thinking that I was speaking in some official capacity or that I had some inside information. I was merely stating an opinion based on what I thought would happen at the time that I posted. :redface:

---

### Post by martago on 2018-08-06
I do understand your concerns and I am aware of what is happening, like the release of 16.04.5 a couple of days ago.  I have been using ubuntu/xubuntu LTS releases for 10 years at least and I don't recall in previous releases this time delay from the original LTS release (like 26th April 2018) and the availability of upgrades from the previous LTS release (via do-upgrade-release).  Nor did it happen ever before that in a regular kernel update recently of a LTS release, that I got a black screen at startup, forcing me to reinstall xubuntu from scratch.  I thought LTS versions were supposed to be stable and not a result of untested updates.  So maybe it was bad luck, but recently I am getting the impression that the Ubuntu team is not doing ok, maybe less people working, less investment in ubuntu from Canonical Software, it seems like something is happening.

---

### Post by freesitebuilder on 2018-08-06
This thread may help - it started my upgrade - [https://ubuntuforums.org/showthread.php?t=2397927](https://ubuntuforums.org/showthread.php?t=2397927)

---

### Post by hans12345 on 2018-08-07
> **freesitebuilder said:**
> This thread may help - it started my upgrade - [https://ubuntuforums.org/showthread.php?t=2397927](https://ubuntuforums.org/showthread.php?t=2397927)

Thanks, it worked for me too.

:)

---

### Post by kansasnoob on 2018-08-09
There actually is a reason:

[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html)

I hope those choosing to change release notifications to "any new release" remember to change it back to LTS only after the upgrade so they don't end up on 18.10 unintentionally in a couple of months :eek:

---

### Post by David_Wright on 2018-08-09
> **kansasnoob said:**
> There actually is a reason:

[https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-August/004556.html)


Thanks for sharing this. I had assumed that there was some issue being resolved but it is nice to know what it is (and it will help me to wait more patiently).

---

