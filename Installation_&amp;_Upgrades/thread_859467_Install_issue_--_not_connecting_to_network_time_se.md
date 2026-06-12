---
title: "Install issue -- not connecting to network time server"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by deltoids on 2008-07-14
Hi, everyone, I'm installing Ubuntu 8.04, and so far, so good, until the point where the installer needs to "get the time from a network time server."  It is hanging at 87%, and won't budge.

I am installing this on a laptop, so it was relying on a secured wireless connection. BUT then I remembered to connect the ethernet cable while it was still at 87% and check if the installer would detect a wired connection -- but to no avail.

Is there anything I can do right now -- while it is still at 87% -- to bypass this "getting the time from a network time server" segment of the installation?

Any suggestions? All are appreciated!

Thank you in advance.
DN

---

### Post by Pumalite on 2008-07-14
Cancel installation. Get wired, reboot and start again.

---

### Post by deltoids on 2008-07-14
> **Pumalite said:**
> Cancel installation. Get wired, reboot and start again.

Thank you! :)

I took your suggestion, but now I have a new problem. I was setting up my laptop so that I could have a double-booting system -- windows xp and Ubuntu.

Now, I'm not entirely sure if I canceled the installation correctly. There was no "cancel" button, so I just ended up minimizing the window, pressing control+alt+delete a couple of times, and shutting off the machine... Taking out the installation CD, etc.

Then of course, I connected the ethernet to the laptop, plopped in the Ubuntu CD, and started again -- only to find that there was no Microsoft Windows XP label in the partition. In the first Guided Partition label, there are two Ubuntus -- the one I supposedly installed, and the one I'm about to install. 

Does that make sense? :(


Oh dear, please help!

---

### Post by Pumalite on 2008-07-14
Boot your Live CD and post a screenshot of Gparted. You can also get Super Grub and boot XP to see if it's OK. It will also fix it's MBR for you. Then you can continue with the installation.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by deltoids on 2008-07-14
> **Pumalite said:**
> Boot your Live CD and post a screenshot of Gparted. You can also get Super Grub and boot XP to see if it's OK. It will also fix it's MBR for you. Then you can continue with the installation.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

Thank, I really appreciate your help. I'm not entirely sure how I would take a screenshot of Gparted. 

During my first Ubuntu installation try, I wanted half my 30gig drive for XP, and the other half for Ubuntu. During my second try, Gparted wanted me to split 15 gigs between two different Ubuntu installations. But it did recognize the full 30gigs, because the second guided option was to install Ubuntu on one 30 gig "partition."   So, given that, I think the problem must have been that I didn't completely cancel the first Ubuntu installation.

I tried booting Windows XP, and it did go through a file check system prompt, and then worked ok. I needed to reboot again because Windows was alerting me that it had installed new devices.

I made a Super Grub disk, and reboot the laptop. It would boot windows fine, but if I tried to boot Linux, it would eventually come to "error: file not found."

Well, I'm going to try to install Ubuntu again now, and see if perhaps all I was missing was a couple of Windows reboots.

Thank you so much for your help. I'll take all the suggestions I can get, and if all else fails, I'll just end up taking the second option on Gparted which is to basically have Ubuntu OS installed on the entire hard-drive, partition-free.

---

### Post by Pumalite on 2008-07-14
Get Gparted Live CD and 'shrink' the XP partition to whatever you want. In the new 'free space' make 3 'New' partitions:
10 GB fot '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Then install, go Manual and use the already prepared partitions.
Right click on XP and choose 'resize' from the menu.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
You can take a screenshot with the camera icon.

---

### Post by deltoids on 2008-07-20
Thank you, with your help I resolved everything without issue.  

I went into GParted Live CD, but there were already two partitions, one for Windows, and one for Ubuntu. I shrunk the apparently installed Ubuntu to a tiny little partition after trying to format it, and ended in installing Ubuntu again! 

But no problem, whatever I did, it's booting up just fine now. Soon there will be no Windows on my laptop, I just wanted to install Ubuntu before I tried backing up all my files on XP through my incredibly slow USB 1.0 connection.

Thanks Pumalite, forever grateful for your help!

DN




> **Pumalite said:**
> Get Gparted Live CD and 'shrink' the XP partition to whatever you want. In the new 'free space' make 3 'New' partitions:
10 GB fot '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Then install, go Manual and use the already prepared partitions.
Right click on XP and choose 'resize' from the menu.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
You can take a screenshot with the camera icon.

---

### Post by Pumalite on 2008-07-20
You are welcome. Good luck!

---

