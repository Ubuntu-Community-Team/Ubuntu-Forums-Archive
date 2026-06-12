---
title: "Problem with  xorg-driver-fglrx after upgrade"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2006-11-04
Got this message after upgrading to edgy, whilst in synaptic:

"E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2".

I have tried several ways to progress but no further updating of the system via synaptic can occur.  There are over 1000 packages waiting to be upgraded.

Any suggestions please?

---

### Post by amohanty on 2006-11-04
In synaptic, click on the custom button on the bottom left, and select Broken  in the list above, does anything show up there?

---

### Post by aum11 on 2006-11-04
Thanks amohanty and yes,

synaptic says that xorg-driver-fglrx is broken.

How to fix?

---

### Post by amohanty on 2006-11-04
Ok on the right pane, right click on the xorg-driver-fglrx package and select Remove Completely.

Once its done, run:
sudo dpkg-reconfigure xserver-xorg
run through tht defaults and reboot.

Once you are done, then if you want 3d accel, retry the fglrx install procedure

HTH
AM

---

### Post by aum11 on 2006-11-04
Followed Your advice. The same problem is still there when trying to delete it:

E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2.

After further searching through the forums there was a chance that "sudo aptitude update && sudo aptitude upgrade" would fix the problem but it also returned with this message:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: xserver-xorg but it is not installable

So then I thought to try to install xserver-xorg however it changes about 60 packages.  In particular it changes many xserver-xorg-driver* packages to xserver-xorg-video-*.

Is it ok to proceed with this install?

Am lost here and really need some wisdom....thanks.

---

### Post by aum11 on 2006-11-04
Used package force in synaptic to install the earlier version of xorg-driver-fglrx required for edgy.

However there is now a problem with xfonts-intl-european with the error message 

E: xfonts-intl-european: subprocess post-installation script returned error exit status 2

This upgrade is a nightmare!!!!

Any help please.

---

### Post by amohanty on 2006-11-04
> In particular it changes many xserver-xorg-driver* packages to xserver-xorg-video-*.

I think that should be fine. But you will have to undo the force installs you did.

HTH
AM

---

### Post by aum11 on 2006-11-05
Thanks for your help.

No updates can occur because of the xfonts problem.  It seems as though this must be overcome to proceed further.

Any suggestions?

---

### Post by amohanty on 2006-11-05
Oh thats fairly easy:
1. Fire up synaptic
2. Select Custom in the bottom left
3. Select Broken in the left panel
4. Right click on the pkg in the right panel and select remove completely

and you should be good to go

HTH
AM

---

### Post by aum11 on 2006-11-05
There are no broken packages.  No matter whether I try to remove, complete remove or reinstall this same error keeps on arising.  It is the same for any update that I have tested.Always the same xfonts error as above.

Further advice please.

---

### Post by amohanty on 2006-11-05
Can you look for the offending package in synaptic (xfonts-intl-european) and remove it.

AM

---

