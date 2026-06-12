---
title: "Broken Python and package management, dist upgrade 20.04 to 22.04"
date: 2023-07-17
forum: Installation &amp; Upgrades
---

### Post by mryumyum on 2023-07-17
Hi, I recently updated my Ubuntu 20.04 desktop to 22.04 using the "do-release-upgrade" via the terminal. The terminal was local (not ssh), but I walked away from the machine and came back to a login screen that was constantly denying my login (without me touching the keyboard!).

So I ssh'd in and rebooted the machine and I was pretty certain it said no new updates and on 22.04 (but now it says there are many updates available and it's on 20.04... so something probably changed while I was messing with it before posting here.)

In any case, python/pip seem to be broken. Python is 3.10.6 but doesn't have xml, shutil, or json packages or other things (it throws Tracebacks saying as much when trying to use apt to fix things). When trying to use pip to install these packages, it breaks with the same errors.

I've done all sorts of apt/dpkg fix commands and they all break with these same python errors or other issues. Upgrade logs (+ dpkg log) attached.

Is there any possibility to get this fixed and upgraded to 22.04 without doing a full install on top of the old system?

Any help would be greatly appreciated. Thank you!

---

### Post by Impavidus on 2023-07-20
> **mryumyum said:**
> 
Is there any possibility to get this fixed and upgraded to 22.04 without doing a full install on top of the old system?

Any possibility? Yes. Will that be efficient use of your time? No. When a release upgrade goes wrong, just do a clean install.

---

### Post by guiverc on 2023-07-20
My backup strategy (*on release-upgrade failure, or if I don't have time too*), is just to do an *unclean* install.

ie. install the new release; re-using your existing partitions **without format** which triggers the *repair type installation* or *non-destructive* re-install. 

I write about it [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743"), though please do note that was written for QA testers & not end-users, plus the QA testing of it **only** includes Ubuntu repository software (ie. no 3rd party).

I'm waiting for *kinetic* or 22.10 EOL to be posted (*and then I'll post the notice to the fridge*) which will also mean I have no need for keeping *kinetic* or 22.10 *support* installs any longer, and as I already have 23.04 I have no desire to *release-upgrade* them to 23.04, instead I'll re-install using a *mantic *(23.10) system & subsequently re-install them weekly (*QA purposes*) to ensure none of my files are erased during that install process, plus the additional (or *manually installed*) packages I have (*esp. my non-standard music player* *I talk about in the testcase doc*) gets auto-reinstalled etc.

By default all *flavors* (*which includes Lubuntu which the link I provided to applies*) have 'universe' enabled by default; where as main Ubuntu Desktop does not, thus I manually enable 'universe' & `sudo apt update` before I start the installer. This hasn't been needed for all re-installs (*cycle specific*), but I have noted it being required for a couple of *cycles* (*though that could have been during the pre-release stage; I forget sorry*) and can't recall if 22.04/*jammy* required it or coped where you had it *enabled* on your prior install, but even if you get this wrong; the only consequence is you don't get 'universe' packages & have to re-add them yourself.

Backup as always first, but I'd just do an *unclean* install which is only a no-format install meaning your data survives (for desktop apps anyway; not server apps/configs).

Sorry I'm tired, and have no desire to look at .zip/logs.

---

### Post by mryumyum on 2023-07-21
Roger that, thanks for the resources. I'll do a backup and try an unclean install and see if that works. If not, I'll do a clean install.

Thank you.

---

