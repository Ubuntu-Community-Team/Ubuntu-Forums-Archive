---
title: "Ubuntu and windows will not boot..."
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by chicagorush1 on 2008-02-08
Ok i have a big problem. I've looked up how to install ubuntu and windows vista on the same hard drive but every time i try to install it won't let me load any operating system except windows xp.

Heres my setup.

I have 3 hard drives.

1 has windows xp on it.
1 has windows vista 64-bit ultimate on it.
1 is just used to store files.

The 1 with windows vista on it is the one i have that is the master disk. That is the one i use to load up windows without having a boot menu pop up during the boot. If i wanted to switch to windows xp i go into the boot options under the bios menu to select my windows xp hard drive.

When i go to install ubuntu it won't let me load up anything. If i go to load up ubuntu it comes up with error 22 or 15 i think that says no partition. If i go to try and load up windows vista under the grub menu it loads windows xp. If i go to load up windows xp it loads windows xp. I don't know what to do. I've tried every possible way to get it to boot up but it won't let me at all. I've looked at all the tutorials and stuff but it won't work. If you guys need more information let me know so i can boot up ubuntu and show you the /dev/hd1 or whatever it is you need. But i don't know what else to do.

If anyone can help that would be great. Thanks

---

### Post by Cresho on 2008-02-08
also, your bios sequence, your ata100 pci cards, your serial ata, also boot sequence, as well as prioritized devices has alot to do with this.  ohh yeah boot flags on partitions.  are your hardrives using cable select or did you change your jumpers to be picky at what is a slave and master?

I keep it simple.  2x 500gb disks on sata o and sata 1 no raid.  I install windows xp on second drive and remove the first drive cable to prevent windows from medling with it.  install ubuntu on primary drive and prevent ubuntu from medling with windows partition.  after boot up, its just fine.

KEEP IT SIMPLE!  What's your hardware configuration?

---

### Post by chicagorush1 on 2008-02-08
well see the thing is, i don't want to lose any information from my windows xp disk becuase i have a lot on there and i wanted it to stay somewhat opposite from vista.

---

### Post by confused57 on 2008-02-08
> **chicagorush1 said:**
> Ok i have a big problem. I've looked up how to install ubuntu and windows vista on the same hard drive but every time i try to install it won't let me load any operating system except windows xp.

Heres my setup.

I have 3 hard drives.

1 has windows xp on it.
1 has windows vista 64-bit ultimate on it.
1 is just used to store files.

The 1 with windows vista on it is the one i have that is the master disk. That is the one i use to load up windows without having a boot menu pop up during the boot. If i wanted to switch to windows xp i go into the boot options under the bios menu to select my windows xp hard drive.

When i go to install ubuntu it won't let me load up anything. If i go to load up ubuntu it comes up with error 22 or 15 i think that says no partition. If i go to try and load up windows vista under the grub menu it loads windows xp. If i go to load up windows xp it loads windows xp. I don't know what to do. I've tried every possible way to get it to boot up but it won't let me at all. I've looked at all the tutorials and stuff but it won't work. If you guys need more information let me know so i can boot up ubuntu and show you the /dev/hd1 or whatever it is you need. But i don't know what else to do.

If anyone can help that would be great. Thanks
Since you have 3 hard drives, your grub root entry will be (hd0,x), (hd1,x), or (hd2,x)...try the 2 that aren't being used in the line with root in your grub boot entry.
Here's something you might try to boot into Ubuntu...boot your pc, make sure your Ubuntu entry is highlighted, press "e", then highlight the line with root, press "e" again, then change root to something different than is listed, e.g.  (hd0,x) to (hd1,x), press "enter", then "b" to boot...x means leave this value as it is.  You shouldn't have to try this more than 2x, hopefully the first will work...this change is temporary, but can be made permanent.

Check back in if this works.

---

### Post by chicagorush1 on 2008-02-13
ok if i do that, how do i make it permanent? i haven't tried it yet since i kinda gave up but i will try it now.

also heres the order i have my hard drives set up on my motherboard.


SATA 1: Windows Vista / Ubuntu
SATA 2: Windows XP
SATA 3: Storage Drive

But when i start up the computer and after it shows the bios screen it shows my IRQ and drives. Well it shows my Windows Vista / Ubuntu as SATA 2 and my XP and Storage as SATA 1. Let me check on that first before you guys consider that since i'm at school at this moment while typing this up. I have to see what it really says but i think its something like that.

---

