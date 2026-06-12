---
title: "Need help installing Ubuntu 8.04 (manually)"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by macubux on 2008-11-08
Hi guys I am a complete noob and need help installing Ubuntu 8.04.

This is my current laptop(desktop replacement) that I will be using

SAGER NP9262
intel core 2 Quad Q9550 2.83GHz
4gigs ram
2x Nvidia 9800m GTX (512mb) SLi enabled
Realtek Hi-def audio
3x 320GB 

I was trying to install Ubuntu 8.10 but kept getting 

MP_BIOS bug: 8254 timer no connected to IO-APIC

I tried the solutions  I found online such as pressing F6 and replacing the "quiet splash" ending with "no apic" but then I receive X server [fail] on the gnome display

I then tried disabling IOAPIC in bios but I dont get that option

I also tried replacing "quiet splash" with "ro single" which gets me to the recovery panel but that is all

So after hours of searching and getting same answers I decided to install an older build. I had the Ubuntu 8.04 dvd desktop with me so I decided to insert that and strangely I did not get the above message. So I decided to install this build rather than 8.10 since I cannot find a solution.

Preinstall, if you look at my specs above I have three hard drives. The first is running XP SP3 (32bit), second is running Vista 64bit and third is meant to be running Ubuntu if I can get the thing working.

I found this tutorial on youtube and its pretty good except the options I am presented are different and I think play a major role in installing Ubuntu. Here's the site

[http://www.youtube.com/watch?v=PEadYq63jjE&feature=related](http://www.youtube.com/watch?v=PEadYq63jjE&feature=related)

Following the instructions on the video, I edited and resized my third drive (320070mb) to 157987mb formated as NSTF but it is not mounted to anything. 

That's another thing, in the video the guy has all his drives show up mounted to some area but during my installation process, I see my three drives but neither are mounted to anything. Is this ok?

Anyhow, I resized the drive to 157987 and then created a new partition with 2000mb to use as swap. Finally I created my last partition (the actual one that will be running ubuntu) with the remaining available space I have and used it as ext 3 and mounted it to /

I stopped here and cancel the whole installation process since I am a bit concerned about the fact that my original drive (320070mb) and the window partitions are not mounted to anything. I wanted to know if I need to have them mounted? 

So if anyone can provide some input on what I should, I would greatly appreciated. 

Thanks

---

### Post by cariboo on 2008-11-08
If you try the alternate install cd you shouldn't have any of the problems you have run into so far, you still may have to apply the no apic option. It has a text based installer, so it doesn't need any graphics until you reboot.

You can get the alternate iso here:

[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

Jim

---

### Post by macubux on 2008-11-09
thanks for the site but even if I download and burn a copy of the alternate cd I still need to know how to partition it. I'm just concerned about mounting the drives. If someone could direct me in the right way to do this then I will be fine. Thanks for the reply though.

---

### Post by bulldog on 2008-11-09
Download the GParted live cd at,
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Boot from it and choose the right hdd to partition.
Make a 10GB / partition,format ext3
Make a 2GB swap partition format as swap
Make a /home as big as you want.
The partitions can be either logical or primary at your choice.

When you install ubuntu,choose manual partition.
Set the 10GB to format ext3,mount it as / and set bootflag on
Mount swap as swap
Mount your /home as /home and set it to format ext3 if it's empty.
Write changes to disk and proceed with the install.

---

