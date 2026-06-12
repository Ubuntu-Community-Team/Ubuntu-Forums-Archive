---
title: "Upgrading Wubi to 10.10 Safe?"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by acconrad on 2010-10-13
I checked the release notes and there seems to still be some serious errors when upgrading Wubi Ubuntu to 10.10. Is it recommended to wait before upgrading?

---

### Post by JGUbun on 2010-10-13
You might want to hold off.

I tried doing the Upgrade last night but after the restart I could no longer boot into Ubuntu.

It acts as if it can't find the disk files but the root.disk and swap.disk files are there.  Not sure what the problem is.

Anyway, might be better to wait till some of the bugs are worked out.

Joe

---

### Post by Frogs Hair on 2010-10-13
Wubi upgrades are known to be messy , best to backup what you want transfer to disc and do fresh Wubi install of 10.10.

---

### Post by bcbc on 2010-10-14
It's not safe. But if you've done it there is a workaround to get it booting. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by JGUbun on 2010-10-26
Hey, thanks for the tip bcbc.  Restoring the wubildr file fixed everything.

Joe

---

### Post by tommcd on 2010-10-27
> **acconrad said:**
> I checked the release notes and there seems to still be some serious errors when upgrading Wubi Ubuntu to 10.10. Is it recommended to wait before upgrading?
Wubi was never designed or intended to be used to do upgrades. It is only meant to be used as a way to try out Ubuntu. 
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle. 
So if you have been using Ubuntu long enough to worry about upgrading to a newer version, then it is time to do a real Ubuntu install to a dedicated linux partition on your hard drive.

---

### Post by bcbc on 2010-10-27
> **JGUbun said:**
> Hey, thanks for the tip bcbc.  Restoring the wubildr file fixed everything.

Joe

Great! Glad it worked out. :)

> **tommcd said:**
> Wubi was never designed or intended to be used to do upgrades. It is only meant to be used as a way to try out Ubuntu. 
...
Why do they include wubi upgrades in release testing? ([http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)) 

If they are not intended then it would be simpler just to state that in the release notes.

---

### Post by Mark Phelps on 2010-10-27
> **bcbc said:**
> If they are not intended then it would be simpler just to state that in the release notes.

My guess would be, that if the frequency of postings here that are related to 10.10 upgrade problems is any indication, NO ONE actually READS the Release Notes!!

OK, so a handful of us actually DO read them, but the great mass of the community obviously does not. 

If they DID, they would have read the section on Issues and seen the text mentioning that upgrading Wubi fails.

---

### Post by bcbc on 2010-10-27
> **Mark Phelps said:**
> My guess would be, that if the frequency of postings here that are related to 10.10 upgrade problems is any indication, NO ONE actually READS the Release Notes!!

OK, so a handful of us actually DO read them, but the great mass of the community obviously does not. 

If they DID, they would have read the section on Issues and seen the text mentioning that upgrading Wubi fails.

Very true :P

(The impression may be a bit skewed, since mainly users with problems post on the forum.) But it would definitely help if reviewing the release notes was the first step in the upgrade process.

---

### Post by JGUbun on 2010-10-27
In my defense, here's all I could find about wubi in the release notes:


[LIST]
[*]**The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases.**  Investigation of the problems are ongoing ([613288]("https://bugs.launchpad.net/bugs/613288")) 
[*]**You cannot upgrade if wubi is installed to a partition other than Windows.** ([610898]("https://bugs.launchpad.net/bugs/610898"),[653134]("https://bugs.launchpad.net/bugs/653134")) 
[/LIST]
When I read the first bug note, it seemed to apply to a fresh install of Wubi.  The second doesn't seem to apply because I have wubi installed on my Windows partition so I didn't read the bug notes.

Now that I know about bcbc's fix I'm happy I risked the upgrade.  The fix was trivial and upgrading was easier than starting over from scratch.

---

### Post by bcbc on 2010-10-27
> **JGUbun said:**
> In my defense, here's all I could find about wubi in the release notes:


[LIST]
[*]**The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases.**  Investigation of the problems are ongoing ([613288]("https://bugs.launchpad.net/bugs/613288")) 
[*]**You cannot upgrade if wubi is installed to a partition other than Windows.** ([610898]("https://bugs.launchpad.net/bugs/610898"),[653134]("https://bugs.launchpad.net/bugs/653134")) 
[/LIST]
When I read the first bug note, it seemed to apply to a fresh install of Wubi.  The second doesn't seem to apply because I have wubi installed on my Windows partition so I didn't read the bug notes.

Now that I know about bcbc's fix I'm happy I risked the upgrade.  The fix was trivial and upgrading was easier than starting over from scratch.

You're right, the release notes have a bug too since bug 653134 should only apply to installs that are on the same partition as windows.

---

