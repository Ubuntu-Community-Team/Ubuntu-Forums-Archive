---
title: "Linux newb in need. Ubuntu install issues."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Kevsta100 on 2007-11-03
Hi I'm in dire need of some help here!
(please)

OK lemme just set the scene.
I have recently decided Vista is not for me, more to the point I want out of the whole windows OS environment.

A friend recommended Ubuntu, with the promise of everything I was missing in vista being in there:-

So i downloaded Ubuntu 7.10 via the main link, I had issues with that so used the alternative link.

So now I have a bootable installation disk.

At the grub install splash screen for Ubuntu i choose option one to installl.
It fails due to Kernel timer sync, surfice to say I rebooted, retried (after a lil googling)
I now press F6 and enter the command noapic pci=nommconf

all goes well for about 3 seconds.

My next error is 

VFS unable to mount root fs on unknown-block (104,1)
A google search of this gives me alot of options I find unclear of how to work with.

Having only the bland experience of a week on SUSE linux I feel somewhat stumped by how difficult installing whats boasted as the best PC OS available.

I consulted with a friend who seems to be somewhat of a OS guru, he did a quick google and informed me due to the fact I have a non OEM machine I have many a problem ahead of me and should seek help here. (lol too much for him? XD)

My specs are as follows.

Gigabyte M59SLI S5 motherboard
AMD x2 dualcore 5200+ cpu
4GB of DDR2 667 RAM
Nvidia 7900GS 512MB PCIE graphics card
500GB SATA HDD
Dual 19" TFT monitors.

I have restored my original bios
I have restored my bootloader to the XP legacy bootloader
I have enabled fail safe defaults to the bios.

I also have 4 partitions on my HDD, the forth being labelled U and is 41GB large which I plan to install Ubuntu to.

I would much appreciate someone(s) experienced in Ubuntu to kinda hold my hand and help me out till I can find my feet on the Linux Kernel.

I also plan to convert my brothers anf friends to linux so hope to be able to learn enough to get by being a teacher as well as a pupil. :p

If this is a lil too much info am sorry, if its not enough please let me know.
Thanks.
Kev.

---

### Post by Pumalite on 2007-11-03
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Kevsta100 on 2007-11-03
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

OK ty mate for pointing me in the right direction.
I will make note of all the fixes and methods I use and post them here for all to see.

Again ty for the speedy reply.

---

### Post by Pumalite on 2007-11-03
You are welcome. Good luck.

---

### Post by Kevsta100 on 2007-11-03
0.94800 VFS:cannot open root device "<null>" or unknown-block (104,1)
0.94800 Please append a correct "root=" boot option ; here are the available partions:
0.94800 Kernel panic- not syncing :VFS :unable to mount root fs on unknown-block(104,1)

Thats my problem or atleast what the install is telling me.

It would probs be alot easier for me to do something about it if I understood half of what it either means or what the solution  stated in the google results mean.

I think this is my 5th day of trying to install this now, its breaking my spirits.
Maybe Linux is not for me, I have extremely little coding experience and the simplest tasks in linux seem to need a qualified IT specialist to work out.

 I just wanted something better than windows 


:mad::confused::(

---

### Post by Pumalite on 2007-11-03
If you are using the Live CD, try the Alternate CD.

---

### Post by Kevsta100 on 2007-11-03
The live CD wouldn't work for me, it took a day and many CD-Rs to figure out that one :(

So its the alternative one am using.

I googling but all am getting is page after page of similar problems with no actual clear and decisive solution. 

I spent a short time using SUSE and that installed right away with no problems.
I did however think is was a joke of an OS which is why i gave vista a go.

So all in all my Linux experiences so far are not good.

---

### Post by Pumalite on 2007-11-03
Disconnect everything connected to your computer. May try to disable floppy in BIOS too.

---

### Post by Kevsta100 on 2007-11-03
This is what I did to get my first Kubuntu boot.
I'm not entirely sure if all or part of it did it so I'll be full.

I booted up the pc with the fresh Kubuntu iso I just downloaded and burned to disk using magiciso.

I went to bios and disabled floppy support.

I then bootmenu'd and set to boot from cdrom.

I then did an F6 bootand used the command noapic acpi=off pci=nommconf

I then fianally sees the Kubuntu loading screen.

I'm pretty sure it was a live session I have had as I never actually installed it

---

### Post by Pumalite on 2007-11-03
If that works, you can later change it in your menu.lst, in the Ubuntu entry.

---

