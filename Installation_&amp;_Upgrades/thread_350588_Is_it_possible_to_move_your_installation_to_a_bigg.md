---
title: "Is it possible to move your installation to a bigger drive?"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by fbarcenas on 2007-01-31
I purchased a bigger hard drive for my laptop and have it connected to my laptop in an external USb enclosure.

I installed and tried to use gparted to copy the partitions to my new drive, however gparted won't  let me copy any partitions that are currently mounted. 

If I bootup with my live CD I won't have access to gparted, so I'm in a catch-22.

Will the Grub be coppied also and continue to boot or will I have to try to recue the new drive in order to get it to work?

Can someone refer me to a step-by-step guide to getting this done?:confused:

---

### Post by Rab22 on 2007-01-31
I believe the LiveCD has Gparted. That's how you can manually partition when you install.

Maybe you can use dd to move the partitions? I'm not entirely sure how this would work, but I know that people do backups like that.

In fact, there was a fantastic article on these forums about backing up using Ubuntu a while ago. Trying searching something like that out -- maybe it'll help.

---

### Post by minitman on 2007-01-31
I have been playing with linux on and off for awhile and am now really interested, but a real novice. I know you can clone the hard drive with Acronis Migrate Easy. They have a 15 day free trial. It can boot from floppy or cd and clone the old drive structure to the new drive. I have done this hundreds of times recovering failing drives over to new units. I have no experience in the Linux environment but look at Partimage that looks like it will do what you want to do. Check out:  [http://www.thefreecountry.com/utilities/backupandimage.shtml](http://www.thefreecountry.com/utilities/backupandimage.shtml)

Also  check out:  [http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html](http://www.faqs.org/docs/Linux-mini/Hard-Disk-Upgrade.html)

---

### Post by z987k on 2007-01-31
should be able to do something like dd if=/ of=/mnt/new_drive and then make sure you would do it with any other partitions like if you had /home on a different partition than /.
I could be missing something to.  I'm stuck on a windows computer right now.
[http://linuxreviews.org/man/dd/](http://linuxreviews.org/man/dd/)

---

### Post by reiki on 2007-01-31
I used partimage to do exactly this... moved from an IDE to a SATA drive. Yes it's possible to move an entire install but be aware that using partimage will also clone the UUID of the drive. This is not an issue if you're not going to use the old drive any more. Search for my posts on the UUID saga

---

### Post by Quintin Riis on 2007-02-16
dd is for working with block special devices whoever was writing about it above.

Do you have any planned partition layout?  I can help you do this, it's really quite easy.

---

