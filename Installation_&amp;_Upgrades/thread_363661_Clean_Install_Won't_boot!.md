---
title: "Clean Install Won't boot!"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by craig.sharp on 2007-02-17
Hi,  i've searched and searched and can't find a solution to my problem.  I installed a brand new 250gb hard disk and did a clean install of 6.10 Lamp Server x86 and went through everything without a hitch, i Partitioned the drive  with a 125gb Primary with a 1gb swap.  I cant get my computer to boot into linux without the cd.  Please help.

Thanks
Craig

---

### Post by meng on 2007-02-17
How far does it get when you boot from the hard drive?

---

### Post by craig.sharp on 2007-02-17
well,  it won't even boot from it,  when i try to boot, there's just a dos like cursor that just flashes,  the flashing underscore.  and it just hangs there.

---

### Post by craig.sharp on 2007-02-17
Right now i'm installing the ubuntu desktop so that maybe i can reinstall the grub boot loader.

---

### Post by craig.sharp on 2007-02-17
One thing i noticed when i was setting up my partitions was the option for "boot flaggable".

The default was no,  should i have checked yes?  i've done about 4 ubuntu installs and left that alone.  

Thanks

---

### Post by meng on 2007-02-17
Boot flag shouldn't make any difference to Linux. Windows will have a fit without it though.

---

### Post by craig.sharp on 2007-02-17
Here's where i stand so far...

After installing ubuntu desktop, i went to terminal and tried to reinstall grub,  it said it was succesfull, so i continued to restart my pc.  When i did, still nothing happened.  I downloaded and installed GAG for my boot menu. and the first time it worked just fine.  I changed out my video card to my much more powerfull geforce and when i restarted with GAG and started ubuntu,  it said that my x server failed to start.  Please someone help me.  how do i restore my x server?

Thanks
Craig

---

### Post by meng on 2007-02-17
What sort of video card do you have? Probably worth posting other system specs just in case they're relevant.

---

### Post by craig.sharp on 2007-02-17
geforce 7600 256mb
Intel Core 2 Duo 2.4 Ghz e6600
2.5 GB DDR2
250GB Hard Disk
Intel 975 Motherboard

Not sure what else you'd need.  I have a feeling it might be my mobo though.
Also, after uninstalling GAG, it'll now boot into grub, but even with my DVD at the top of the list, i cant boot from my dvd.  that just happened.  is there a way i can erase the Hard Drive from within the main terminal?

---

### Post by craig.sharp on 2007-02-17
Anybody????

---

### Post by meng on 2007-02-17
When the x-server fails to start, log in to the console with your username and password, then:
sudo dpkg-reconfigure xserver-xorg
(enter your user password when prompted, and press enter)

and make sure that the video driver selected is "nv"
you can probably go with default choices for all the other questions you'll be asked.

Then try starting the xserver again.

If that doesn't work, try
sudo dpkg-reconfigure xserver-xorg
again, but choose "vesa"

---

### Post by craig.sharp on 2007-02-17
This just in!!!!  I finally got it to work.  The downside,  I had to use the full 250 gigs for the install.  I'm assuming it has a problem with the disk not being full?????  i dunno, but i got it to work.  After trying to partition it with ubuntu install, i think when i have time, i'll erase again and partition with the windows install and make sure that all the partitions take up the entire disk.  That shouldn't be the case, but it is for some reason.  Oh well,  Got my lamp server up and running!

---

