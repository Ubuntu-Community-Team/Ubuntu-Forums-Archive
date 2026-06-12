---
title: "no way i manage to install one linux distro (RAID involved?)"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by koda on 2006-06-07
hi everybody!
i'm really breaking my brain trying to solve my problem but i can't find a solution, also because my linux and hardware experience is very little!
I wanted to install the newest ubuntu distro on one quite moder deskop computer (bought on past december) and so i waited for the 6.06 version to come out!:rolleyes: 

my hard disk configuration is a little weird:
i have a
- RAID-1 74Gb WC
- Legacy 250 Gb Maxor
both connected to an Adaptec Sata Controller (model 2820SA)
-RAID-5 750Gb WC (4 disks total)
connected to the mainboard and managed by the Intel Matrix Storage Manager

When i was installing Dapper, at the partition step, i noticed something weird about how it mapped the harddrives:
the ones connected to the Adapec Controller were fine, but the other 4 connected directly to the mainboard were not and were managed as 4 different hard drives (sdc,sdd,sde,sdf) with unreadable partion table! :confused: 
Oh well i said, and i went on as i was installing and partitioning a the Legacy drive (and in fact I had no problems doing that)8-) 
The trouble arose when the base system was being installed as at one point
RED SCREEN :-k  "unable to install linux-386" and if pressed "continue" the whole installation program would stop and i had to reboot! :( 
I tried this several times with kubuntu 6.06 x86 and amd64 but they stopped there! Only once i managed not to mount the cd and make it download the packets but it would stop afterwards while installing the xserver-xorg :???: (and that's even more weird since i have an NVidia that usually doesn't trouble linux) I even tried to install Ubuntu 5.10 and upgrade to Dapper afterwards: same problem all the way!
So after that i wondered why I could not install any Ubuntu distro and believing it was a software fault i tried to put several other distros (SUSE, Slackware, Gentoo) but NONE of them could configure the RAID-5 and complete installation as they always blocked somewhere claiming that they could not "read" (suse) or "unpack" (gentoo) some packages!](*,) 

I have no idea how to proceed! I don't even know if it's the raid's fault or if there's something wrong with my pc! I managed to install Kubuntu 6.06 on a normal Laptop (ide disks) and had not a single problem!!!
Another oddity is that my bios sees the raid 5 array so why does the installation not see that? is there some software/hardware controller i should do something about?

Am I missing something? Do you know what I could do??? :cry: 
thanks for the help!!!
Koda

---

### Post by koda on 2006-06-09
hi all!
I've managed somehow to get kubuntu on one disc!
I had to change the Legacy drive into "Volume" one!
However i cannot boot it, even if i installed it in the first MBR!

Now Grub didn't even load, but a warning of Window saying that it cannot boot normally and offers some choices (net boot, normal boot, prompt boot etc)
I also tried in rescue mode "grub-install" but it won't work on any device saying "Unknown Partition Table Signatue" (which is something i don't understand...)
always in the rescue mode i even started the graphic server so the final problem is just that nasty booting thing!!!

Do you have any ideas????
Please HEEELP[-o< [-o< [-o< I'm desperate :cry:
Koda

---

### Post by koda on 2006-06-11
hi all!
I have somehow managed to install ubuntu on my machine!
I had to remove the RAID1 array from the controller so that only the 250GB was detected and correctly set up the MBR!

For the time being this solution works for me (as i don't have to access the files on that array so often) but it is likely that in the future i'll format that RAID1 array to put the system files only!
one oddity is that when i wanted to partition that array it returned me an error... however now i don't have time to tnink about it as i'm busy trying solutions to the fact that my soundblaster xfi is not supported :/

bye!
Koda

---

