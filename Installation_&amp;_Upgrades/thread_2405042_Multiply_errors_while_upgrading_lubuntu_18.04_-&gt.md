---
title: "Multiply errors while upgrading lubuntu 18.04 -&gt; 18.10"
date: 2018-10-31
forum: Installation &amp; Upgrades
---

### Post by when-updtae on 2018-10-31
Today lubuntu showed me prompt to upgrade 18.04 to 18.10. At first, "upgrade" button did nothing and as suggested I used "sudo apt-get upgrade" and it finally worked. Now the process of update is going, but lubuntu already failed to install 2 packages including "lubuntu-core" and asked to paste command to terminal to submit log to devs. When using this command lubuntu showed prompt about "it seems like you have modified contents of /etc/update-manager/release-updates". I have never ever modified any files, not ever settings, and my lubuntu is clean, the only thing I did is install steam.
So: 1) My upgrading process is still going despite inability to install "lubuntu-core". I suppose this package is essential so could it be that update can break my PC or not work as intended, and what should I do then?
2) Those bugs with upgrading, plus I am also getting error messages on ubuntu start and in terminal which don't interrupt process but still exist, and I've got more unexpected bugs which are not fatal but this certainly indicates that something is not right. I suppose something wrong with my lubuntu installation but how do I repair it? I have a lot of files in lubuntu I can't reinstall and also this installation is reinstall too because on previous ones once my wi-fi wasn't working and once it refused to install GPU drivers. I would rather keep with my working installation and try to fix as much as I can, if possible.
EDIT: yes, after installation I can't boot my lubuntu. It just flickers my screen on startup. What do I do?

---

### Post by Dennis N on 2018-10-31
The only lubuntu* packages that exist for 18.10 are these:

```
dmn@Sydney-VM:~$ apt list lubuntu*
Listing... Done
lubuntu-artwork/cosmic,now 1.8 all [installed,automatic]
lubuntu-default-settings/cosmic,now 1.17 all [installed,automatic]
lubuntu-desktop/cosmic,now 1.15 amd64 [installed]
lubuntu-restricted-addons/cosmic 26 amd64
lubuntu-restricted-extras/cosmic 67 all

```
so lubuntu-core isn't needed.

Lots of packages changed between 18.04 and 18.10, and in the release notes the Lubuntu team wrote: 
> The most major and notable problem is that upgrading Lubuntu from 18.04 to 18.10 causes a fair amount of issues. Therefore, we are not officially supporting this upgrade path at this time, however we have prepared a page in the Lubuntu Manual which can help address the problems that arise after the upgrade.
[Release Notes]("https://lubuntu.me/cosmic-released/")
and this is the page that's referred to in the above quote. It might help:
[Upgrading Problems]("https://manual.lubuntu.me/D/upgrading.html")

I hope it helps. Good luck.

---

### Post by Impavidus on 2018-10-31
> **when-updtae said:**
> When using this command lubuntu showed prompt about "it seems like you have modified contents of /etc/update-manager/release-updates". I have never ever modified any files, not ever settings, and my lubuntu is clean, the only thing I did is install steam.
The default contents of /etc/update-manager/release-upgrades contain the setting to only offer upgrades to LTS releases. As you attempt to upgrade to a regular release, it must have been altered.
> So: 1) My upgrading process is still going despite inability to install "lubuntu-core". I suppose this package is essential so could it be that update can break my PC or not work as intended, and what should I do then?
lubuntu-core doesn't exist on 18.10. That explains the error. On 18.04 it's a meta-package, that is, an empty package that only serves to pull in other packages. So it's not essential. It would have been neat is the upgrader had simply removed it, but as the upgrade on Lubuntu isn't officially supported, we can't expect that to happen. It would have been conceivable if the upgrade hadn't been offered at all, but then people had been asking questions on why they couldn't upgrade and people would have tried to force the upgrade anyway. There's no ideal solution to this.
> I have a lot of files in lubuntu I can't reinstall and also this installation is reinstall too because on previous ones once my wi-fi wasn't working and once it refused to install GPU drivers. I would rather keep with my working installation and try to fix as much as I can, if possible.
EDIT: yes, after installation I can't boot my lubuntu. It just flickers my screen on startup. What do I do?
You should never get in the situation that you can't simply do a fresh install. Always have backups. Broken release upgrades are very hard to fix, in particular if they're not officially supported. Can you boot your system using a live disk? That should allow you at least to make backups of all important documents. Then either fresh install or fix it. The former is the easy way.

---

### Post by when-updtae on 2018-11-01
Well when system showed me updtae prompt I thought it is just another security updtae bc 18.04->18.10 does not seem major. Only after process began I red about what it actually is. I suggest adding at least warning for those who get that updtae prompt.
Everyone was like "linux advantage is that it is so stable you dont ever need backups or antivirus or etc." and I didn't bother doing backups. That my fault.
 18.10 works well with wifi and gpu so far but eats 800mb RAM for some reason

---

### Post by oldos2er on 2018-11-01
> Everyone was like "linux advantage is that it is so stable you dont ever need backups Backups are never NOT needed, and I can't imagine "everyone" would tell you something like this. All software has bugs, and all hardware fails eventually, so ALWAYS backup, no matter which OS you're running.

Upgrading from one version to the next should always be considered "major" in my opinion.

---

