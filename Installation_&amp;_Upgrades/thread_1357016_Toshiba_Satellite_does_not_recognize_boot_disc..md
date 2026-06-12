---
title: "Toshiba Satellite does not recognize boot disc."
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Jaecyn42 on 2009-12-16
Greetings all,

   Attempting to install Ubuntu 9.10 after much frustration with Windoze.  I've hit a bit of a snag, however.

Toshiba Satellite L35-S2161 running XP SP2, Matshita DVD-RAM UJ-841S.  

First attempt, disc would not boot.  Boot priority was set properly (DVD/CD first, other stuff, HDD last).  Tried browsing the disc through Windows Explorer.  "D:\ is not accessible. Incorrect function."  This disc was burnt at the highest speed possible (47x).

Second attempt, read up on the forums a tad, reburnt iso at a slower speed (7x).  Boot priority still properly set, but disc still would not boot.  Browsing the disc revealed that it was being recognized as an audio CD with only a 1kb track on it. :confused: 

Checked both discs on my other machine (a Gateway AMD Phenom Quad Core running Vista).  Both appear to be nominal (have not attempted to boot them on the Gateway yet).

Contacted Toshiba Tech Support (my biggest mistake yet).  Was informed that my computer would ONLY boot a Windows recovery disc.  Technician said my computer must have a faulty drive and should contact the Geek Squad.  I'm pretty sure this is not the real problem.  Other retail disc function nominally.

What other options do I have?  It seems as though Toshiba has taken active measures to prevent me from using the OS of my choice.  Any suggestions?

---

### Post by spydeyrch on 2009-12-16
I would recommend downloading the .iso for the distribution that you want and also [unetbootin.]("http://unetbootin.sourceforge.net/") if you are running windows, download the windows version. Hopefully you have a usb flash drive (usb thumb drive, same thing). You will need at least a 1GB usb flash drive. you can get a 2GB from any hardware dealer for roughly $15 - $25. Good investment.
 
save any files that you have on the usb flash drive to a different location, preferably NOT your windows partition. do it to like an external drive.
 
format your usb flash drive to fat32, the entire thing.
 
run unetbootin, select your distribution from the drop down box if you have not downloaded a copy yet or if you do have an .iso file of the distro that you want, select the .iso radio button and broswe to your .iso file.
 
select the usb flash drive that you have connected as the destination and have at it! (install it)
 
This will install the .iso files to your usb flash drive. once it is done, reboot your machine with your flash drive still connected.
 
enter BIOS, make sure that you have your system boot from the usb drive first. Some systems can't do this due to age, but the majority of new systems, like around 4/5 years old and newer should be able to do it.
 
if you can boot from your usb flash drive, you should be able to boot into the ubuntu live desktop.
 
Give it a try and see if you really do like it. if so, use the installer and double click on it to start it. Have fun and post any questions/issues so we can try to help! :)
 
 
-Spydey  :guitar:

---

### Post by lisati on 2009-12-16
I'd recommend burning the disc at the SLOWEST speed possible, rather than the highest.
If you haven't already done so, it might be a good idea to look here as well: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Jaecyn42 on 2009-12-16
Thanks for the speedy replies. :)

Firstly, spydeyrch, sadly my Toshiba does not support USB booting. :(  The available boot options are: DVD/CD, FDD, LAN and HDD.

Secondly, lisati, the second burn I did (with ISO Recorder v 3 from your link) was done at the lowest speed available (7x).  

Additionally,I have since confirmed that the second burn is solid.  Popped it in the Gateway and it came right up.  Ran the disc integrity check and ran Ubuntu in live mode. The disc is definitely good.  

Any other ideas?

---

### Post by spydeyrch on 2009-12-16
When was the last time you updated your BIOS for your machine? Sometimes a newer bios will allow usb booting.
 
also, does your machine support "credit cards" (PCIMA cards)? If so, you might be able to us an external optical drive. I know that my wifes DINOSAUR laptop's optical drive is dead and that is the only way that I can get any discs to boot on the dino. Try that and the bios thing.
 
Also, try the alternate cd. it is a text isntaller, so no gui, but who knows, maybe it might posibly on a blue moon while dancing with a flamingo eating crumbcake......work :P
 
I will look around and see what else I can find. Hopefully that helps.
 
-Spydey:guitar:

---

### Post by Jaecyn42 on 2009-12-16
Ok, I fixed it.  The solution was much simpler than I anticipated.

On my desktop, I Copy/Pasta'd the contents of the disc onto my iPod in disk mode, moved and extracted the files onto the laptop and installed via Wubi.

Viola.

---

### Post by spydeyrch on 2009-12-16
Wow, a very creative way of doing it but good job!!
 
If you think that your issue has been resolved, make sure tha tyou mark it resolved.
 
-Spydey:guitar:

---

