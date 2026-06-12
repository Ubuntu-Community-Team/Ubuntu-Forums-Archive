---
title: "Feisty Upgrade Wiped My Entire Hard Drive!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by iq-9 on 2007-04-21
Kubuntu 7.04.  After the "official" upgrade failing at about 57% and hanging the system, I rebooted.  Tons of text errors on the screen and the machine would not boot.  So, I installed the CD.  Not once did the CD installer warn me that the installation would wipe my entire hard drive clean.  My entire setup is gone!  Months of work!  Gone!

How about a kind message, "There was data detected on volume [whatever]. If you proceed with this installation you will loose all data on this drive." Then, how about some options? Installing to a different drive or partition.  Absolutely unacceptable for a product that has impressed me so much over the past 6 months.

Does anyone know if my data is, in fact, gone?  I have a hard time believing that an OS installer would really destroy hard drives unannounced.  Is my data on some alternate partition somewhere - hidden maybe?

Any help is immensely appreciated.

---

### Post by jdong on 2007-04-21
The installer definitely warns the step before installation commences that it will format the listed partitions, with an accompanying statement that formatting will result in data loss.


At this point, unfortunately, it is prohibitively difficult to do a full recovery of a drive that has been reformatted and partially overwritten.

---

### Post by sandman55 on 2007-04-21
You could try looking with the live CD also you only mentioned Ubuntu not a dual boot with XP but if it is a dual boot then you probably just have to replace the Master Boot record on XP which is quite simple so post back if thats the case

---

### Post by jdong on 2007-04-21
I just ran through the Ubuntu installer (I don't have the Kubuntu one on hand, but they present the same dialogs, just in different GUI themes), and the pre-install confirmation page does warn that it will destroy data, though understandably in the heat of the battle we can easily overlook such warnings.

---

### Post by TransitMan on 2007-04-21
You tried and failed at 57% of the "official" upgrade route. 
You re-booted, got a ton of error messages and then rebooted with the CD to do an install.
When the CD install failed to find your previous installed files, it was because a portion of those files were already converted over to Fiesty. And the /mbr had been written over as well. Hence, finding a previous install was not possible, because you had a prior failure that you were trying to correct with the CD install.
And like jdong stated, in the heat of the install, over-looking the warning screens are very easy to do.
My only other thought on this matter is, did you back up your impotant data, or have you lost this as well and are now blaming the CD install routine on this?

When updating from a prevous OS install, always make a fresh back-up of your most important data, that way you will not lose that which is important.
As for settings, some of those may not be able to be backed up.

Do not blame the new OS for a lack of preparation on your behalf.
Step back, take a deep breath, relax and think before proceeding. You'll thank yourself later.

---

### Post by iq-9 on 2007-04-21
OK, I'm an idiot. You'll have to forgive me. Using computers since the mid 70's [90% Windoze, admittedly]. Total brain fart.

The entire time, I was running in the "virtual" Kubuntu - when the CD first boots.  [I thought it just went ahead and installed itself unattended.]  I haven't actually reinstalled the OS yet.   I've installed [K]Ubuntu before and I'm fully aware of this "virtual" installation approach.  It just slipped my mind, for some reason.  Nonetheless, my computer is still in a bad state from the failed "upgrade" install.  On boot, I get a screen full of file system checks, then it just sits there.  But, maybe my data is still there and recoverable.  I'm really only after my website.  Lots of work in there.  The rest of the stuff I [may have] lost I can rebuild or live without.

So, the important question.  Where is my data and how do I get it off the hard drive and onto something external - a different system on my network, a CD, or even a CF Card?  The website I'd like to retrieve used to reside in /var/apps/rb/, but this is a path I do not see when I go to the Root folder in this "virtual" Kubuntu.

I can see the partition in Disk & Filesystems.

    1 Partition 143.2 Gb   / dev/sda1
    2 Partition 1.0 Kb       tmpfs
    5 Partition 5.8 Gb       / dev/sda5

I can also see it in the QTParted partition manager.  How do I access this drive?  I can't "cd" to it.  I can't simply double click it in these partition managers.  Once I access it, how do I burn it to a CD, send it to a Windows box, or send it to a USB CF Card reader?

Assistance is greatly appreciated.

---

### Post by iq-9 on 2007-04-21
OK, got it!

$ mkdir /mnt/sda1
$ mount /dev/sda1 /mnt/sda1
$ cd /mnt/sda1
$ ls -l

There's all my stuff!!!

Now getting it off is another story...  Working on it.

---

### Post by iq-9 on 2007-04-21
Got it!

Bring up two Konqueror windows.  Enter "//<windows server name>" into the address bar. Type my Admin login.  Done!  There's all the shares on my Windows box.  Drag my old files over.

Phwew!  That was close.

---

### Post by TransitMan on 2007-04-21
Glad you got it worked out.

And don't feel bad. Those "brain farts" happen to all of us at one time or another, even me.

---

### Post by iq-9 on 2007-04-21
After I got it working, I documented the process of installing Ruby on Rails on Kubuntu:

[http://www.russbrooks.com]("http://www.russbrooks.com")
[Install Rails on Kubuntu]("http://www2.russbrooks.com:8080/2007/4/21/install-rails-on-kubuntu-7-04-feisty-fawn")
[Install nginx and Mongrel Cluster on Kubuntu]("http://www2.russbrooks.com:8080/2007/4/21/install-nginx-mongrel-cluster-on-kubuntu")

---

