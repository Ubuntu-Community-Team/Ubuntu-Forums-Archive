---
title: "tetex problem upgrading to edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by barmaley on 2006-10-27
Hello,ubuntu users

I have upgraded from dapper to eft and it went not that smoothly. The main problem was in the tetex. The upgrade was almost completed but then there was an error with dependencies to upgrade the tetex and its utilities. So now I don't have tetex installed on my comp, which I need vitally. I tried to install it after the restart, but also failed.
If someone kows how to solve the problem and install tetex in eft, please help.
Thank you in advance.

---

### Post by KedDeK on 2006-10-27
Get **texlive**, it is even better than tetex. It's in the repos ;)

---

### Post by barmaley on 2006-10-29
Thanks for the reply.

I have another pc with dapper and I also would like to upgrade it to Eft. The  question is what should I do to avoid those problems with tetex? Since the upgrade did not finish as it should have, the last 2 steps clean up and restart were not accomplished, I want to understand what to do before I upgrade.

Another question is why do you think texlive is better than tetex? Is there a comparison between them in some place?

Thank you in advance

---

### Post by hajk on 2006-10-29
> **KedDeK said:**
> Get **texlive**, it is even better than tetex. It's in the repos ;)

Even better: download the TeXLive CD from TUG and install it yourself to the default /usr/local/texlive tree. (The Debian packages in the repositories have messed with the directory structure of TeXLive, not a good thing IMHO.)

---

### Post by hajk on 2006-10-29
> **barmaley said:**
> 

Another question is why do you think texlive is better than tetex? Is there a comparison between them in some place?



Thomas Esser does no longer maintain teTeX, so it is getting left behind in the world of TeX distributions. At the same time, the TeXLive distribution from the TeX User Group (TUG) seems to be poised to become the leading ditsribution for all platforms. The current version is TeXLive 2005. Other than the name suggests, the TeXLive2005 *CD* cannot be used as a liveCD, but only as an install CD; there are also versions on the TUG website that can be used as a liveCD (or DVD).

---

### Post by barmaley on 2006-10-29
I have tried texlive from the repositories and it did not work. Now I know why, thank you. I will try the texlive cd, as explained somewhere in the ubuntu forum.
Should I uninstall all the tex before upgrade to eft?
Thank you for yoour help.

---

### Post by hajk on 2006-10-29
> **barmaley said:**
> 
Should I uninstall all the tex before upgrade to eft?
Thank you for yoour help.

That would be a good idea, even though TeXLive is best installed in its own tree in /usr/local/texlive (the default). If you don't remove the old TeX, there is a chance that parts of the old and the new versions start to interfere with each other.

The TeXLive2005 CD should be downloaded and burned to CD (it is an iso, so just click on it and select Write to CD). Once mounted, move to the toplevel directory on the CD and give the command "sudo bash install-tl.sh" (this is a little different from what the README says), then you'll be presented with a lot of options: you should at the minimum deselect all the language documentation and packs that you don't need. Leave the directories at the defaults offered, and also select Symlinks in the usual directories (just in case there are still some old symlinks left in /usr/bin).

Once the options are set, you can sit back and let the TeXLive installer do the job. You can start using it right after it's finished.

Let me know if you want to install any proprietary fonts, like LucidaBright -- installing those is not difficult, but you have to watch out for some traps.

Have fun!

---

