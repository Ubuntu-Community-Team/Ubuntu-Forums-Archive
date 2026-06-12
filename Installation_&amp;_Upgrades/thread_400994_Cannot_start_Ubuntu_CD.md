---
title: "Cannot start Ubuntu CD"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Tridion2000 on 2007-04-04
I am trying to boot from the Ubuntu CD (version 6.10). Every time I do it starts up, brings up the Ubuntu screen, the progress bar gets to about 90% and then I get some screen corruption (a few odd lines going across the screen) and the machine hangs.

I have now tried this on 3 different PCs and all of them do the same thing. I have tried redownloading the iso and burning it again but it makes no difference.

The only thing the 3 PCs have in common are that they have a Radeon X800 gfx card. The current PC I am trying to do this on is:

Intel Core 2 Duo 2.4ghz
Asus P5B Deluxe motherboard
2GB GeIL PC2-6400C4 DDR2 Dual Channel Kit
ATI Radeon X800 256Mb
NEC 3500 DVD Writer
320Gb Samsung SATA HDD

Any ideas how to solve this? I am keen to try Ubuntu as people keep raving about it but so far it has been one massive disappointment.

---

### Post by quark_77 on 2007-04-04
Hi Tridion2000,

If all your PCs have a Radeon X800 gfx card in common, this is likely to be the problem. The reason for this is the ATI drivers for linux are proprietary and are not provided by default in Ubuntu - the default open source drivers work but not brilliantly. I'm using a ATI Mobility Radeon X1400 and my LiveCD worked but not massively smoothly - installing fglrx, the proprietary drivers, worked.

If you want to install Ubuntu I think the best way would be via the alternative installer option. This is effectively the desktop cd minus the live bit. The installer is similar, albeit console based. If you have ever installed windows, this will be familiar territory. If not, let me know I'll try to explain the steps.

This should allow you to install Ubuntu despite your graphics card. You can then try to load Ubuntu normally, which may or may not work. If not, you have the option of the recovery console. The latter is a more difficult but not impossible method, provided you have an internet connection.

Apologies, but I don't think the Edgy livecd will work - it might be worth waiting until Feisty is released as this may have been improved - the beta live cd runs better on my card (usplash - the splash screen you see when Ubuntu is loading - kills my terminals under edgy, under feisty it works fine). 

I'm not sure which option you want to go for, so let me know and I'll try to help,

Good luck,

Quark_77

---

### Post by Tridion2000 on 2007-04-04
Thanks for the reply. Judging by that, Ubuntu is not for me. I don't want to start messing around with recovery consoles and config files and all that stuff. I dont have the time, either something woks or it doesn't. I found the same problem with the Feisty beta so no improvement there.

Back to Windows I think.

---

### Post by quark_77 on 2007-04-04
Hi Tridion2000,
[COLOR="DarkRed"]
**One suggestion for you - when you run your live CD, you have the start / install ubuntu option. Press F6 or whatever option at the bottom gives you the option to change the options. You will see options like "live ro quiet splash". To this line, add nofb. Then try to load the live cd. This turns off the kernel framebuffer which might cause problems with your graphics card.**
[/COLOR]
Linux's greatest weakness in terms of desktops is hardware support. This doesn't just apply to Ubuntu but to all distributions - we don't have the same industry backing as windows.

Keep an eye on this thread, someone else may post a solution to your problem that I don't know about / haven't thought of. 
As for the recovery console - if you used MS-DOS or have ever used cmd.exe/PowerShell under windows this will be familiar territory - unlike the Windows recovery console which I have no idea how to use, the Linux one under ubuntu simply logs you in as root (administrator) lets you use the command line. You can press Ctrl-D to start the desktop at any time. I think startx does the same.

Have you ever installed windows? If so, you may have had to install graphics drivers for windows too - its just the same idea. Windows loads up in 16-bit colour and 640X480 resolution until you install graphics drivers - luckily for Windows, it's usually pre-installed. If Linux were pre-installed, a lot of problems would be solved.

Do you have any PCs available without this graphics card / friend's PCs you can at least try the LiveCD on to identify this as the problem?

If you have any questions / wish to try any of the above I'll try to help as much as I can.

Quark_77

---

### Post by Tridion2000 on 2007-04-04
I have just ordered a nVidia 7950GT gfx card not specifically to solve this problem (maybe it wont) but I was planning on upgrading anyway as the X800 is getting a bit old.

Will try again tomorrow when this is delivered. If it solves it then great. Otherwise I will try the other suggestions.

