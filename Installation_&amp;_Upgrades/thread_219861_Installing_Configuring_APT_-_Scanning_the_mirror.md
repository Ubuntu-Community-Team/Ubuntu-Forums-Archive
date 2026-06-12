---
title: "Installing Configuring APT - Scanning the mirror"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by Gorlist on 2006-07-20
Hi, we've been trying to install Ubuntu 6.06 Dapper 64bit on my fathers PC's but having a number of issues.

Couple of days ago, downloaded, burnt and tried to use the 64bit Live Desktop of Ubuntu - it would boot up off the CD fine, but for some reason it would randomly  freeze, even during installation forcing a reboot.  CD checked out fine.

After a number attempts we managed to get the Live Desktop installing, but for some reason would always lock at "85% " Installing Configuring apt " Scanning the mirror".

So decided to redownload Ubuntu (same version), accept as the Server Edition. First time round installed with no problems, then downloaded the Desktop using the APT command. Boot, loaded and appeared to work with no problems.

After a few hours use it then froze, very similar to the Live Desktop - after that it was just unstable with the same freezing issue.

Last effort was to download the Ubuntu 6.06 64 bit Alternative CD, but now it would crash during installation at "40% Installing Configuring apt " Scanning the mirror".

At this point we retried installing the Server Edition as it was the only one which worked to any extent - but failed surprisingly? - "40% Installing Configuring apt " Scanning the mirror".

Since then no luck, simply stops on all CD's with the above errors (CD checks have been done).

Running Duel Boot with Windows XP 64 (Ubuntu is being installed onto the second drive)

--------------------------------

3400 AMD 64
MSI K8N Neo 2 Platinum
1 Gig Crucial Ram
250 gig Western Digital SATA
350 gig Wester Digital SATA
ATI 9800 XT

--------------------------------

Regards!

---

### Post by bionnaki on 2006-07-22
I am having the exact same problem now. I am stuck on 40% of "scanning the mirrors" - no matter what.

---

### Post by taurus on 2006-07-22
> **bionnaki said:**
> I am having the exact same problem now. I am stuck on 40% of "scanning the mirrors" - no matter what.
I just answered your post!!!

---

### Post by jimmygoon on 2006-07-22
I believe this is due to the fact that the Ubuntu repos are experiencing some type of difficulties or outages... in which case you all should try unplugging your internet, installing, and then turning it back on afterwards.... that or wait a REALLY long time for it to timeout trying to reach the apt repos

---

### Post by plutonium83 on 2006-07-22
It is also possible to solve this problem during install.

If you are connected via ethernet cable, just unplug the connection.

If you are connected via wireless, go to System > Administration > Networking and disable your network card.

As a result, the installation should timeout and proceed with the rest of the install.

---

### Post by Gorlist on 2006-07-23
Ok thanks! will give it try - would this also be the cause of the random freeze? ](*,) 

Regards,

---

### Post by tim- on 2006-08-31
> **plutonium83 said:**
> It is also possible to solve this problem during install.

If you are connected via ethernet cable, just unplug the connection.

If you are connected via wireless, go to System > Administration > Networking and disable your network card.

As a result, the installation should timeout and proceed with the rest of the install.

This just happened to me while trying to install Kubuntu 6.06.1 and I found this thread, disabled my network card (unplugging the cable didn't do squat since I had it manually configured) and it timed out within 30 seconds.

Thanks alot!

---

### Post by snovak on 2008-02-29
I was having the same exact problem installing 7.10.  I just unplugged the net cable, mid-install, and it continued happily.

---

### Post by dharmajsoni on 2008-05-01
Thank You. For a newbie like me, that was a great deal of help.

---

