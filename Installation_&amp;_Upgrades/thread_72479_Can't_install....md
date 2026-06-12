---
title: "Can't install..."
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by groundpounder on 2005-10-06
I posted this on the Warty forum a couple days ago, but didn't get any responses.  Today, I downloaded the Hoary install cd and tried that.  Unfortunately, it met with the exact same results.
I had Warty installed on this old Compaq (ugh) 5070. I made a wrong turn somewhere while setting it up and decided I needed to start over (apparently a wrong choice). Now, the install doesn't work. I've tried it 2 times with Warty, once with Suse, and now once with Hoary, with the exact same results. It goes through all the installation with no problem to the point where it ejects the install cd and reboots. During reboot, it grts to the point where it says "Starting Ubuntu...", then it says:
> pivot_root: No such file or directory
/sbin/init: 429: cannot open dev/console: No such file
Kernel panic: Attempted to kill init!
With Suse, the error messaage wasn't identical, but the key words in that last line were there, and it happened at approx the same point in the boot process.  Anyone have any ideas?

---

### Post by Miguel on 2005-10-06
Hello groundpounder,

What are the hardware specs of your compaq (HD, processor, ram, graphics card,...)? Second, a new version of Ubuntu is due out next week. It will probably have improved hardware detection, so, if time is not too important, you could wait.

Anyway, have you tried a Live CD? If yes, was that successfull? which distro?

However, I will be sincere. I don't know why that kernel panic appears. I only know that killing init is not a good thing.

---

### Post by groundpounder on 2005-10-06
4.3 GB HDD, 350 MHz K6-2, 96MB PC100 ram, graphics card is on the mobo (description says "2X AGP Graphics with Direct3D"), a 56k modem, and Netgear ethernet card.  

What gets me is that I had Warty successfully installed a couple days ago.  I figured I had screwed something up because I went to edit the sources.list file and it said "gedit: command not found" or something like that (I had already used gedit a couple times).  I figured I had screwed something up, and it wouldn't be too bad to just start over.  Boy was I wrong!

---

### Post by groundpounder on 2005-10-06
Ok, I booted it up successfully with a Warty live cd.  Running really slow though due to only having 96MB of memory.

---

### Post by Miguel on 2005-10-07
If  you managed to run the live CD with 96Mb of ram (it supposedly requires 128) then it should work. Either warty or hoary. Now, that kernel panic puzzles me even more, because the live CD works.

I'm just bumping this, because I am feeling useless apart from encouraging you to try again (with any linux distro).

Anyway, if you are installing Ubuntu again and have a good network, try doing a "server" install. This should install only the minimum. No graphics, no gedit, just a terminal. The editor in this case is nano (in case you want to touch anything). And XFce or IceWM should work much better than gnome.

---

