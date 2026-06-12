---
title: "Uninstall ubuntu dual boot vista"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by germike on 2008-02-05
After resizing vista i installed ubuntu without any problems on the free space. However after some use i decided i want to uninstall ubuntu. It would be nice if this is possible without losing the vista partition and being able to add this space to vista again.

How do i do this, and how do i get rid of Grub ? Can i just delete the partition in vista and repair the mbr with the vista dvd ? I aks here just to be sure that i do not kill vista in the process.

vista + ubuntu are on an acer laptop with 1 harddrive

You might ask why i want to delete ubuntu :

Altough i really liked the quick install and setup, i ran into many problems that are difficult to solve or are not possible at the moment :

-Wlan i got working after reading up on it and connecting to a wired lan to download the restricted driver
-Compiz desktop effects works after reading up on terminal commands and editing some very nicely hidden config file. After that the video's don't work unless i switch off the desktop effects.
-Flash did not work in firefox until i read up on that and after some more terminal command got it working
-Sound stutters in same games
-Dvd not working out of the box
-Sleep mode does not function
-Fonts are less nice to read than in vista
-startup is not faster than windows
-Not being able to swap 2 keys
-All those config files are just as bad as the registry

Of course i saw lots of pluspoints also 
-Quick and easy install with most apps already there
-Wonderfull desktop and effects (when they work)
-Thousands of apps and stuff all for free
-Secure (well people tell you it is)

I think that the biggest problem in my case is that the intel X3100 is not good supported yet. The second largest problem is that you still need the commandline way and way too often, if ubuntu wants to be the non-nerd linux they have to really concentrate on getting everything done without the commandline. Can you imagine having to type something like this windows :

Sudo gedit /usr/bin/compiz 
sudo aptitude purge xserver-xgl
sudo dpkg-reconfigure bcm43xx-fwcutter 

And still not found a way to temporary run the file browser in admin/root mode so i can search and edit config file without having to type open a terminal and start SudoGeditting ?

Anyway do not get me wrong Ubuntu is probably 90% there but the last 10% is so much hassle that it's not worth it at the moment, especially when you have a laptop like mine (and many more like it) that has a X3100 intel graphics.

Thanks for reading !

---

### Post by zvacet on 2008-02-05
Download [Gparted live CD](http://gparted.sourceforge.net/) and burn it on disc.With it you can delete Ubuntu partitions and add unallocated space to Vista.

---

### Post by Mark Phelps on 2008-02-05
To answer your Vista question -- yes.  You can delete the ubuntu partition(s) inside Vista, and then reboot using the DVD and run the Repair option to reset the MBR to what Vista expects.

I'm also multi-booting Vista and Ubuntu, but I see the tweaking in Ubuntu more as an opportunity to tweak it with much more freedom than in any version of Windows.

And, yes, the "learning curve" is a lot steeper in GNU/Linux than it is in Windows -- in terms of what you have to do to get your setup up an running and configured with various video, sound, and networking options.

But in all fairness to the Ubuntu community, with each release, more tweaking and easier setups are being added.  Just reading the difference between what you had to do back in the "old" Dapper days vs. what comes installed and ready with 7.10, show the enormous distance that Ubuntu has come in the short time.  And when you consider that a lot (if not most) of all this progress comes from a worldwide "community", not a multi-billion dollar enterprise, that is even more amazing!

But, I can understand that if you just want an solution, ready to go, "out of the gox" so to speak, then even today, Ubuntu is probably not the right solution.  There are other GNU/Linux distros that attempt to ease the shift away from Windows, most notably, PCLinuxOS (PCLOS).  If you still want to experiment with GNU/Linux, suggest you try that.

---

### Post by germike on 2008-02-05
Thanks for the help and i do appreciate the enourmous efforts that are behind the free distrubtions. I have downloaded and tried the new hardy alpha 4 live-cd and in that one the problems with compiz and the graphics card seem to be solved already.

Thanks again and i will come back as soon as the Hardy release is out in 2 months.

Ubuntu uninstalled just as painlessly as it installed !

I am certainly keeping an eye on things and be installing the next release as soon as its out. Hoping that sleep will work just as good as the x3100 support is looking. With those 2 things out of the way i can see myself looking into the other things with more confidence.

*edit* And i will checkout the pclinuxos that you mentioned thanks.

---

### Post by zvacet on 2008-02-05
Best linux distro is one that works for you.If PLOS is the one sick with it.If you decide to come back to Ubuntu you know where you can find us.Good luck!

---

