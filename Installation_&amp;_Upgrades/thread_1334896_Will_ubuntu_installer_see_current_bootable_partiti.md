---
title: "Will ubuntu installer see current bootable partitions?"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by nickapalooza on 2009-11-22
The drive started out with XP 32bit, then Vista 32bit, now Win 7 64bit. The boot loader of MS's will boot all three operating systems without a hitch.

If I do the "Install Ubuntu inside Windows" (wubi?) installation, will it give me a boot loader with all of the current partitions as well as it's own?

---

### Post by nickapalooza on 2009-11-23
Sorry to have to do this, but SOMEONE must know the answer. Can anyone give me a yes or no?

---

### Post by Scarlath on 2009-11-23
As far as I know, do not quote me on this one though, when installing through Wubi all it does is adding an extra option for Ubuntu in the Windows Boot loader (source: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20select%20whether%20to%20run%20Windows%20or%20Ubuntu?)). Which obviously means you should still be able to see your other options.

---

### Post by nickapalooza on 2009-11-23
Thank you Scarlath. I will now be installing Ubuntu to one of my computers for the first time.

---

### Post by Mark Phelps on 2009-11-23
Just to you know ... LOTS of folks have reported serious problems trying to install Ubuntu 9.10 via Wubi in Win7.  Much better results have been obtained installing it inside Vista.

---

### Post by phillw on 2009-11-23
Wubi installs unbuntu WITHIN the windows area. If you hose your windows area  - you'll wave goodbye to your ubuntu area also.

If you install a dual-boot with windows & ubuntu, then you can transfer your 'stuff' from the wubi 'folder' safely into your new partition and get at the data (files, images, bookmarks etc. etc.)

However, for example, upgrading from XP to, say, Win7 seems to well delete your wubi stuff.

As ever, with 'playing' around with operating systems, the secret is in doing a backup.

As for people having problems with wubi under Win7 .... why not make Win7 run under ubuntu ?  It's virtualbox and you can have as many operating systems as your heart desires.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)    Go have a play :-)

If you want a clear set of instructions for Win7 and ubuntu (or many other permutations)  head over here --> [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Just bear in mind, if you install Win AFTER Ubuntu, you'll need to head over here for the new instructions for 9.10  -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Regards,

Phill.

---

### Post by nickapalooza on 2009-11-26
great answers, thanks guys

---

