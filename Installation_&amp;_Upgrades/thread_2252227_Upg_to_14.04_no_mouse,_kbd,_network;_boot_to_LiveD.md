---
title: "Upg to 14.04: no mouse, kbd, network; boot to LiveDVD works fine; now what?"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by drifting_along on 2014-11-10
My upgrade from 12.04 to 14.04 did not go smoothly but after a few apt-get update, upgrade, clean, etc. I could boot to the desktop.  But the mouse and keyboard do not work and it appears there is no network connection.  I cannot even boot to the GRUB menu.  Booting with a LiveDVD of 14.04.1 works fine, and I can see all data on my drives, so I think my hardware is ok.  So what next?

I use this machine as a Plex Media Server with lots of movies, all on three large non-boot drives.  I would have to double check but I can probably afford to wipe the boot drive or use another drive altogether.  There's no data worth saving other than the movies.  Would it be easy to install 14.04.1 fresh and add the data drives later?  Or should I attempt a repair?  Either way I need advice on where to start, as I am still a bit new to Linux/ Ubuntu.  In case it matters the CPU is AMD A6-5400K (on-chip graphics) on an ECS mobo.  Thanks!

---

### Post by sp40140 on 2014-11-10
The symptoms point to something going wrong with upgrade. If you say that live CD / DVD boots and all hardware works, then no need to change the HD. 
Did you run into any errors while upgrading? How did you upgrade? Did you use a cd/dvd/usb drive? or commandline or update manager gui?

Now to Fix this, I think if you run ubuntu installer, it gives you option to repair the os (IIRC). If not, you can just do clean install from scratch on that same partition where the current os is installed. And as you mention that all your data is on other drives, there shouldn't be any risk to it. But still be careful when you run installer and choose the correct drive from the list.

---

### Post by Mark Phelps on 2014-11-10
> Would it be easy to install 14.04.1 fresh and add the data drives later? 

That's what I do to "upgrade" from one release to the next.  I'd even recommend that you do, as I do, and disconnect ALL but the target drive when doing the install.  That prevents any accidental overwrite of other drives during install.

---

### Post by drifting_along on 2014-11-10
@sp40140: I used the update manager GUI.  I just hit the button and let it run.  It ran for a while and while I was turned away the system just shut down.  After restarting I had to do a few apt-get commands from the command line to install/ update everything.  That took hours and resulted in an incorrect upgrade because of the loss of keyboard and mouse.

@Mark: Thanks for the advice on that "upgrade" method--I'll try it but have one concern.  I am wondering how the old drives are recognized after upgrading.  Do I need to copy that file that specifies the UUIDs and other settings for the drives (what's the name of that file?) and copy it back after upgrading?  Or will the system recognize the drives automagically after I hook them back up?

Thanks to both for your help.

---

