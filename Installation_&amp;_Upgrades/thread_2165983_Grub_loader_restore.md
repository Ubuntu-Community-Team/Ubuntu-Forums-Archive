---
title: "Grub loader restore"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by nabla2 on 2013-08-07
Hi, I have ubuntu and vista dual booted on my laptop and my vista partition has recently become corrupt, and nothing I have tried thus far has been able to save it. 

After using a windows cd to rebuild the Master Boot Record, I no longer get the grub loader at startup, and am unable to access my ubuntu partition. On top of that, my windows CD no longer boots to the repair screen, and tools like gparted crash everytime I try a repair of the vista partition from the bootable CD.

Anyhow, my laptop is currently unusable without being able to access the ubuntu partition at least, especially since I now want to try and use that to recover data from the vista partition to an external harddrive, so I can just then reformat it.

I've searched and tried the following that everyone has said should work, but it hasnt worked for me:

Booted from Ubuntu (12.04) live CD, and clicked "try ubuntu" to run it from the disk.

Opened a terminal at typed:

```

sudo grub
find /boot/grub/stage1

```

which gave me the response "(hd0,4)". Then I typed:

```

root (hd0,4)
setup (hd0,4)
quit

```

Then closed the terminal and rebooted, removing the ubuntu CD in the process. after several attempts, and also after trying using "su" and setting a password instead of just "sudo" (Not knowing if it would make a difference), it still just boots straight into the broken vista partition, which doesnt get past "windows is loading files".

Is there anything else I can try to get GRUB back again and get into my ubuntu partition?

Cheers

---

### Post by nabla2 on 2013-08-07
Never mind I figured out what I was doing wrong....it should have been "setup (hd0)" not "setup (hd0,4)"

---

