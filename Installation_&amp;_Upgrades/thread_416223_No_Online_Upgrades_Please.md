---
title: "No Online Upgrades Please"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by harshad on 2007-04-20
[SIZE="4"]I upgrade from Edgy to Feisty using the alternate CD. However Ubuntu still wants to upgrade and install 10s of software and download 100s of MBs from the net, to complete the upgrade.

On slow and unreliable internet connections in most of the developing world. Not only does this lead to a very long wait but there's always the risk of the power failing or internet dying while the upgrade is in progress,  and completely messing up one's machine.

Isn't there a way in which all the upgrade steps can be completed through CDs and offline?

Maybe a second alternate CD which has the upgrades?

Online upgrades might be fine in the US or Europe where power doesn't fail and Internet speeds are in MBs but for the rest of the world I am sure online upgrades are a big problem,

Kindly consider. Thanks
[/SIZE]

---

### Post by jgcamp99 on 2007-04-21
I agree the standard desktop or server version cdrom should simply have an option to upgrade as well. I did that when I went from 6.06 to 6.10, but it went seriously wrong. I thought after having to do a clean install of 6.10, that Windows was light years ahead in that regard. I didn't even try it with 6.10 to 7.04 with the new desktop cdrom. I'm afraid to from last October/November's experience.

I must say though, I couldn't resist temptation 7.04 is updating from 6.10 on a Dell L400 notebook using update manager. I have what they call DSLLite, this is taking over 7 hours to get accomplished and even with stable power and broadband, I would've rather have done it via cdrom. That'll be my test, before I try on my main system.

---

### Post by lingnoi on 2007-04-21
> **harshad said:**
> Online upgrades might be fine in the US or Europe where power doesn't fail and Internet speeds are in MBs but for the rest of the world I am sure online upgrades are a big problem,

I am in Thailand where the power is not great too. Get yourself a UPS if you are worried about power failures. 

I am [trying to figure out how to change the update manager to download from the Thai mirror servers]("http://ubuntuforums.org/showthread.php?t=414899"). The international bandwidth is not great here and if someone could tell me how to download locally it would be super fast compared to trying to grab the files from somewhere outside.

---

### Post by jgcamp99 on 2007-04-21
> **lingnoi said:**
> I am in Thailand where the power is not great too. Get yourself a UPS if you are worried about power failures. 

I am [trying to figure out how to change the update manager to download from the Thai mirror servers]("http://ubuntuforums.org/showthread.php?t=414899"). The international bandwidth is not great here and if someone could tell me how to download locally it would be super fast compared to trying to grab the files from somewhere outside.

Apply all updates in edgy, one of them should be update-manager that gets you to this version:

[https://wiki.ubuntu.com/EdgyUpdatesEnabled](https://wiki.ubuntu.com/EdgyUpdatesEnabled)

Or you can do the Synaptic Package manager and search for "update-manager"

That actually will allow you to bump it to 045.3, and as a safeguard, I also made sure that update-manager-core was installed as well. This worked last night for my Dell L400 notebook.

I am now 7.04 Feisty on it. Understand though that the notebook was a minimalist approach to Ubuntu 6.10 when that was on it. That is how it PXE'ed network installed is pretty much what was updated to 7.04. What few applications, it broke "Google Earth", it tried to get rid of a few other programs too. I kept them and they don't work, but will reinstall them under 7.04. Oh, and it tried to get rid of the wireless items that supported my Ath0 Proxim Orinoco A/B/G gold, I kept those without cleaning it up. Those are unsupported as they were restricted modules, which is why I kept them, the message upon reboot reinformed me of that fact and I was happy I didn't remove them during the final stages of updating as my wireless still works.

My main system/desktop, that'll be a clean install, if I elect to do it at all. It has more customizations (fglrx for instance), that I have a feeling will be broken beyond my means to fix. I found with 6.06 to 6.10, it was less time intensive to simply clean install, spend the time to get the drivers & applications I wanted back on that clean intall to work and then migrate data to the clean install.

---

