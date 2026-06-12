---
title: "Upgrade from mounted cd-rom"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by bluefoot on 2010-10-09
Hi. I have downloaded ubuntu RC 10.10. (or, if you're reading this tomorrow, remove "rc" it wont make any difference)

I would like to mount the image that I downloaded and update my ubuntu 10.09 trough upgrade manager.

Is that possible? It appears that the software sources tool only accepts cd-rom.

Or I can add it manually in the sources file?

---

### Post by sveterv on 2010-10-10
Yes, it is possible, but I was only doind this with ALTERNATE iso version.

1. First unmount your cdrom drive (physical one)
umount /dev/sr0
2. then mount .iso file
mount /SOMEWHERE/ubuntu-10.10-rc-alternate-i386.iso /media/cdrom0 -t iso9660 -o ro,loop
3. As I said I was doing this only with alternate version, so from this point it is only valid for that version:
hit Alt+F2 -> then type:
gksu "sh /cdrom/cdromupgrade"
and this will work for sure, as I am upgrading my Ubuntu that way from 6.06 till today.

Also there is a official document about it here:
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
(go to Alternate CD section)

---

### Post by bluefoot on 2010-10-10
> **sveterv said:**
> Yes, it is possible, but I was only doind this with ALTERNATE iso version.

1. First unmount your cdrom drive (physical one)
umount /dev/sr0
2. then mount .iso file
mount /SOMEWHERE/ubuntu-10.10-rc-alternate-i386.iso /media/cdrom0 -t iso9660 -o ro,loop
3. As I said I was doing this only with alternate version, so from this point it is only valid for that version:
hit Alt+F2 -> then type:
gksu "sh /cdrom/cdromupgrade"
and this will work for sure, as I am upgrading my Ubuntu that way from 6.06 till today.

Also there is a official document about it here:
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
(go to Alternate CD section)

nice.
so, that's the objective of this "alternate" version?

---

### Post by sveterv on 2010-10-10
Yes that is one of them. 

You can also repair your broken Ubuntu installation with that CD (broken grub, etc)  but you need bootable CD then and boot your computer with it. Also system installer is in the text mode and is a little more verbose (you can read logs on the console, so if something is going wrong you know at what point, and can find help a little faster or even try to manually set things right), asks you more questions and gives you more choices with answers :) 

It does not have bootable Ubuntu OS, I mean you can't start Ubuntu from the CD so don't expect any GUI. It's worth to have that Ubuntu version on CD just in case :)

---

### Post by bluefoot on 2010-10-10
> **sveterv said:**
> Yes that is one of them. 

You can also repair your broken Ubuntu installation with that CD (broken grub, etc)  but you need bootable CD then and boot your computer with it. Also system installer is in the text mode and is a little more verbose (you can read logs on the console, so if something is going wrong you know at what point, and can find help a little faster or even try to manually set things right), asks you more questions and gives you more choices with answers :) 

It does not have bootable Ubuntu OS, I mean you can't start Ubuntu from the CD so don't expect any GUI. It's worth to have that Ubuntu version on CD just in case :)

Great!! :) thanks.

---

### Post by abhisranjan on 2010-10-10
I tried it but a pop up window opened with the comment
I initially had lucid and i didn't try a pre release version


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I previously upgraded to 10.04 using the same method
is this causing the problem


thanking you in anticipation

---

### Post by sveterv on 2010-10-10
> **abhisranjan said:**
> I tried it but a pop up window opened with the comment


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I previously upgraded to 10.04 using the same method
is this causing the problem


thanking you in anticipation

I assume you were trying to make an upgrade from 10.04.1 to 10.10 with alternate CD method?

Well, anyway, I can't help you, simply because I don't know what is wrong. What I can tell you, is that more people have this problem, and it is known to developers as states here:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652)

What you can do more about it, is try to find help in other threads on this forum or simply watch a page from link I have showed you and maybe add some comments there, if you want or attach there log file with information about failed upgrade, it can help resolve problem faster. If other people have the same problem as you, and it is recognized by developers, it is possible it will be repaired pretty soon.

As this thread is now marked as SOLVED and you are posting there with a new problem (not related to this thread), please create a new thread in this forum about your situation, so other people with the same problem will find you much easier.

And at the end, you can try upgrading your system with other methods than one with alternate CD, it may help. I will post again link to official documentation, go there and read what are other methods:
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

---

### Post by medya on 2010-10-14
I have the same problem , hope someone could find a way for us

---

