---
title: "Install issues Dell Latitude C640"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by _Ty_ on 2007-04-24
Ok. first attempt at installing Ubuntu. I told myself I would wait for Feisty and I managed to do that just barely. I have this Dell Lat C640 I use for work, mainly for troubleshooting network issues. I thought it would make a good machine to play with Ubuntu on. I downloaded the Desktop CD and burned it, checked the disc for errors, etc. I then attempted booting the cd so that I could install.

I rebooted machine with disc in drive - bios recognized the live cd and booted from it. I got the boot options menu for Ubuntu and chose to "Start or Install Ubuntu." This began the boot process for the live cd.

First error I received was:
> Buffer I/0 error on device fd0; logical block 0

After about a minute's pause, the boot process continued. Then:
> intel_rng: FWH not detected

Another pause, then continued. The GUI began to load and immediately I got:
> there was an error starting the gnome setting daemon.

some things, such as themes, sounds, or background settings may not work correctly.

the last error message was:

did not receive a reply. possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

gnome will still try to restart the settings daemon next time you log in.

This remained until the Gnome desktop had loaded and I could click cancel on the error box. This took several minutes. From here the system was up but very very slow. For example, I clicked on the applications menu, and about 2 minutes later it opened. I let the system be for a while thinking maybe it just needed to catch up. Never happened. The system remained very slow. Finally I decided to try clicking on the Install icon. Once the system registered that I had done that, the screen went black and the hdd and cdrom read/wrote incessantly for 20 minutes. Finally i got a few white and beige squares on the screen that looked like windows that failed to render. This stayed for many minutes until I forced a reboot and tried again. I tried again with the Start and Install Ubuntu option, and twice under the Video Safe Mode. They all had the same result. 

Basically I ended up not being able to even successfully boot the live cd so that I could attempt an install. Does this mean that my system will not intall/run Ubuntu successfully, or is there something I can do. 

Sorry for the lengthy post, but if I know anything, it's that to get real help you have to be thorough in your explanation. Below are my system specs as well.

Dell Latitude C640
Intel P4 Mobile 2.0Ghz
256 Mb DDR SDRAM
ATI Radeon Mobility 7500
20Gb HDD
Samsung CD ROM
3Com Ethernet NIC
Intel PRO Wireless 2200BG Wireless NIC
Cirrus Login AC'97 Audio Controller

Any help at all would, of course, be greatly appreciated.

---

### Post by _Ty_ on 2007-04-25
I have managed to find bug reports for each of my error messages:
[URL="https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95857"]Buffer I/O error on device fd0, l
ogical block 0 Error[/URL]

[intel_rng: FWH not detected Error]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982")

[Gnome Settings Daemon Error]("https://bugs.launchpad.net/ubuntu/+bug/94027")

They all include a fix, or at least a workaround, but the problem is, that they all relate to an install, not booting the live CD. I can't even get the Live CD to run well enough to install in the first place.

Any thoughts? Anyone? Even if it's just to tell me I am screwed, let me know.

---

### Post by gamx on 2007-04-25
Same problem here. It seems to have to do with the combo DVD/CDRW. For some reason the liveCD does not recognize it properlyy. Take a look at this page

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

---

### Post by _Ty_ on 2007-04-25
Thanks gamx, that seems to be related to the bug I posted about earlier. The kernel is looking for the non-existant Floppy drive and pauses for a few minutes before moving on. Seems that once you manage to install, it goes away. Now if I could just get it to install...

---

### Post by eduardomartin71 on 2007-05-03
Hello all,

I have the very same computer c640 and I upgraded from edgy, and every thing looked fine, but i have this minor issues: I also get the error for the floppy, which in this kind of laptop is replaceable with the dvd/cdrw unit, but does not wait any time, just reports the error. Another thing is that my drives now are /dev/sdx instead /dev/hda, and i am completely unable to mount the dvd/cdrw drive though the gnomebaker works!!! just for writting!!! (reports an error dealing with dma which is normal because is now a scsi drive instead ide ;P).

Try downloading edgy and installing, is much more stable and i have not seen any thing so new in feisty to upgrade; i am going back. This is turning much alike vista I dare to compare!!!

Have a nice day, see you with edgy next time!!!

Thanks all!!!

---

### Post by eduardomartin71 on 2007-05-03
Hello All, again.

no edgy backwards!!! y restarted the computer with the 2.6.17-10 kernel using grub, which is the kernel that worked fine in edgy.

Every thing is working great now. So my response: this has to do with the new compilation of the kernel the boys from canonical have done...

If some one has played with the 2.6.20 kernel, post the solution... pleeeease!!!

thaks to every one!!

---

### Post by gamx on 2007-05-05
I solved the problem using the alternate install CD. No graphical install but other than that it works great.

---

### Post by Anomali on 2007-05-07
I tried to install Feisty (Ubuntu 7.04) on our Dell Latitude C640.

The hardware is almost identical to -Ty-'s and my error report would be almost identical too so I'll skip that.

I set the BIOS to boot from CD first.  It did.  I was presented with the Ubuntu menu and selected the first option.  The desktop loaded and was usable.  I then tried to install... a while later the screen went blank and I dozed off... 2 hours later there was a non-flashing white cursor on the screen and nothing would respond so I turned it off and gave up for the night.

This morning I turned off the BIOS's power saving functions so that the screen wouldn't go blank and repeated the process.  The desktop was loaded and I tried to install... 5 hours later I have a half loaded "Welcome" screen (step 1 of 7 for installation) and nothing has happened since.

I have Feisty on my desktop and it seems to be working fine.

EDIT>
I then downloaded Dapper (Ubuntu 6.06) and installed it successfully on the laptop, thinking that it was Edgy (Ubuntu 6.10)!
Now I'm downloading the Final Release of Edgy and that is what I will try to put on the Dell C640 for the time being.
<EDIT

I would have downloaded the "alternate CD" for Feisty but didn't want:
[a] to wait 1 hour 20 mins
[b] to find myself in a text based installer being asked a too-technical question and getting stuck
[c] to eventually manage to install but finding it unstable and being unable to change to Edgy

Perhaps someone can dispel my [b] and [c] concerns and then I'll put up with [a] :)

---

### Post by gamx on 2007-05-09
Regarding your concerns, the text installation is not that difficult and after that the system is stable, so far. I have been using it for a week just fine. The only issue is that compiz does not work well.

---

### Post by _Ty_ on 2007-05-09
I am looking at going the Alternate CD route as well. I downloaded and burned it already. I then realized that on a 20Gb drive in this laptop, I only have 8Gb free. I am ordering a new, bigger drive before I attempt an install. I'll keep you posted. Thanks for all the posts guys. It really is helpful.

---

### Post by DoubleR on 2007-07-01
I installed 7.10 tribe1 Ubuntu on my dell laptop c640 last night and was successful.. I had to install twice.  I think the first install had some trouble because of the way I partitioned.  I am dual booting and the original 20gig drive is getting crowded.  Second attempt went very well.  You can find tribe1 here,  [http://www.ubuntu.com/testing/tribe1](http://www.ubuntu.com/testing/tribe1)

---

