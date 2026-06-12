---
title: "When will 14.04.1 update be available in 12.04.4LTS update manager?"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2014-07-25
The release notes state that the 14.04.1 upgrade to 12.04.x will be available "soon"? This is rather vague and as of 11:25am on July 25, 2014, I still don't see any notice in update manager that I can upgrade to 14.04.1.

---

### Post by Bucky Ball on 2014-07-25
Good timing. Should be right about now, or tomorrow. ;) There is a thread posted about it on the forums somewhere if you do a search. If you do an update and then check in Software Centre, my guess is it should be there. See here:

[http://ubuntuforums.org/showthread.php?t=2236248&highlight=upgrade+14.04.1](http://ubuntuforums.org/showthread.php?t=2236248&highlight=upgrade+14.04.1)

---

### Post by Rizlaw on 2014-07-25
Thanks Bucky Ball, but as of 12 Noon, New York time, still no notification in Update Manager or Software Centre.

---

### Post by ubfan1 on 2014-07-25
The release is probably rolled out in stages, to avoid overloading the servers.  You can "jump the line" by following the
suggestions in [http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04](http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04)

---

### Post by Bucky Ball on 2014-07-25
Yea, it will take awhile and might be a day before it gets to your mirror, perhaps.

---

### Post by Rizlaw on 2014-07-25
ubfan1,

Thanks. I was aware of that "omgubuntu" blog post and I tried it several weeks ago, but it didn't work. I also tried "sudo update-manager -p" which did work, but rebooting into 14.04 was very problematical so I simply restored my 12.04.4 image and decided to wait for the 14.04.1 release upgrade. I'm hoping this .1 upgrade will fix some of the issues I had with the 14.04 upgrade.

I'll just be patient and wait.

---

### Post by Bucky Ball on 2014-07-25
If you have installed a bunch of PPAs, disable them and try again if you want to go. That could have been the problem. If you have a pretty clean install (no third-party bits) you stand a much better chance of a problem free upgrade. Of course, a back up and clean install is the least problematic of all. 

If you have enough room on the drive why not just install 14.04 to another partition? If it goes pear-shaped you have 12.04 to fall back on. Make sure 12.04 still rules grub by installing the 14.04 grub on the 14.04 partition during install. ;)

---

### Post by kansasnoob on 2014-07-25
Canonical may delay the upgrade auto-notification due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

I didn't discover and report that bug until the 23rd so they just didn't have time to fix it. but Canonical Foundations was subscribed so they could decide what to do next.

---

### Post by Rizlaw on 2014-07-25
kansasnoob,

Thanks for that. Yes, I did install the HWE update two days ago (no problems with it). Not sure if this is the reason I'm not seeing a notification that the 14.04.1 upgrade is available. If it is the culprit, does anyone know if there is a way to uninstall the HWE update?

---

### Post by kansasnoob on 2014-07-25
> **Rizlaw said:**
> kansasnoob,

Thanks for that. Yes, I did install the HWE update two days ago (no problems with it). Not sure if this is the reason I'm not seeing a notification that the 14.04.1 upgrade is available. If it is the culprit, does anyone know if there is a way to uninstall the HWE update?

If things are working I'd suggest just waiting for Canonical to sort things out, they will sort it out :)

---

### Post by oldfred on 2014-07-25
Ubuntu 14.04.1 released
[https://lists.ubuntu.com/archives/ubuntu-announce/2014-July/000188.html](https://lists.ubuntu.com/archives/ubuntu-announce/2014-July/000188.html)
Users of Ubuntu 12.04 will soon be offered an automatic upgrade to
14.04.1 via Update Manager.

Whatever soon means.

---

### Post by parix on 2014-08-12
I've been finaly today been offered the upgrade for 14.04.1 from 12.04 LTS (without -d option). See you in some hour(s) ;-)

---

