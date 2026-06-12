---
title: "Trouble Installing Ubuntu"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by Komet on 2006-05-17
I've been trying to dual-boot XP and Ubuntu on my machine. I'm horrible at this and believed I had deleted everything on my computer for a few hours. When I tried installing ubuntu on my second harddrive, I was stuck on the step that mentioned both "configure RAID" and "configure volumetric xx." It would not let me go on and told me I needed to designate a root, but I could not find where to do this. I've tried gooogling it but have had little luck.

I realize how poorly this is written, but I am virtually clueless on the topic.

---

### Post by deadgobby on 2006-05-17
For a good video on line
[http://video.google.com/videoplay?do...11311898236&q=](http://video.google.com/videoplay?do...11311898236&q=)
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2)
[http://shots.osdir.com/slideshows/sl...se=475&slide=2](http://shots.osdir.com/slideshows/sl...se=475&slide=2)
How to at
[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)

Good luck
Gobby

---

### Post by Sef on 2006-05-17
For an excellent tutorial read this:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Komet on 2006-05-17
Thank you, I've tried going at it again, but for some reason, it isn't recognizing my second HD anymore when I boot up. I've tried moving it around a little and resetting it many times. Do you have any suggestions?

---

### Post by confused57 on 2006-05-17
Are you still able to boot into windows?  If you have 2 IDE drives, I suggest you look at the option provided by these 2 links(note advice by "lha"):

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

It's how I have my system set up and it's pretty easy to do.  When you're installing Ubuntu, are you selecting "Erase entire disk...", not LVM...

If you have access to a liveCD,  I'd recommend you try running one to see if your system hardward is compatible?

---

### Post by Komet on 2006-05-17
Let me elaborate:

The first time I tried to install linux, it recognized my 2nd HD and let me go to the setup. I was in over my head so I cancelled the installation and unplugged all the cables. Now it won't recognize my 2nd HD when I reboot. It worked earlier, but when I cancelled the installation and replugged in the cables, it quit working.

---

### Post by confused57 on 2006-05-18
Is the 2nd hard drive recognized in your bios?  Check the jumper settings for the drive, unconnect and reconnect the cables, try a different cable?  I don't what else may be causing it not to be recognized, unless there's a problem with the hd.

---

### Post by Komet on 2006-05-18
I tried to download shootmgr.dsk and burn it to a  floppy, but it did not work properly when I rebooted. This program supposedly forces my computer to load from the CD-ROM on boots. Do you know of any others that may work better for em?

---

### Post by confused57 on 2006-05-18
You may want to try running a liveCD and see what devices are detected.
Does windows detect your 2nd hd?

I'm thinking you may have selected LVM when you tried the first install, but if you did, I don't believe that would cause the drive not to be detected trying to reinstall.

---

### Post by Komet on 2006-05-18
I bought some new floppy disks today, and sbootmgr.dsk is loading when I reboot my computer. It gives me an error whenever I select CD-ROM, however. Does this work with XP? I noticed on the descriptions it only lists compatability up to NT.

---

### Post by confused57 on 2006-05-18
From your first post, it appears you booted correctly with the CD drive first; I don't think sbm will help...just check your bios boot order.

I highly recommend you try the liveCD, it doesn't install to your computer(only runs on ram memory)...you can see how your system runs Ubuntu and learn your way around the OS.  If the liveCD boots up, you know that your CD drive is the first boot device.

See this guide for burning an iso:

[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by gesho on 2006-05-19
hello guys, I am trying to migrate from Mandriva 2006 to Kubuntu 5.10. Got DVD from bittorents, 3 gigs.

I've current partition:
hd2 WinXP
hd6 ext 3 
swap 2GB

I do not need anything from ext 3 (can one format just one partition, without touching the other?), but I want to keep hd2 XP as is. Will installation from DVD do that? Any care needed?

My current bootloader under mandriva is LILO. Will installation take care of that too? Will I have XP/Kubuntu as new loading options?

---

