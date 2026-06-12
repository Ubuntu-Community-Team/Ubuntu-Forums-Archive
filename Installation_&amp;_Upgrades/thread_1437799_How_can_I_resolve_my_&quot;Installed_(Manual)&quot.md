---
title: "How can I resolve my &quot;Installed (Manual)&quot; packages?"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by gbear14275 on 2010-03-24
Hello,

I have lived with this quirk for a while.  When I organize my packages in Synaptic by status I an extensive list of "Installed (Manual)" packages which include many core packages (See below for examples).  I have tried looking for a resolution to this issue but was only able to find a couple related offerings.  Can anyone explain this quirk or possibly tell me how to appropriately classify these packages?  Thank you.

V/R
Garrett

P.S.  Selecting them and classifying them as "Automatically installed" via the packages menu option just reclassifies them as Auto Removable.

Related:
[http://ubuntuforums.org/showthread.php?t=1258250](http://ubuntuforums.org/showthread.php?t=1258250)
[https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/424643](https://bugs.launchpad.net/ubuntu/+source/livecd-rootfs/+bug/424643)

My Package list examples:
acl
...
alsa-base
...
apparmor
apparmor-utils
apport
...
aptitude
...
gdm
...
(many More)

---

### Post by gordintoronto on 2010-03-24
> **gbear14275 said:**
> Hello,

I have lived with this quirk for a while.  When I organize my packages in Synaptic by status I an extensive list of "Installed (Manual)" packages which include many core packages (See below for examples).  I have tried looking for a resolution to this issue...


I don't understand what makes this "an issue"?  If it makes the core packages harder to delete, that seems like a good thing.

---

### Post by floborg on 2010-03-26
After reading that bug report, I'm not sure there's any point in trying to fix this ourselves.  They have done nothing about it, so it will come back the next time we upgrade.  I think someone found a semi-automatic way to do this in another thread...

---

### Post by dcstar on 2010-05-02
> **gordintoronto said:**
> I don't understand what makes this "an issue"?  If it makes the core packages harder to delete, that seems like a good thing.

Not really, the "Manually installed" section is supposed to be just that - and area where a user can see what has been installed outside of the default system installation. No critical packages should ever be in that section anyway.

The "bug" is due the the Ubuntu installation process not marking all those packages as installed by the that process, hopefully it will be fixed by 10.10.......

If you read the second bug report you will see that you can manually mark most packages as "Automatic" if you are selective.

---

