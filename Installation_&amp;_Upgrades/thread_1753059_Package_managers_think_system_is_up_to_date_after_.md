---
title: "Package managers think system is up to date after canceling update"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by ktmhz on 2011-05-08
I did a clean install of 11.04 this morning. Upon logging in, Update Manager appeared, telling me there were 67 packages to upgrade. I obliged, and the update progress window appeared, as usual.
At this point I realized it was not a convenient time to install the updates. No progress had yet been made; Update Manager had not downloaded anything, the progress bar had not moved, and the status was "waiting". I canceled the update and closed Update manager. However, upon running it again, it thinks that it successfully installed all the packages. In the "Ubuntu Software Center" Update history, it shows all those packages as having been updated with a timestamp of when I canceled the update.

apt-get and aptitude will not update the packages either. It seems like the packages have been marked as updated even though no update was installed. How can I rectify this problem and get the package managers to actually install the updates?

---

### Post by Quackers on 2011-05-08
In a terminal try ```
sudo dpkg --configure -a
``` and see what is reported.

---

### Post by ktmhz on 2011-05-08
Alas, nothing is reported:
```

$ sudo dpkg --configure -a
$ 

```

---

### Post by Quackers on 2011-05-08
If you open synaptic package manager and look at the very bottom of the screen where it says 33596 packages listed, 1545 installed etc etc does it mention any number of broken packages?

---

### Post by ktmhz on 2011-05-08
similarly, no broken packages are listed in Synaptic.

---

### Post by Quackers on 2011-05-08
Ok, still in synaptic click on Settings and choose Repositories and in the new window uncheck one of the voxes there. But remember which one!!!
Then click on the close button. You should get a pop-up telling you to reload. Ok that pop-up then click on the Reload tab near top left of Synaptic window.
When that's run, click on Settings/ Repositories again and check the boc that you unchecked earlier. Close the screen and click on Reload again in synaptic.
Is there now an "upgradeable" heading in the left pane of synaptic? If so click on it and you should see updates in the right pane.

---

### Post by ktmhz on 2011-05-08
Still no luck. It is as though the record of what has been updated was written before the updates were downloaded and installed. I am just going off of the fact that I canceled the update manager before it appeared to download or install anything. However, "firefox -version" returns the version that it ought to be after the update, not what it should have been prior, so maybe something weird happened and the update manager was actually downloading and not showing it...
Maybe it's best I just let this be, and if I end up with slightly outdated packages until their next updates, so be it. The "firefox -version" however, suggests that the packages actually did get updated.

---

### Post by Quackers on 2011-05-08
It seems strange, but if there are no adverse effects it may be best to leave things alone, as you say :-)

---

