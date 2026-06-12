---
title: "Trying to install ubuntu mini"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by Chris1965 on 2016-03-18
First off I am no where near new to computers. I was a MS Windows power user and decided to change to linux. While playing with the ubuntu mini offering for some time trying to learn from the ground up persay then all the sudden I couldn't get it to install anymore and that has been my last 25+ tries. So I decided to finally ask on the forum if any changes have been made as of late to the iso or possibly if it had became corrupt. I did wipe the drives and downloaded a fresh iso each time I tried a reinstall which I either burned to a cdrw or used unetbootin to install to usb to install from there. The part that always fails now is the section just before installing grub boot loader where a program window shows and says I had broken files. I even tried going back to the beginning of the step after it failed and trying just the step and it failed again.  I know it was working because I installed ubuntu mini 6+ times just before it started failing.

I was downloading the **14.04 lts 64 bit** on a Dell M6400 workstation laptop fully loaded.

Any help would be greatly appreciated,

---

### Post by Bucky Ball on 2016-03-18
Welcome. If the first six installs worked I'd stick with the ISO and the software you used used to make the USB for them rather than downloading a new ISO each time. If it worked once, the ISO is fine. There shouldn't be any need to wipe the drives everytime either. All you need is free space on a partition somewhere and choose 'Something Else' at the partitioning section of the install and install to the free space.

From what you're saying seems to be specific to grub installing. Could you install [bootrepair]("https://help.ubuntu.com/community/Boot-Repair") and just run the bootinfo script (not any repair) and post the link it spits out here, please? 

Have you tried another USB? Are you trying to install to the same place on the same drive each time? Are you trying to install the grub to sda and it's throwing that error?

As for the USB, you should wipe that and create one FAT32 on it prior to using UNetbootin. Not doing so can cause issues. I use Gparted (it's default in the live session) to rewrite the partition table on the USB which kills the partitions then I create one fat32 partition then UNetbootin it.

---

### Post by Chris1965 on 2016-03-19
Well I tried again this morning twice and it failed yet again. I do have more specifics now though ........ the program that shows up saying broken files is called aptitude 0.6.8.2. At the bottem in red it says "unable to resolve dependencies". I have no idea of what to do besides for clicking "ok" and rerunning **Select and Install software** step again and it also always fails. I did an "u" update and that worked fine then I typed in "g" for download and install and an error comes up "No Solution to these dependency problems exists!"  I know I am doing nothing different then I did when I got it to install the first times I got it to install. 

I used imgburn to burn the iso to cd in windows and wipe my hard drive after each failure to insure a fresh uncorrupted drive and let ubuntu mini partition and format the drive during setup. It just doesn't make any sense.

---

### Post by Bucky Ball on 2016-03-19
This is happening during install??? Don't update during install and don't tick the box to download third-party stuff during install. Even thought the options are there it is advised you don't use them. You can do ALL of that once installed. Updating and downloading third-party stuff during install is known to sometimes cause issues for some people on some computers. You probably fit into that category.

---

### Post by Chris1965 on 2016-03-21
Well I finally figured out what was messing me up after watching some youtube video's. Come to find out when you install a minimal install you don't tick the box for minimal, you don't tick anything and continue on. I would have never guessed ubuntu still had many bugs in it as many followers that use it. Another issue that I've ran into since is that once the computer goes into sleep it won't wake back up even after unticking sleep and hibernation settings in power settings. I am running a minimal xfce4 and perhaps there are other requirements needed to fix the issue.

---

### Post by ian-weisser on 2016-03-21
> **Chris1965 said:**
> Come to find out when you install a minimal install you don't tick the box for minimal, you don't tick anything and continue on. I would have never guessed ubuntu still had many bugs in it as many followers that use it

Your patch to fix that issue is welcome.

---

### Post by Bucky Ball on 2016-03-21
Unless you want a machine profile which you select at tasksel, why would you select one for a mini install? Sorry didn't mention that earlier, but yes, don't choose a machine profile.

Please post a new thread for your suspend issues, it will greatly improve your chances as this thread has nothing to do with it and has been solved, but food for thought: what power management app have you installed? xfce powermanager? Another? Put it all in the new post and good luck. :)

(And make sure to say this is a minimal install. :))

---

