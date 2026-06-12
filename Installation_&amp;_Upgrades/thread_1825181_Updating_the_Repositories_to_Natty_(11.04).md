---
title: "Updating the Repositories to Natty (11.04)"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by fester225 on 2011-08-14
After my system was updated to Natty, even though Software Sources is set for LTS updates only, none of the repositories in Software Sources or /etc/apt/sources.list.d were updated.

I have manually updated the Software Sources repositories, and removed the outdated repositories from /etc/apt/sources.list.d, but when I do apt-get update I still see references to previous Ubuntu versions.

How do I update ALL the repositories?

---

### Post by Hakunka-Matata on 2011-08-14
According to this list, Natty is not an LTS version.  I'm not sure I understood your post correctly, but might?, this fact make a difference?

---

### Post by garvinrick4 on 2011-08-14
What does this say.
```
lsb_release -a
```

---

### Post by fester225 on 2011-08-15
> **garvinrick4 said:**
> What does this say.
```
lsb_release -a
```

For reasons I don't understand, lsb_release -a says I'm running Maverick while "System/About Ubuntu" says I'm running Natty.

---

### Post by dino99 on 2011-08-15
as i know Natty is not LTS, so what do you expect ? clear your mind ;)

---

### Post by TBABill on 2011-08-15
> **fester225 said:**
> After my system was updated to Natty, How did your system upgrade to Natty if your software sources are set to inform you of new LTS releases only? > even though Software Sources is set for LTS updates only, none of the repositories in Software Sources or /etc/apt/sources.list.d were updated.This setting does not change your repositories. All it does is change when the system informs you new versions of Ubuntu are available. If you have it set to LTS versions only, you will only be informed every 2 years when the new LTS releases that a new version is available. In either setting, no repositories will be updated. Only during the upgrade process to the next version will your repositories be updated to reflect the new distro. That's part of the upgrade process itself. > I have manually updated the Software Sources repositories, and removed the outdated repositories from /etc/apt/sources.list.d, but when I do apt-get update I still see references to previous Ubuntu versions. How do I update ALL the repositories?Not knowing how you upgraded (or even if you upgraded), we'll need more information before being able to assist. I'm guessing you had a single or more repos showing Natty, did an apt-get update/upgrade and then ended with a mix of both, but not a full distro upgrade.

---

### Post by fester225 on 2011-08-15
> **dino99 said:**
> as i know Natty is not LTS, so what do you expect ? clear your mind ;)


As "System/About Ubuntu" said I was running Natty, I rather expected I was running Natty.

---

### Post by fester225 on 2011-08-15
> **TBABill said:**
> How did your system upgrade to Natty if your software sources are set to inform you of new LTS releases only? 

That's a good question.



[/QUOTE]This setting does not change your repositories. All it does is change when the system informs you new versions of Ubuntu are available. If you have it set to LTS versions only, you will only be informed every 2 years when the new LTS releases that a new version is available. In either setting, no repositories will be updated. Only during the upgrade process to the next version will your repositories be updated to reflect the new distro. That's part of the upgrade process itself. Not knowing how you upgraded (or even if you upgraded), we'll need more information before being able to assist. I'm guessing you had a single or more repos showing Natty, did an apt-get update/upgrade and then ended with a mix of both, but not a full distro upgrade.[/QUOTE]


Would you suggest manually changing all my Software Sources repos back to Maverick? Maybe it would be more to the point to upgrade to Natty and wait for the next LTS, and hope this doesn't happen again?

It seems that "About Ubuntu" and lsb-release should be getting their information from the same place to avoid such problems.

---

### Post by TBABill on 2011-08-15
To be honest I don't have a recommendation. Changing the repos back to Maverick may be safest, but that's assuming nothing critical was upgraded that may bork down the road by the changes. You should be able to look at which kernel you are running to know for sure which version you are actually using. Maverick uses 2.6.35 and Natty is 2.6.38(9?). Unless you upgraded the kernel in Maverick to a newer one manually, you should still see 2.6.35 if you are still on Maverick. 
 
Without knowing the state of your machine I can't really say what change would be best. Safest may be to backup your data and reinstall the preferred distro, but that may be unnecessary if you didn't really upgrade as your machine may be leading you to believe.

---

### Post by Hakunka-Matata on 2011-08-15
2.6.38-10  is natty
2.6.38-8  is maverick

                                                      >  Quote:
                                                                      Originally Posted by **garvinrick4**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11152763#post11152763")                 
                 [I]What does this say.
     Code:
     lsb_release -a 
[/I]
                                 
For reasons I don't understand, lsb_release -a says I'm running Maverick while "System/About Ubuntu" says I'm running Natty.

Can you post the results from boot_info_script please.  Those results may reveal something strange?  A guess.

---

