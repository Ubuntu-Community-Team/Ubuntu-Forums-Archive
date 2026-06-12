---
title: "Upgrade form 14.04 LTS to 15.04 velvet"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by luwizghieherald on 2015-04-29
Hie guys,
I upgraded my Ubuntu desktop 14.04 LTS to Ubuntu 15.04 velvet. After the online upgrade process the system requested to reboot. On reboot, the system went straight to command prompt with the following: "Welcome to emergency mode! After logging in, type "journal -xb" to view system logs, ""systemctl reboot" to reboot, "systemctl default" or ^D to try again to boot into default mode."

What can I do to boot normally. I have tried the provided option for rebooting and booting into default mode but to no avail.

---

### Post by Bucky Ball on 2015-04-29
Welcome. How did you upgrade your machine? A clean install?

A bit off-topic, but just curious as to why you upgraded from an LTS to an interim release. Was there a specific reason? 14.04 LTS is supported for five years, until April 2019. 15.04 is supported for nine months from now (about the end of Jan 2016 by my calculations).

---

### Post by luwizghieherald on 2015-04-29
I really did a silly mistake. I upgraded via the internet. It was not a fresh installation. There was no specific reason. Can you help me please. As of now when I use the installation disk to repeir my OS its not showing all the partitions on my drive by only sda and sdb. Can I repair this?

---

### Post by Bucky Ball on 2015-04-29
Hmm. What should be there? What are you seeing with Gparted when you boot from the Live media and 'Try Ubuntu'?

If you KNOW you've accidentally deleted some partitions or data that you want to retrieve, best to _stop using the drive immediately_ and see these links:

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You have sda and sdb. One is the internal drive, one is the live media probably (or another external storage device). You mean you are missing partitions on one of the drives?

PS: I'm guessing you did an net upgrade of 14.04 LTS to 14.10 to 15.05 as there is no direct net upgrade from 14.04 to 15.04 (unless there's something new I'm unaware of)? ;)

---

### Post by luwizghieherald on 2015-04-29
When I use try Ubuntu am able to run it and I can see all the partitions under devices. All my data is there but the issues is when I boot normally its going straight to command prompt on emergency mode.

The main issue is to get away from this emergency mode to boot normally.

---

### Post by kansasnoob on 2015-04-29
How exactly did you upgrade from 14.04 to 15.04? It's not possible to upgrade directly from 14.04 to 15.04 using the release-upgrader via update-manager. You would have had to go 14.04 -> 14.10 -> 15.04 unless you manually changed all of your software sources and then did a dist-upgrade which would probably break things irreparably.

---

### Post by luwizghieherald on 2015-04-29
It was a bad idea.

I followed this: [http://www.noobslab.com/2015/04/how-to-upgrade-to-ubuntu-1504-vivid.html](http://www.noobslab.com/2015/04/how-to-upgrade-to-ubuntu-1504-vivid.html)

I think the best way is to have a backup of my data and re-install Ubuntu....

---

### Post by kansasnoob on 2015-04-29
> **luwizghieherald said:**
> It was a bad idea.

I followed this: [http://www.noobslab.com/2015/04/how-to-upgrade-to-ubuntu-1504-vivid.html](http://www.noobslab.com/2015/04/how-to-upgrade-to-ubuntu-1504-vivid.html)

I think the best way is to have a backup of my data and re-install Ubuntu....

The writer is obviously a boob rather than a noob ;)

Did you use the graphical process? Either way it wouldn't really directly upgrade 14.04 to 15.04. So we don't really know if you're now on 14.10 or 15.04.

Did you backup your data first? If so I suspect reinstalling would be easier than anything else. But if this is a dual-boot ask for some guidance first so you don't wipe your Windows OS!

---

### Post by luwizghieherald on 2015-04-29
Thanks Kansasnoob and BB,

I have reinstalled my Ubuntu 14.04 LTS. I have taken backup of all my data. I will upgrade later to 14.10. Thanks guys.

I consider this conversation closed.

---

### Post by Bucky Ball on 2015-04-29
I would stick right where you are on 14.04 LTS rather than upgrade. 14.10 has three or four months of support left. Hardly worth the effort.

Please mark the thread as solved (by following the second link in my signature). Thanks.

---

