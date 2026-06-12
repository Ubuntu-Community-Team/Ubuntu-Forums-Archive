---
title: "Failure While Running Update Manager"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2010-03-26
While running the update manager my system froze and all that I knew to do was power down and power up again.  When I first started the update said 18.5 MB and on restart it said 17.x MB.  I restarted the update manager and it failed with errors.  

The last message says "E: Sub-process /usr/bin/dpkg returned an error code (1) A package failed to install.  Trying to recover:" but no progress in 1/2 hour.  If I try to copy the messages to the clipboard it says that cntl-c will abort the operation so I haven't done that.

From the top of the "Details" there are about eight "Invalid archive signature" messages.  I don't know how to proceed.

Thanks for any help.

---

### Post by n4lbl on 2010-03-26
In the absence of advice I hit "close" and then "check".  There were 9 updates and 0KB to download.  

The messages said: E: /var/cache/apt/archives/libgssapi-krb5-2_1.7dfsg~beta3-1ubuntu0.5_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/libkrb5-3_1.7dfsg~beta3-1ubuntu0.5_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/libkrb5support0_1.7dfsg~beta3-1ubuntu0.5_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/libk5crypto3_1.7dfsg~beta3-1ubuntu0.5_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/app-install-data-commercial_12.9.10.3_all.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/app-install-data-partner_12.9.10.3_all.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/devicekit-disks_007-2ubuntu5_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/landscape-common_1.4.4-0ubuntu0.9.10_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/libwbclient0_2%3a3.4.0-3ubuntu5.6_i386.deb: subprocess dpkg-deb --control returned error exit status 2

Then "Update is complete.  Not all updates succeeded..."  The "details" button does not work!!

Any ideas??

---

### Post by n4lbl on 2010-03-26
"Details" button is OK.  I hadn't hit "close" in another box.

I closed the update manager and restarted it with the same results.  I have no idea of how to proceed.

---

### Post by n4lbl on 2010-03-26
Is there a way to back out the changes and start over??  I assume that there must be but I don't see where.

thanx,,,,

---

### Post by n4lbl on 2010-03-26
I restarted in recovery mode and ran (I think it said) "recover packages" or something like that.  Didn't help.

Restarted in normal mode and ran update manager again.  Since I didn't believe that "trying to recover" was true I tried to copy the content but control-d doesn't work as copy-to-clipboard.

The system boots and runs but obviously has errors.  "Computer Janitor" finds nothing to clean up.  

How do you back out maintenance??  Shall I boot the previous version??  If I did that what else must I do??

thanx,,,

---

### Post by n4lbl on 2010-03-27
Any ideas??  

I thought about _apt-get -f install_ but don't understand enough.  Is this a broken dependency problem??  If this is a dependency problem will this just clean-up and the Update Manager will pick up the pieces the next time I go thru "check"??  Is there possible harm doing this??

---

### Post by mac9416 on 2010-03-27
Hey, n4lbl,

I'm not particularly skilled in this area, but I will offer a suggestion with a bag of salt.

I am guessing that a package got corrupted when the download failed. To fix this, you can delete all package files in /var/cache/apt/archives/ by running...

```
$ sudo apt-get clean
```

Then try to run Update Manager again.

---

### Post by n4lbl on 2010-03-27
Hey mac9416:

That sounded good, I read the man-page and I favor ionic bonds (the salt).  It seems to have worked correctly.  The update manager went after the nine missing entries but transferred 1 MB instead of zero (from the likely corrupted cache).  

Many thanks!!  I believe that you got it!!

---

