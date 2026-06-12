---
title: "PC uses PCLinuxOS's vice Feisty's grub menu.lst"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by kpictjl on 2007-07-01
I had Feisty installed on /dev/hda1 and all was well.  I then installed PCLinuxOS 2007 on /dev/hda3.  The install seemed fine but when I booted the grub menu didn't have an Feisty option.  I was able to edit the /dev/hda3/boot/grub/menu.lst to add an entry for Feisty.   So, it all works fine,   I just don't like the way I'm setup now.  Nor do I understand what happened.:confused:

How do I tell my machine to use the hda1 grub menu instead of the hda3 menu?

---

### Post by logos34 on 2007-07-01
How about adding an entry for the PCLinuxOS kernel to hda1 menu.lst and restoring grub so that it points to /boot/grub on hda1?

[B]sudo grub
root (hd0,0)
setup (hd0)
quit[/B]

This will overwrite the grub deposited by pclinuxos.

---

### Post by kpictjl on 2007-07-01
That sound like the solution...before I do it though, is there a setting or something in grub that I can look at to see that which partition it's pointing at?   I guess I'm a little fuzzy on where the MBR ends and grub starts (I get that this comment might be non-sensical).  

What starts grub?  Is there a line in the MBR or something?

---

### Post by mikewhatever on 2007-07-01
I strongly recommend the following pages 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

The command you were looking for is:
> sudo grub
grub> find /boot/grub/stage1

The output would show where grub is installed.

---

### Post by logos34 on 2007-07-01
If I understand your initial post correctly, you installed pclinuxos second and it overwrote ubuntu's grub with its own (but didn't detect/add entry for ubuntu for some reason).  So grub stage1 is on the MBR and currently pointing to the config files on hda3.  (You can read more about how grub works  [here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")).  But when you reinstall grub it will point to the menu.lst on hda1.

---

### Post by kpictjl on 2007-07-01
> **mikewhatever said:**
> 
The command you were looking for is:
Quote:
sudo grub
grub> find /boot/grub/stage1
The output would show where grub is installed.

When I run the find command I get this.   I haven't read those links yet...I will before I ask any more q's.

```
grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,2)

```

---

### Post by mikewhatever on 2007-07-01
The output says that grub is installed on two partitions. (hd0,0)=/dev/sda1, and (hd0,2)=/dev/sda3. A small part of grub is installed to the MBR and points to stage1 on one of the partitions. Which one? You can set it up with commands posted by logos34. It seems that currently, the boot loader from pclinux partition is used. If you set it to use the one on hda1, you'd have to manually add an entry for pclinux to its menu. It really makes no difference if hda1 or hda3 is used, so no reason to bother changing it.
You are welcome with more questions, however, the guides by Herman I posted above are so good, I do not think many can explain things better.

---

### Post by kpictjl on 2007-07-01
Thank you mikewhatever and logos34.  I'm good to go now.  Educated enough to be dangerous but g2g.

I edited /hda1/boot/grub/menu.lst with the entries for PCLinuxOS.  I copied the appropriate text from /hda3/boot/grub/menu.lst and pasted it in the hda1/menu.lst after the automagic list.  Therefore I think the PCLinuxOS entries will not change.  I also hashed out the hiddenmenu option on hda1/menu.lst so I see the grub menu everytime I boot.

Then I executed the commands posted by logo34 to load hda1's stage 1 into the MBR.

I rebooted and was able to arrow down to the PCLinuxOS entry on grub's menu and boot to PCLinux OS.
I rebooted again and allowed grub to automatically boot to Ubuntu after the timer expired.

Thanks again for the help.

---

