---
title: "Installation woes: 7.10 live cd bootup makes the machine VERY VERY slow"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by linux-sigh on 2008-02-24
All,

Am trying to convince myself that linux is not a pain in the ... to live with, but I'm loosing.

Since Ubuntu is touted as 'user friendly', am trying to install Ubuntu 7.10... but all i get is problems!

My machine:
Intel duo core, 2.4Ghz, 2GB DDR2 ram, nvidia geforce 8400GS... 

- I've burnt the desktop CD and am booting off that, chose the first option to start or install.
- It takes ages to bring up the desktop (about 30-45mins)
- Its good at this point, i can browse my machine. When i double click on 'Install to disk" icon, it prompts me for a few questions and at step 4 of 7, (choose partition), the machine is SO SLOW, i can't even click on anything! It was stuck there for 20 mins, I had to reboot.

I've used linux for years, am comfortable with linux in general, except when some installation/setup going bad, its an absolutely terrible experience.

Can't I just get a simple install cd that will setup a ubuntu desktop in text mode or without giving me the live cd experience?. I'm having to wait for 30-45 mins each time i reboot so as to get the live-cd ubuntu desktop and to start the installation.

Time spent (wasted) today:
- Try #1: booted via live cd. Really impressed when i got the desktop. (rebooted without saving settings onto a USB driver - n00bie mistake)
- Try #2: another 30-45 min wait to get the live-cd desktop, but VERY VERY slow and i couldn't even click a menu. Reboot
- Try #3: another 30-45 min wait to get the live-cd desktop, started installation, stuck at step 4 of 7. Reboot
- Try #4: going on while i register and write this

How can I just burn a ubuntu 7.10 cd/dvd, boot off that, NOT have to load live-cd experience, but just start the installation?

I earlier had fedora 8, am trying to remove that and install 7.10 on that. Lets see if i can do that today.

Sigh...

---

### Post by Pumalite on 2008-02-24
Use the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Download'

---

### Post by mrsteveman1 on 2008-02-24
You could also make a liveusb out of the livecd, it boots in about 3 minutes that way.

Copy whats on the cd to a fat32 usb stick, move everything from /isolinux to the root of the drive, rename isolinux.cfg to syslinux.cfg, and install syslinux to the drive.

---

### Post by linux-sigh on 2008-02-24
Thanks for the link, I was able to download and burn the 'alternate' CD.

When i boot off that, and start the text-installation, I get a couple of prompts for keyboard layout and lanuage after which I get a blank, blue screen with a grey line at the bottom. Nothing happens after this!!

If I hit ^C, the display is all messed up with vertical lines and I can see some text screen that has come up. I'm able to scroll up n down with the arrow key, but cannot select because i can't read what is getting highlighted! 

Tried this a few times as well, dint help!

I HAVE run text based setups before and have installed linux via boot cd's many times on the same PC. Why is ubuntu's text setup not working?

I'm again trying the live-cd to see if the install-on-disk in live-cd goes through all 7 steps. Lets see... if it doens't, I'd have wasted one full day trying to get Ubuntu, I'd have to fall back the to fedora 8 that I already had.

Sigh.... just another day with a linux setup-struggle!

---

### Post by jmate24 on 2008-02-24
Try Xubuntu 7.10 and use It's Alternate install. It Uses Less Resources and it may work if you have an older system. [HTML]http://www.xubuntu.org/[/HTML]

---

### Post by linux-sigh on 2008-02-24
Thanks for the link. 

I do have quite a fast system and I dont think the slowness was due to the limitation of my system.

I tried live-cd + install (Yet) again, and it seems to be going on ok this time. I'm 94% done with the installation. Lets see if it completes successfully.

Some of my faith in linux might get restored...

---

### Post by linux-sigh on 2008-02-26
Hi All,

I'm happy to report that I was able to install Ubuntu although it took me a long time and had to play around with a few things. 

For the benefit of others who might get into the same issues, here are the problems I faced.

- Booting from Live CD and then  'install on disk' running VERY VERY slowly.

**Solution:** There was a kernel process 'kacpid' which was taking up almost 80% of the CPU and that was making the system CRAWL, and the installation took AGES to complete (>2 hrs). In order to get rid of this, once Ubuntu was finally installed, i added a couple of parameters to the kernel when booting up. I added 'acpi=off' and 'apm=off' during boot up (in grub's menu.lst). This got rid of the high CPU usage and the desktop was very responsive.

- Problems enabling the desktop effects/compiz - problem with graphics card (EVGA nVidia geforce 8400 GS.

**Solution:** For some reason, Ubuntu did not like the card even after I used the 'Restricted driver manager'. I used to get "PCI: Failed to allocate mem resource #6:...." on boot up and the startup messages used to take a LONG time and the login screen did not come up. I removed the graphics card and restarted a couple of times. Ubuntu stabilized and only the settings for compiz etc was not yet setup. I then inserted the graphics card and rebooted. I had to once again install nvidia drivers, xgl server and reconfigure X a few times (by running sudo dpkg-reconfigure xserver-xorg).

Finally it all worked ! And I'm able to ubuntu stable, WITH the lovely compiz!

Phew, thank god my faith in linux was restored! Kudos to the Ubuntu team, this is truly an amazing distribution and very user friendly. The user experience with Ubuntu rightly fits the slogan "linux: it just works".  Although I struggled to set this up due to many hardware issues, the usability and features have really been worth the while!

Now I'd spread the word so Ubuntu (and Linux) gets popular! :)

Thanks to all that replied/read :)

Cheers!

---

