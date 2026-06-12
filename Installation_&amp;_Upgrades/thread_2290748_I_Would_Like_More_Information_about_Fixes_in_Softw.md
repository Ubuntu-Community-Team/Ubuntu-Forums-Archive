---
title: "I Would Like More Information about Fixes in Software Updater"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2015-08-14
Every day or so I am reminded to apply updates to my system.  These can range anywhere from updates to tzdata to replacement of the kernel.  I have seldom regretted agreeing to the update.  OK this week I got hit with a bug in FireFox 40.0 that cost me a day and a half to figure out a workaround, but that is about as bad as it gets.  But I am uncomfortable that I have to agree to changes where usually all that I am given in information about the changes is the number of kilobytes that are going to be downloaded.  I would prefer it if there was, for example, a hyper-link that I could click on that would take me to a description of exactly what is in the package and why.  For example the tool doesn't even tell me that it is replacing the kernel, and therefore I will have to reboot, or it is replacing the browser, in which case I will have to restart the browser, until it starts applying the fixes.

---

### Post by deadflowr on 2015-08-14
You can always read the change logs for which ever package listed, if you click on the arrow below the package listing window marked something like "technical details".
These usually list whatever changes the new package has, along with links to whatever bug report forced the new package change/fix.

Note that ppas and 3rd party repositories may not support this feature (I know google chrome doesn't).

---

### Post by 7-webmaster on 2015-08-25
> **deadflowr said:**
> You can always read the change logs for which ever package listed, if you click on the arrow below the package listing window marked something like "technical details".
These usually list whatever changes the new package has, along with links to whatever bug report forced the new package change/fix.

Note that ppas and 3rd party repositories may not support this feature (I know google chrome doesn't).

I have clicked on every clickable icon or text in the window, and there is no information available on anything.  The "technical details" button just opens and closes the window that identifies which packages are changed.  There is not enough information to even determine WHICH change log for a given product is relevant.  For example I have have received 3 updates related to Firefox 40, but all of them just say "Firefox 40".   They do not identify which level of FF 40 they reference. I focus on that one because FF 40 broke my web-site requiring 2 days of work to develop a bypass for the lost functionality (clicking on an option in a <select> did not select the option and did not call the onchange method, so I had to add an onclick onto each option).  I can accept some reticence with regard to "security exposures", although it would be nice to know when well publicised major threats, such as the on-going SSL threats, are addressed, but there is no obvious way to get this information.

---

### Post by 7-webmaster on 2015-08-27
> **v3.xx said:**
> Have you tried synaptic package manager?


Synaptic is just a graphical front-end to the CLI Apt commands.  I would need to know the precise identity of the fixes being applied by the software updater to be able to ask any questions about what the fixes actually contain and what they do, and the software updater does not supply any information that I can use to perform that search.

---

### Post by coldraven on 2015-08-27
I just ran "Software Updater". It said that there was an update for Firefox. I expanded the "Technical Details" at the bottom of the screen. It states > Changes for firefox versions:
Installed version: 40.0+build4-0ubuntu0.14.04.4
Available version: 40.0.3+build1-0ubuntu0.14.04.1

Version 40.0.3+build1-0ubuntu0.14.04.1: 

  * New upstream stable release (FIREFOX_40_0_3_BUILD1)
    - see USN-2723-1
Searching for "Firefox USN-2723-1" takes me here where it describes what the patch is for.
[http://www.ubuntu.com/usn/usn-2723-1/](http://www.ubuntu.com/usn/usn-2723-1/)

How hard was that? Windows 10 will not tell you anything about what the updates are doing.

---

### Post by efflandt on 2015-08-27
Just curious what specific issue you had with Firefox 40.0? I have been running Ubuntu off and on since 9.04 a week before 9.10 was released, and the only odd updates I can think of off the top of my head from the normal gui software updater was when Firefox recently blocked flash due to known security issues with flash and kernel 3.13.0-59 which broke Steam and I heard wine and some other things. But in the latter case booting an earlier kernel worked until a newer kernel fixed what broke 3.13.0-59.

---

### Post by tgalati4 on 2015-08-28
With experience, you will find that any updates to the kernel or xorg (graphics) will need a reboot.  With any update applied to your system, there is a small risk of regression--breaking something that was working before.  So you have to weigh the Agony Units, of applying the update and then spending time fixing any regressions.  Printers/CUPS frequently break with kernel updates.  So delete and reinstall printers that break after an update, rather than spend a lot of time trying to troubleshoot CUPS.

Linux Mint uses a Level of 1 through 5 to rate updates based on importance to the system.  They are color-coded and kernel/xorg updates get Level 4 or 5 depending on how extensive the update.  You can hide or unhide Level 4/5 updates so that you can apply minor updates with less chance of breaking your system.  There is no optimum strategy for applying updates.

Instead, keep another computer as a backup that is configured with similar packages.  Update one, but leave the other intact.  So if an update breaks your system, you have a backup.  Another method is to dual-boot.  Keep two copies of Ubuntu on your system.  If one breaks, boot into the other.  

Just about all linux systems maintain backup kernels that you can boot into.  Look at your GRUB2 listing when you first boot and try those backup kernels to make sure they work.  Backup kernels won't help with xorg/graphics issues or a single application that is broken after an update.

---

