---
title: "Upgrading from 16.04 LTS to 18.04 LTS"
date: 2019-09-02
forum: Installation &amp; Upgrades
---

### Post by c-cubed on 2019-09-02
If you're considering upgrading from 16.04 LTS to 18.04 LTS my suggestion is don't try it.

A much better approach is to get a thumb drive or usb drive; download the 18.04 ISO installation image.
Install on the removable device.
Boot the new 18.04 image on the removable device.
Mount your current 16.04 LTS partition.
On the booted 18.04 image create a spreadsheet with date, time and action columns.
Now methodically install and configure software on the new 18.04 image until you have an exact duplicate of your 16.04 installation,
 being very, very careful to record each step. Its highly likely you will have to redo or undo many f them.
Finally create new partitions on your hard drive for 18.04.
Install the 18.04 ISO image in the new partitions.
Boot the new 18.04 LTS on the new partition.
Repeat the steps that were successful on the removable device.

Why do it this way?
1) You preserve your original 16.04 installation and can always fall back to it.
2) If you have any significant software installed on 16.04, trying to upgrade will lead to many failures and frustrations.
3) This approach allows you to copy over configuration files from 16.04 and 18.04 (on removable device) and edit as necessary.
4) You are likely to discover software and features that existed in 16.04 and are no longer available in 18.04. This process
    allows you to experiment (a good example is 32-bit Eclipse, doesn't exist in 18.04 LTS).

---

### Post by TheFu on 2019-09-02
Before doing any major updates, we should all make know-you-can-restore backups.  This is a common thing for computing. Don't at your own risk.

I like to pull a list of manually installed packages as part of my backup method.  Use **apt-mark** for this.  Save it into a file that gets included in your backups, so you'll have it on the other side.

If anything fails in the attempted upgrade, I'd just wipe and perform a fresh install, then using the backups as a guide to have everything installed that was there previously.  System and personal config files, settings, and data are all included in the backups, so bring those things back or having them as reference is pretty easy.

And if everything fails, you still have your system backup which can be restored so you can try again later from the same know point.

---

### Post by grahammechanical on 2019-09-03
I learnt several years ago from this forum to have a separate partition just for data. My data can be accessed from more than one installation of Ubuntu. I do not risk loosing data with an upgrade failing. If I am careful I can install, re-install and remove installs by partitioning without loosing data.

I also like to have more than one working install of Ubuntu so that I can carry on working if I mess up my usual install of Ubuntu. I usually have an LTS and an Interim release.

Regards.

---

