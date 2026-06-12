---
title: "Upgraded to feisty, computer will not boot"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by hooked on 2007-03-17
Hello All,
   Yesterday I upgraded from edgy to feisty using sudo apt-get dist-upgrade. At that point I left the computer because projected download time was over 4 hours. I came back when it was finished and restarted my computer and now it will not boot. The load bar at the first screen gets about 2/3 of the way across and then switches to text. Some of the output messages are:
init:/etc/event.d/tty3:13: Unknown stanza
udevd[2016]: add_to_rules:invalid BUS operation
udevd[2016]: add_to_rules:invalid rule '/etc/udev/rules.d/51-udev.rules:1

All action halts after:
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006)

I've also tried booting in recovery mode with essentially the same results, except that it stops at mapping the keyboard.

Please help!! I love this OS.

---

### Post by bulldog on 2007-03-17
Yes, well you made a little mistake by "upgrading" to Feisty.
You have to know it's not even a Beta version,so you shouldn't use it on a machine which is important to you.

It's a wise thing to install Feisty next to your Edgy or Dapper,so in case of trouble you can fall back on your stable system.
Feisty is mend for users who know what they have installed and who are able to resolve some problems on their own.

Can you tell me which kernel version you have?

---

### Post by hooked on 2007-03-17
Yeah, I made a stupid mistake and I'm regretting it now, believe me. My kernel version is 2.6.17-11-generic

---

### Post by hooked on 2007-03-17
Sorry about the delay in response time, by the way. I rarely post in the forums and in the past it's taken hours for a reply. I didn't expect such a quick answer :)

---

### Post by bulldog on 2007-03-17
I have Feisty running as well and I have to inform you that the latest kernel is:Linux AMD64 2.6.20-11-generic #2 SMP Thu Mar 15 08:03:07 UTC 2007 i686 GNU/Linux

Maybe if you try a dist-upgrade in your console?
```
sudo aptitude update && sudo aptitude dist-upgrade
```

You can try to boot in recovery-mode to upgrade your install.

---

### Post by hooked on 2007-03-17
I've tried recovery mode, but to no effect. Also, the way I "installed" feisty was by doing a dist-upgrade, plus I switched my main repositories from 'edgy' to 'feisty.' I've considered reinstalling ubuntu in another partition and then moving my important files over from the old. The problem with that is that I don't know if that's possible, and I'm sort of shaky on partitions and wouldn't know how to do it in gparted while still keeping old data intact.

---

### Post by bulldog on 2007-03-17
Do you have a separate /home partition?
If not you can mount your partition with the live cd and copy your important data to another place.
As long as you don't touch the partition with your data you can create a new partition,but there's always a slight chance it goes wrong.
But that's a risk I wanna take,just read carefully and look twice at what you're gonna do,and if you're absolutely sure it's okay,then hit the apply button.

I can tell you that Feisty is running very well btw,so you can consider a fresh install from scratch.
You can download the ISO and install it on your existing partitions if you want.

I have to warn you,it's running fine now,but it can be broken on next update,if you can't afford it to happen,I should reinstall Edgy again,and wait with the update till it's release.

---

### Post by hooked on 2007-03-17
Thanks for the help, I'll do that, I think.

---

