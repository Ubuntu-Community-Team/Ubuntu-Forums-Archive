---
title: "Can i upgrade to latest version of Ubuntu using Wubi"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by karlb1483 on 2011-10-18
Sorry if i have been looking in the wrong places and this question has been already been answered, i just cant find it.

What i would like to know is, can i just upgrade to from 11.04 to 11.10 through software update in WUBI, as i am not allowed to instal a proper version on my work laptop, or do i need to remove and reinstall latest version.

cheers

Edforce 1

---

### Post by jimbo99 on 2011-10-18
> **karlb1483 said:**
> Sorry if i have been looking in the wrong places and this question has been already been answered, i just cant find it.

What i would like to know is, can i just upgrade to from 11.04 to 11.10 through software update in WUBI, as i am not allowed to instal a proper version on my work laptop, or do i need to remove and reinstall latest version.

cheers

Edforce 1

WUBI is just the installer which installs Ubuntu in a virtual file system (not to be confused with a virtual machine).  Once you have Ubuntu installed you can just use the normal method to upgrade it, the same method everyone else would.

But...I have a disclaimer...Ubuntu 11.10 has proven, to me and many others, to be a nightmare.  You might be best advised to hold off for now until Canonical gets its act together and resolves the overabundance of issues wreaking havoc on the user base.

Also, when doing an upgrade to something using a virtual file system, such as wubi, you need to first boot into windows and then exit normally.  The next thing is that you need to back up your data because if the install fails you will have great difficulty figuring out how to get access to the contents of those virtual files.  So, it is best to back up first.  Don't think I'm just saying that you should back up.  Back up any necessary files you have in the virtual files before you perform the upgrade.  Please heed that advice.  After that, if the upgrade fails you can just uninstall WUBI from within Windows and start over.

---

### Post by karlb1483 on 2011-10-18
Thank you so much. I am in no rush to upgrade just wondered how it was done. I have noted all the problems.

Thank you

---

### Post by Mark Phelps on 2011-10-18
Can't speak specifically to upgrading Wubi to 11.10, but I do know that in previous version, attempting a version upgrade was a sure-fire way to trash the Ubuntu install.

Wubi is really intended to be a short-term trial of Ubuntu, so it's not unusual that it does not handle version upgrades well.

Also, as already mentioned, 11.10 is yielding LOTS of posts with upgrade problems being a leading topic.

If you're going to be using Ubuntu for the long term, long enough to need to upgrade every six months, you would be better off using a separate partition.  Even then, clean installs are recommended instead of in-place upgrades, one major reason being that, unlike with MS Windows, there is no way to roll-back to a previous OS version.

---

