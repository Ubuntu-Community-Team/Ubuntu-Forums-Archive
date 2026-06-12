---
title: "Migrate installation to new hard drive, from direct partition to logical volume"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by kaliif2 on 2015-03-13
Hi,

I got me a new bigger hard drive and I'd like to move my existing installation from the old disk to new one without installing from scratch. The catch is that in the process I would also like to adopt lvm. I have found tutorials describing how to migrate system from one direct partition to another and from one logical volume to another but I haven't found any that help me with the case of direct partition to lvm volume. I have tried to mix the instructions but without any success, won't boot. Has anyone had any luck with this? Is it even possible?

Thanks in advance,

---

### Post by oldfred on 2015-03-13
Frankly I think reinstall would be easier, but I always suggest reinstall over copy. And I do not know LVM.
You may be able to partition in advance and rsync data & reinstall grub, with major edits to fstab.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by kaliif2 on 2015-03-17
[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), I sort of see your point but at the same time I also see a hard drive as a component not a definitive feature of the system. At least that's how it should be.

Anyway, after some struggling I managed to get it working. I installed a new fresh system on the new drive using lvm as planned, took the fstab file, then rsynced my old system to the new lvm volume, replaced the fstab and reconfigured and reinstalled grub (the step that failed before for some reason). I fully admit, this is not the most straightforward solution but (fingers crossed) seems to be working all right.

---

