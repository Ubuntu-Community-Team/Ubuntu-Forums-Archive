---
title: "Ubuntu 10.04 freezes on splash screen after upgrade"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by vfargenta on 2010-06-02
Hi all,

At a research lab where I work there is a server who recently was running with Ubuntu 7.10 (it was pretty late), and I decided to upgrade it to the newest version available.So I did the recommended: successive upgrades from one version to the next one until I reached the 10.04 distribution.

All went fine until the upgrade from 9.04 to 9.10. This upgrade itself succeed smoothly, but when I rebooted the machine, X display wasn't working: it was showing a blank screen with a X cursor. The text terminals were all working however; it was just the graphic terminal that was with this problem.

Then I thought "Oh, this shouldn't be a big problem, I'll upgrade to 10.04 and this problem will disappear". But I was mistaken, because the problem persists.
I saw in the logs a message saying "registered panic notifier" from inteldrmfb frame buffer, and I searched googled and I found something about grub2 config file. I hadn't this config file because I hadn't grub2, so I installed it as well.

Now, after the machine boots,  it appears that purple splash screen with the dots switching colors normally for a few seconds, and then all the five dots become red and the screen freezes at this point. I can't switch to terminals, the screen remains unchanged.

The server has onboard graphics provided by Intel chipset 82Q35. Would this be a driver issue? I can ssh to the machine from any other machine and operate normally.

Please note that the problem occurred after the upgrade from 9.04 to 10.04 and on the next upgrade persisted (after the first upgrade I could switch to text terminals - just the X was that blank screen with X cursor; now it seems to be totally a graphical problem, because ctrl-alt-del works ok).

All packages are updated and upgraded, there isn't any dependency unmet. All the necessary gnome/gdm packages are installed as well.

I don't know what log I should post; I don't know much about Linux maintenance. If you ask me, I post whatever log you may find helpful.

I am very grateful for all the time you spend and help you give. This community-based effort really makes the world a better place.


Regards,
Vinícius

---

### Post by phrodod on 2010-11-09
I had this problem as well.  I was able to fix it by restarting in "safe mode" (I don't remember the Ubuntu term for it, but it should be something like safe mode, console mode, or some such thing -- typically, it's just below the usual bootup on the Grub menu).  Once it started, I had a number of choices including "dpkg".  This choice fixes packages that have been downloaded or that were missed when you upgraded.  Once I let that fix my computer, I was able to continue booting.  I had to do an immediate reboot before I could do anything else, and then when I selected the regular Ubuntu partition, everything booted normally.

Good luck!

---

### Post by phrodod on 2010-11-09
The "dpkg" option took about 2 hours, then required a reboot.  After that, my system started working correctly again.

---

