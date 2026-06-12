---
title: "Grief after updating following Gutsy re-install"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2008-03-11
I re-installed Gutsy on my Dell desktop yesterday and everything went smoothly.
Until, that is, I installed the 198 updates that announced their availability as soon as I rebooted to the newly installed Ubuntu.
When the update was complete, these mesasages remained:

```
initramfs-tools: subprocess post-installation script returned error exit status 2
```
```
linux-image-2.6.22-14-generic: dependency problems - leaving unconfigured

linux-restricted-modules-2.6.22-14-generic: dependency problems - leaving unconfigured
```

(note that these messages are transcribed but should be fairly accurate)

When I rebooted, the GUI boot screen did not show up but a text-based output. Also, only 640x480 or 800x600 screen resolutions were available to me.
Further, although the package linux-restricted-modules-2.6.22-14-generic was marked in Synaptic as being installed, in fact a slightly different version (-2.6.14-22.10 I think) was installed).

So, I re-installed Guitsy but this time did not go for the updates. As things stand everything is working perfectly.

Does anybody know 
i) why my updates caused such problems?
ii) what can I do to prevent this happening again?

---

### Post by rillip on 2008-03-11
It looks like the kernel tried to update but couldn't because of some package update.  Next time unselect any kernel updates and let all the other updates install first.  Reboot to make sure everything is still good, then let the kernel upgrades run.  Reboot again to make sure everything's okay.  If not, rever to a former kernel from the Grub menu list and continue troubleshooting.

I'd say the next step for this error would be to run 

```
sudo apt-get update
sudo apt-get upgrade
```

and see what happens from there.  There are also error logs for dpkg, I think in /var/log, might be worth it to check those for errors related to that package.

---

### Post by PaulFXH on 2008-03-11
Thanks for your reply.
Actually, before I had a chance to read this, I had decided to install ALL of the available updates apart from linux-restricted-modules-2.6.22-14-generic.
I only did this because of  a gut-feeling that this was this source of the problem.
Surprisingly, everything installed without problem and Gutsy is running normally for me now other than the fact that I have one outstanding update waiting to be installed.
Another surprising feature is that linux-restricted-modules-2.6.22-14-generic is actually marked in Synaptic as being installed although the installed version is 2.6.22.4-14.9
On my Laptop which also has Gutsy, the installed version is 2.6.22.4-14.10

So now I'm in a dilemma: Should I leave well enough alone given that I'm not aware of anything I'm missing by not having version 2.6.22.4-14.10 installed and the update is rated only as Recommended rather than Important?
Or, should I assume that whatever caused the problem before has dissappeared with the latest re-install and therefore the outstanding update won't cause any problems?
If you have views on which way I should go, I'd love to hear them.

---