Thanks again. I appreciate the help. It's just I don't have much spare time to mess about with this stuff. I have installed Windows. It was very painless compared to this.

---

### Post by Tridion2000 on 2007-04-04
I am currently checking out Ubuntu 6.10 in VMWare. At least the Live CD boots in that. Can't get networking working but I just wanted to take a look around and see if I can be bothered trying to get this working on my PC or not.

---

### Post by Normlaure0 on 2007-04-04
Tridion,
I totally agree with you.  I got the CD on the basis that this system was 'user friendly'  Who that user is I have no idea!

My computer is now locked into Ubuntu and I cannot uninstall it to put in Windows.

I tried for two weeks to get an internet connection, then to try and upload programmes from CD's - impossible in ALL cases.

Very, very disappointed with Ubuntu - puitting it mildly.  Now facing an expensive computer shop recovery.

Begionners in particular should not go anywhere near Ubuntu - for techies and nerds may - but being neither of these I am simply fed-up and feeling totally betrayed.

Incidentally not one of my request posts was answered.  Happy amateur hour in a world of professionals.  I'm afraid Ubuntu will always stay peripheral until they get soem professionalism involved - relying on volunteers is crazy.

---

### Post by quark_77 on 2007-04-04
Hi Normlaure0,

Ubuntu is user-friendly in comparison to debian and many other versions of linux whose installers are simply beyond a lot of people - they require technical knowledge the average user doesn't have and doesn't care about. Ubuntu reduces the questions to those that are important and nothing else.

Like I said, however, hardware compatibility is a problem for linux - I have had some problems myself with ipw3945 drivers (my wireless internet) and fglrx (ati graphics - proprietary). This is not the fault of the linux/ubuntu developers but the hardware companies and to a certain extent regulations. For example, Intel cannot open-source their microcode because they are required by regulations to use certain frequency transmissions & other things besides - an open source microcode could be altered to violate these standards. Intel don't want that on their doorstep.

Obviously this causes problems - if you have the wrong microcode or it crashes you can't fix it or rebuild it for your system.

I am assuming that at the current moment in time you have just Ubuntu installed on your PC? If that is the case, you don't need to uninstall it. Reboot with the Windows CD in and run the Windows installer. You will find it pretty much the same as the Ubuntu one. Simply re-format all of the Ubuntu partitions to your own, delete them or whatever, and whack Windows back in. Sadly, you will have to install drivers from the CDs your manufacturer supplied.

How are you trying to connect to the Internet and what programs are you trying to install? If they are Windows programs, you will need a package called "Wine" and be warned not all of them will work.

I believe there is professional support available from Canonical Ltd, try the support pages at Ubuntu.com.

Good luck & hope this helps,

Quark_77

---

### Post by Tridion2000 on 2007-04-06
Swapped my graphics card to a nVidia 7950GT 512Mb and now have Ubuntu installed on my PC but not without a few headaches first. Ubuntu wouldn't recognise the ethernet controller on my Asus P5B Deluxe motherboard. Spent a day searching the net for a solution until I was all ready to give up. Then I noticed my MB had 2 ethernet ports. Tried the other one and all of a sudden I had internet access.

Before I solved that I tried out PCLinuxOS, openSUSE 10.2, Mepis 6.5 and Freespire. All of them crashed on boot up. This is why Linux will never replace Windows, it is just not up to the job.

However, I am relatively happy with my Ubuntu now. Configuring it and installing new apps is an experience in itself though ;) Not ready to delete my Windows XP partition just yet though.

Thanks for the help.

---

### Post by quark_77 on 2007-04-07
Hi Tridion2000,

Glad you had some success at last - we (my Dad & I) installed Suse 8.0 Pro a while ago and it was a bit of a nightmare... Ubuntu is easier... and even though I like linux my xp partition hasn't been removed... I still have to use it from time to time... CD writing is the current reason for keeping it.

If you ever want to go back to ATI, go to System|Administration|Synaptic Package Manager then when this loads go to Settings|Repositories and tick the box labelled proprietary drivers for devices (restricted). Then, close that window and press reload. Now search the list for linux-restricted-modules and make sure it is installed, then xorg-driver-fglrx which is the ATI driver. I don't know how well it'll support your card though - my graphics card isn't officially supported but it works anyway... strange eh?

Might be worth searching launchpad.net for bug reports see if anyone else has your problem and post your own.

I agree, hardware compatibility is the biggest barrier to linux adoption.

Enjoy Ubuntu,

Quark_77

---

