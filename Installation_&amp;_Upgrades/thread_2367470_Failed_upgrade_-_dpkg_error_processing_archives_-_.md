---
title: "Failed upgrade - dpkg: error processing archives - failed to open package files"
date: 2017-07-30
forum: Installation &amp; Upgrades
---

### Post by quantumburnz on 2017-07-30
My Ubuntu upgrade failed due to a lack of disk space.  I think primarily because my /boot didn't have enough space.  I've done quite a bit to recover, but I've probably made things worse.  After the failed upgrade, I couldn't get to the GUI so I've been working from the command prompt (Ctrl + Alt + F1).  I've tried to cleanup some of the packages that failed to install but apt was failing so I've been trying to work with dpkg.  However, I haven't been very successful in actually getting anything to install.  This is what I'm getting when trying to install anything:


dpkg: error processing archive /var/cache/apt/archives/package.deb (--unpack):
  failed to open package info file '/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory
[ATTACH=CONFIG]276184[/ATTACH]

Any guidance or push in the right direction of how to recover from this would be greatly appreciated.
Thanks!

---

### Post by DuckHook on 2017-07-31
Welcome to the forums, quantumburnz.

I wish the welcome could have been under better circumstances.

Borked upgrades are generally bad news and there's not much chance of recovery. Based on your description of your actions, you would spend far more time trying to straighten things out than simply reinstalling and restoring your data. The biggest problem is that you've further tinkered with the already broken system using dpkg, which is a very low-level tool capable of making things worse. I assume that you can't retrace all of the changes and attempted "fixes" you made either.

My suggestion at this point is that you install a fresh system and then restore your critical data from backups. You have made backups, right? If not, then don't do anything further on your current HDD until you've backed up your whole /home directory. If necessary, you can do this with a LiveUSB/DVD and a third USB HDD/SSD/USB-stick/drive. Just boot into the LiveUSB and copy the whole /home directory of your old HDD onto the backup media. Make sure it is readable before wiping your HDD and installing a pristine OS, this time, making sure to have enough room for /boot.

---

### Post by quantumburnz on 2017-07-31
Thanks DuckHook, and I wish the welcome were under better circumstances as well.

That's pretty unfortunate about "borked" upgrades.  I did save my dpkg status file before I started messing with anything other than the new kernel that was attempted to be installed during the upgrade, 4.4.0, if that helps.

I hoped to attempt the recovery and learn something new in the process but if it's not worth it, I can just start fresh.  If you have any insight to push me in the right direction though, I'd be happy to give it a shot.

Either way, thanks for the input.

---

### Post by DuckHook on 2017-07-31
> **quantumburnz said:**
> …That's pretty unfortunate about "borked" upgrades.See my sig.> …I did save my dpkg status file before I started messing with anything other than the new kernel……but did you back up? Please tell us you have good backups from which you can restore? A dpkg status file is better than nothing, but it isn't much to go on. It doesn't tell us what you subsequently did. What files did you subsequently delete? What did you subsequently do with *apt*, *dpkg* or even *rm -rf*? It's like trying to put a jigsaw puzzle back together with some of the pieces missing.> I hoped to attempt the recovery and learn something new in the process but if it's not worth it, I can just start fresh.If this is not a production machine, contains no important data, and you just want to learn, then there is no better way to do so than trying to fix something that's really broken. But to do so, you will have to provide far more info. You can start by retracing for us exactly the steps you took trying to "fix" the problem. You must be very detailed and you can' t leave anything out. Please use the point-form format controls in the "advanced reply" posting box.

If you can't remember your steps, then your desire is not realistic. The members of this forum may be able to help you restore a critical file if we know what it is, but not if we have nothing to go on.

---

### Post by quantumburnz on 2017-08-12
I should have kept better notes...  I will next time I go to do something like this since I'd like the learning experience.  Although, in the days of containers and VMs, perhaps this doesn't even matter any more.  :)  Thanks for your help and guidance!

---

