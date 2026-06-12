---
title: "Dual boot Linux setups"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by DRF on 2006-08-07
I like to have 2 linux distributions on my desktop pc (one for serious work and one to experiment with a bit normally) the combination sometimes varies (ubuntu is always there as my main OS with a random other linux distro installed in another partition).

I'm getting a bit fed up with having to manually edit the grub entry's for the distro that was installed first and was wondering what the best or recommended way was to have 2 linux distributions share a single boot partition and each updating grub itself without having to constantly manually edit the grub menu entry's with each kernel update.

Any advice would be useful thanks,

Daniel

---

### Post by Tomosaur on 2006-08-07
If you type 'update-grub' in a terminal, grub will automatically rescan for installed operating systems and kernels and adjust its menu.lst file accordingly. Normally I would point you to the link in my sig (sorry :P), but I'm not sure whether I entirely understand the problem you're having here. Certainly it's possible to stop grub showing each and every kernel you have, but again, I don't fully understand the problem you're experiencing :/

---

### Post by DRF on 2006-08-07
I've not seen that script before I'll have to check it out thanks, however it's not quite the answer to what I was trying to ask. To give an example.

If i install ubuntu on partition 1 (complete with grub etc)
Then install kubuntu on partition 2 (again default settings let it install grub how it likes)

If I update or install a different kernel on ubuntu it will edit the menu.lst file in it's partition automatically. However since installing kubuntu grub now looks at the menu.lst present on the 2nd partition not reflecting any changes made to the first.

Ideally I would want 1 boot partition and point both linux installs to the same grub menu.lst so if ubuntu (1st partition) is updated or a new kernel is installed it appears on the menu.lst that is being used by grub without manually editing the menu.lst in the 2nd partition (kubuntu in this example).

Does this make any more sense? (then ideally I would be interested if this could also be shared with something other than ubuntu eg suse, fedora, etc)

Thanks,
Daniel

---

### Post by Tomosaur on 2006-08-08
Ah yes I understand you now. Luckily this problem should be fairly easy to fix. What you need to do is edit the menu.lst file on your 2nd partition, and make the following section point to your 1st partition:
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

```

Remember that grub counts from 0. If your partition table is like this, for example:

Partition 1 = Ubuntu
Partition 2 = Kubuntu

Then you should change the groot section of the menu.lst under your Kubuntu partition to point to hd0,0 (in other words, point it to your Ubuntu install.

You should probably also check the menu.lst file on your Ubuntu partition too, to avoid any conflict.

Hope that helps you out.

---

### Post by chakra_dude on 2006-08-09
I just got my Dapper Drake cd's from the mail. will upgrade this weekend. I'm dual-booting with Win XP :)

---

### Post by frafu on 2006-09-14
> **Tomosaur said:**
> Ah yes I understand you now. Luckily this problem should be fairly easy to fix. What you need to do is edit the menu.lst file on your 2nd partition, and make the following section point to your 1st partition:
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

```

Remember that grub counts from 0. If your partition table is like this, for example:

Partition 1 = Ubuntu
Partition 2 = Kubuntu

Then you should change the groot section of the menu.lst under your Kubuntu partition to point to hd0,0 (in other words, point it to your Ubuntu install.

You should probably also check the menu.lst file on your Ubuntu partition too, to avoid any conflict.

Hope that helps you out.


What about replacing the menu.lst file in the second partition with a symbolic link to the menu.lst file of the first partition? 

Would that work? If not, why? 

frafu

---

### Post by frafu on 2006-09-17
Hello,

I now have 2 versions of Ubuntu on two different partitions on my harddisk. Both Ubuntus have a /boot/grub folder; let us assume that the first is on hd(0,0) and the second on hd(0,1). It seems to me, that only one is used...  

Am I assuming correctly, that the mbr on the bootdisk contains a reference to a partition (for example hd(0,1) and that consequently it is always the /boot/grub from that partition (in this case hd(0,1) ) that is used? 

If my assumption is correct, what is the purpose of keeping /boot/grub on hd(0,0)?

Thanks in advance for any reply. 

frafu

---

