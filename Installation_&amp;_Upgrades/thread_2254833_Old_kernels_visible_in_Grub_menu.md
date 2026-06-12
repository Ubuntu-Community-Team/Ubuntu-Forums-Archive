---
title: "Old kernels visible in Grub menu"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by Enigma12 on 2014-11-30
Starting with an update/upgrade a month or so ago, I now have Grub appear at boot-up. Before that update/upgrade, it had never appeared. The only operating system on this computer is Lubuntu 14.04.1 LTS -- NO dual booting. I did, however, initially install Lubuntu 13.10 back in April 2014 and upgraded online a few times to get me to 14.04.1. 

If I hit the Enter key or ignore the screen, it just boots to my familiar Lubuntu log-in and desktop, so it's not a real problem. It just seems an  unnecessary addition to the boot process. 

If I down arrow to "Advanced options for Ubuntu" on the first screen, I see what I suppose are four kernals or parts of them. Since I imagine that the earlier kernals are either vulnerable or less capable, I use the most current one. If these older kernels are unneeded or unsafe, should I delete them? If so, exactly how do I do that?  

Again, this is NOT a major problem. It just seems pointless. One of the first things that impressed me about Lubuntu was the very fast boot-up (less than a minute on a 2.8 GHz computer) to full readiness and fast shut-down (7 seconds). Shut-down is still 7 seconds; I'd like to have back my quicker boot-up and remove unneeded files or kernels or whatevers(?) that should be removed. 

[ATTACH=CONFIG]258291[/ATTACH][ATTACH=CONFIG]258292[/ATTACH]

Thanks in advance for any help and advice on this.

---

### Post by Impavidus on 2014-11-30
In a default single boot install the grub menu is hidden. It is not hidden in a dual boot install and boot repair also unhides it. If you wish, you can modify /etc/default/grub to make the menu visible for a shorter time or, setting the timeout to zero, skip the menu completely. This will make it a bit harder to get to the menu if you one day need it. (You'll have to hit shift.)

Older kernels may be somewhat less secure or less capable (although it may make no difference at all on your system), but it's best to keep one old kernel at all times, so you can boot in case the latest kernel breaks. So keep 3.13.0-39 and 3.13.0-40, remove the others using the package manager. Autoremoving old packages may be all that is needed. Else, uninstall all packages with in their name one of the old version numbers.

---

### Post by oldfred on 2014-11-30
I prefer to keep 2 kernels, one current and one older one just as a backup.
And I prefer to use synaptic, if you do not have it:
sudo apt-get install synaptic

       Determine your current kernel:
uname -a

 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Other housecleaning:

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

With a single install, grub menu should not appear. It does have settings that if an issue on shutdown, it will load menu so you could use recovery mode, if needed.

Post this:

 cat /etc/default/grub

I do change my timeout to 3 from normal 10, I do not suggest 0 as then you may not be able to get into grub menu for recovery mode if needed.

GRUB_TIMEOUT=3

---

### Post by mastablasta on 2014-12-01
even if timeout is 0 it should still popup if you hold the left shift key.

and yes grub menu is no pointless as it provides an easy way to system recovery. e.g. kernel update that has gone wrong  etc.

---

### Post by mörgæs on 2014-12-01
> **Impavidus said:**
> Autoremoving old packages may be all that is needed.

Yes, a reboot and **sudo apt-get autoremove** normally does the trick. It deletes all but the latest two kernels. The command gives you a warning before the actual deletion begins so you know exactly what is going to go.

---

