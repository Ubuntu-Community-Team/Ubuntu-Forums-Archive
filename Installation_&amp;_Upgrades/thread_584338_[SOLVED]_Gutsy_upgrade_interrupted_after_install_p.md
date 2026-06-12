---
title: "[SOLVED] Gutsy upgrade interrupted after install packages download"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Riemann on 2007-10-20
Hi everyone.
I was upgrading from Ubuntu Feisty but had to shut down my computer after update manager finished to download all the need packages for the 
Gutsy upgrade process but not finished to unpack, install nor configure them.

When I got back and restart the computer, the X window server doesn't start and the screen turn off after a few seconds of darkness. So, I switched to a text console [CTRL+ ALT F1] and use:

**sudo dpkg --configure -a**

to resume the installation of downloaded packages. 

But I'm not sure if this finish all the Gutsy upgrade process or if there is something still to do that **dpkg --reconfigure -a** cant do.

Could somebody tell me how to be sure is the upgrade process is complete???:confused:
Thanks for your answers.

---

### Post by barney_1 on 2007-10-20
I had a similar problem when doing to upgrade in that the installer crashed.  After I ran the
```
sudo dpkg --configure -a
```

I logged back in (rebooting might be necessary to get X running again) and went to synaptic package manager once more.  I choose to "mark all upgrades", then "appy changes" and it seemed to finish the rest of the upgrade process without a hitch.

I hope this helps, good luck!

---

### Post by Six13 on 2007-10-21
Thanks so much! I was having the same problem and that fixed it!! :D

---

### Post by heldal on 2007-10-21
> **barney_1 said:**
> I had a similar problem when doing to upgrade in that the installer crashed.  After I ran the
```
sudo dpkg --configure -a
```

I logged back in (rebooting might be necessary to get X running again) and went to synaptic package manager once more.  I choose to "mark all upgrades", then "appy changes" and it seemed to finish the rest of the upgrade process without a hitch.

I hope this helps, good luck!

The same can be achieved from the commandline using "apt-get update" (get the latest file-lists) and "apt-get upgrade" (download and install all available upgrades).

There may however be a few glitches. As dependencies may change between releases some packages may be temporarily removed to resolve such complex relations between packages during the installation. If the process aborts such packages may not be marked for upgrade or install in the package system. As a final check I extracted the lists of packages to be installed and those to be upgraded from /var/log/dist-upgrade/main.log and fed them in a loop to apt-get which then would install the missing packages and not touch anything that already was installed. My upgrade had aborted about the same place as OP mentioned and this last step then resulted in about 20 additional packages being installed.

---

### Post by Riemann on 2007-10-21
> **barney_1 said:**
> I had a similar problem when doing to upgrade in that the installer crashed.  After I ran the
```
sudo dpkg --configure -a
```

I logged back in (rebooting might be necessary to get X running again) and went to synaptic package manager once more.  I choose to "mark all upgrades", then "appy changes" and it seemed to finish the rest of the upgrade process without a hitch.

I hope this helps, good luck!

In synaptic I choose "Edit->mark all upgrades" and then the status bar reads "All upgrades successfully marked" but the right bottom panel said "no package selected" and the "apply" button was unable. So I suppose my system is already upgraded :)

Thanks all for the replies.

---

