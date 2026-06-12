---
title: "Ubuntu 11.04 and RAID-0: no GRUB install"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by biuro74 on 2011-07-23
Hi,

I was using Ubuntu 10.10 beta, and then 10.10 full (by upgrade) and then 11.04 (by upgrade) with NO ISSUES. My system is multiboot with 3 windowses and 4 linuxes in total, so I've got 2 bootmenus (MBR & EBR), but 1st bootmenu came from Ubuntu and included all linuxes and entry for next (Windows specific) bootmenu. I use fake RAID-0.

The problem isI've changed a platform and at the end of Ubuntu install process I've noticed GRUB couldn't be installed at all - no matter which drive to install I wrote in textbox (/dev/dm-0 or /dev/mapper/isw_dhicbhefcg_MyRaid)... 

When I try to install GRUB2 manually from LiveCD, I get an error message:
```

ubuntu@ubuntu:~$ sudo grub-setup /dev/mapper/isw_dhicbhefcg_MyRaid
grub-setup: error: cannot stat `aufs'.
```In the meanwhile I look for solution, of course.

I've heard new Ubuntu has got some issues with GRUB (my revision is 1.99~rc1-13ubuntu3), was it in my case ?
How to reinstall GRUB2 on my RAID-0  ?

Any help appreciated.

---

### Post by Quackers on 2011-07-23
Is the raid array recognised in gparted?

---

### Post by biuro74 on 2011-07-23
> **Quackers said:**
> Is the raid array recognised in gparted?

Sure, if it wasn't, I wouldn't know it's name (/dev/mapper/isw_dhic... etc). So it's recognised & mounted.

---

### Post by Quackers on 2011-07-23
Hmm, mine wasn't recognised by gparted until I installed kpartx in 11.04.
What suggested that you run grub-setup in the terminal?
I would have thought that you would need to mount your root partition first (and boot partition, if appropriate) and then run grub-install as detailed in the thread below (not specifically for raid though), or possibly by chroot.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by biuro74 on 2011-07-23
Thanks.

I've seen this or similar link before and I've tried to follow, but I got "device already mounted" message, so I gave up.

But now I've changed few things - in LiveCD it's enough to mount a device via menu (Places/Removable Media) and it appears in /media directory - so I've chrooted directly to that point, with no /mnt/temp.
Secondly, my installation was not complete, as I suppose, so I had to do:
dpkg --configure -a

And at the end, GRUB installer accepted isw/dhicbfefcg_MyRaid device (maybe it's about prefix - there was no '/dev/mapper' this time ?).

Since now, GRUB2 is installed and works. Now it's time to deep configuration :-/

---

### Post by Quackers on 2011-07-23
That's a result :-)

---

