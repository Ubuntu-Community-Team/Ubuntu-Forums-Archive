---
title: "Trouble partitioning in fresh install of 8.04.1-desktop"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Mark Santesson on 2008-10-17
Hi all, please help me kick the Windows habit... if I don't figure this out I'm going to have to go back to Win2K. I'm trying to install Ubuntu desktop version 8.04.1 from a DVD, but it keeps kicking me back to the partition screen (step 4). I have a single 160 GB hard drive, and I just reflashed my BIOS. I was able to get it to install the server version, but desktop isn't working for me.

I've tried every different partition scheme that seems to make sense, such as:
[LIST]
[*]Guided, use whole disk
[*]Manual: 4 GB /boot, 150 /, 6 GB swap.
[*]Manual: 1 GB /boot, 155 /, 4 GB swap.
[*]Manual: 156 GB /, 4 GB swap
[/LIST]

... some many times over. I get to the end and it seems to try to start, but just returns me to the partition step. If I select Guided, it doesn't really guide, it just goes on to the next step. Usually when I have a /boot partition it warns me that it needs to be "at least this big" but never tells me how big that is.

The really weird thing is that it worked for the server edition. I had to reflash my BIOS, and put /boot first with 4 GB, but it worked.

Thanks for considering my problem. Any ideas?

Thanks,
Mark

---

### Post by Partyboi2 on 2008-10-18
What are your system specs eg. make, model, onboard ram etc...

---

### Post by Mark Santesson on 2008-10-18
> **Partyboi2 said:**
> What are your system specs eg. make, model, onboard ram etc...

It is pretty generic stuff, no make or model. My motherboard is an ASUS CUSL2. It has 512 MB ram. The hard drive is a WD 160 GB EIDE. I have a DVD plugged in that I borrowed from another computer. It has an Elsa Gladiac video card (nvidia chipset). I have an intel CPU but I'm not sure which one. I assembled it about seven years ago and the only thing new in it are the hard drive (the last one just failed, so it is a good opportunity to set it up with a new OS), and the wireless networking card.

Thanks for the help,
Mark

---

### Post by Neo_The_User on 2008-10-18
> **Mark Santesson said:**
> It is pretty generic stuff, no make or model. My motherboard is an ASUS CUSL2. It has 512 MB ram. The hard drive is a WD 160 GB EIDE. I have a DVD plugged in that I borrowed from another computer. It has an Elsa Gladiac video card (nvidia chipset). I have an intel CPU but I'm not sure which one. I assembled it about seven years ago and the only thing new in it are the hard drive (the last one just failed, so it is a good opportunity to set it up with a new OS), and the wireless networking card.

Thanks for the help,
Mark

How I fixed it...

Popped in slackware 12.1, deleted all my partitions. ALL. Worked. I tried installing gentoo and messed up so it completely messed up my HDD. The install CD couldn't even detect my filesystems. Burning slackware or OpenSUSE and popping those in should solve your problem. You'd of coarse have to install openSUSE if you fixed it using openSUSE so I recommend formatting the drive using fdisk or something and delete all possible partitions.

---

### Post by Partyboi2 on 2008-10-18
> **Mark Santesson said:**
> It is pretty generic stuff, no make or model. My motherboard is an ASUS CUSL2. It has 512 MB ram. The hard drive is a WD 160 GB EIDE. I have a DVD plugged in that I borrowed from another computer. It has an Elsa Gladiac video card (nvidia chipset). I have an intel CPU but I'm not sure which one. I assembled it about seven years ago and the only thing new in it are the hard drive (the last one just failed, so it is a good opportunity to set it up with a new OS), and the wireless networking card.

Thanks for the help,
Mark
Have you checked the cd for defects (one of the options at the main menu) As neo_the_user as mentioned formatting the hard drive with [[COLOR=Blue]dban[/COLOR]]("http://www.dban.org/") could be an option. With 512mb ram you should only need about 1 gig for swap. 
You mentioned that you can install the server version ok, you can always install the ubuntu desktop from the terminal by
```
sudo apt-get install  ubuntu-desktop
```

---

### Post by Mark Santesson on 2008-10-20
> **Partyboi2 said:**
> Have you checked the cd for defects (one of the options at the main menu) As neo_the_user as mentioned formatting the hard drive with [[COLOR=Blue]dban[/COLOR]]("http://www.dban.org/") could be an option. With 512mb ram you should only need about 1 gig for swap. 
You mentioned that you can install the server version ok, you can always install the ubuntu desktop from the terminal by
```
sudo apt-get install  ubuntu-desktop
```

I did recently run that option and it checked out ok.

I've been toying around with parted and fdisk. After I use the guided option it leaves the partition in the following state, note the start of the second and third partitions:
```

Number Start  End   Size   Type     Filesystem Flags
1      32.2KB 158GB 158GB  primary
2      158GB  160GB 1546MB extended
5      158GB  160GB 1546MB logical  linux-swap

```
Which could just be linux offering to let another OS reuse the swap space, but looks suspicious to me.


Interesting regarding installing the desktop from the server mode! That looks like what I might need.

I've set up the partitions with fdisk and I'm redoing the installer to see if it will work with those settings. If not, I'll reinstall the server and use your suggestion.


Thanks!
Mark

---

