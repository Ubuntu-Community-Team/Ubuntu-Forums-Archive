---
title: "Ubuntu 16.04 no longer runs after Virtual Box upgrade"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by Bewildered_Bob on 2016-07-29
Ubuntu 16.04 had been running successfully until Virtual Box was upgraded first to 5.0.26 and then to 5.1.2. Corresponding extension pack was also installed. VM appears to start normally and prompts for password to unlock keyring (which apparently authenticates correctly) but then freezes. What am i doing wrong ?

Bewildered Bob

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
EDIT - (1) running with _**WIN 7**_ as _**HOST**_  (2) when VM starts err msg - "virtual box client failed to connect to VB kernel service (rc= verr_access_denied)" appears along with a strange desktop. (3) prompt for keyring id accepted but then it freezes.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

---

### Post by ajgreeny on 2016-07-29
I had big difficulties with VBox 5.1 when I tried it a week or two ago.
I have guests of Linux Mint 17.3 and 18, Xubuntu and Ubuntu 16.04, Debian 8.5, and also WinXP, all of which ran faultlessly in VBox 5.0.# versions in my Xubuntu 14.04 as the host and all the 4.3 and 5.0. versions have given me none, or very few problems ever.

When I noticed 5.1 was available I immediately tried it but it had problems with graphics, USBs, and networking. I did not bother trying to solve this but immediately downgraded back to the 5.0.# version and with that version, the problems went away.

Perhaps worth trying that yourself to see if you have the same success with Vbox-5.0.26, the current 5.0 version.

---

### Post by Bewildered_Bob on 2016-07-30
Thanx for the quick reply. Vbox 5.0.26 was tried first without success so 5.1 was tried next. I'm willing to revert to older release but have not downgraded VBox before - are there instructions or "gotchas" for going backwards ?

---

### Post by ajgreeny on 2016-07-30
> **Bewildered_Bob said:**
> Thanx for the quick reply. Vbox 5.0.26 was tried first without success so 5.1 was tried next. I'm willing to revert to older release but have not downgraded VBox before - are there instructions or "gotchas" for going backwards ?
Not really any problems; just get the deb from the VBox site or use the repos as shown on the VBox site for **Debian based distributions** as I do, and install it in your usual way.  If you use synaptic and the repos you will need to chose to remove the 5.1 version and install the 5.0 version.

---

### Post by Bewildered_Bob on 2016-07-31
Hello AJ:

(1) i'm running Win 7
(2) i'm also a newbie Ubuntu user

Is there a simple solution for this ?  If not maybe i shd reinstall the VM (16.04 or 16.04.1)   Shd VBox also be reloaded first - if so probably 5.0.20 since it ran successfully before the upgrade. Do you agree ?  Thanx.

Bewildered Bob

UPDATE: Vbox 5.0.20 has been reinstalled but not "customer additions". Altho the GUI does not appear during startup, a terminal session is opened by pressing ALT+CTL+F1. Apparently the 16.04 VM is running but will not access the normal GUI (instead a desktop appears and err msg below). 

=======================================================================
VirtualBox client failed to connect to virtualbox kernel service (RC = verr_access_denied)
============================================================

What am i doing wrong ?

---

### Post by ajgreeny on 2016-07-31
If VBox-5.0.20 was the last one that worked successfully for you, yes, why not reinstall it.

If you still do not have the .deb file of that version you can get it from [https://www.virtualbox.org/wiki/Download_Old_Builds_5_0](https://www.virtualbox.org/wiki/Download_Old_Builds_5_0), scroll down to the version you want and also get the Extension Pack of the same version.

EDIT:
I think I may have misunderstood you.  Are you using Win 7 as the host OS and using guests of Ubuntu 16.04?
If that is so, I don't think I can help you with any certainty as I do not use Windows any more apart from a guest OS of Win XP on my Xubuntu host.

---

