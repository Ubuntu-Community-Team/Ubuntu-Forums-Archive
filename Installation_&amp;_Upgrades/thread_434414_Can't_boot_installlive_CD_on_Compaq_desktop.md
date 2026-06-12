---
title: "Can't boot install/live CD on Compaq desktop"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Mazorca Jones on 2007-05-05
Hi, I'm trying to install ubuntu (Feisty) on my desktop, and i'm able to reach the menu where i choose to boot ubuntu or boot from hard disk. Once the loading progress bar finishes i get screenfulls of "squashfs" errors and then a "Loading please wait... Permision denied" screen. Won't ever actually finish loading. This happens regardless of normal or safe graphics mode. However, the disc works fine on my laptop and other computers, though when I check it for errors it reports 5 of them (tried burning several more copies and still get 5 errors on check). I tried using Kubuntu (Feisty) and get the same booting errors/crash. I also tried an official (from Ship It) ubuntu 6.06 cd and it just crashes after the progress bar as well (doesn't give me an error though, just black screen). Any ideas?

---

### Post by tgalati4 on 2007-05-05
Could be a old or dirty CD reader on the Compaq.  Sometimes using compressed air through the loading tray can clean the reading lens.  Not too much, just short bursts.

Also make sure the machine is clean inside, reseating memory, network and video cards and ribbon cables.  If this is an older machine (3 to 5 years old), I would stick with 6.06.1 first as it is stable and you will get 95% of Ubuntu goodness.  

We need the specifics of the machine:

Processor and speed (PII or greater, 300 MHz or greater)
Memory (256 MB or greater, or 128 MB and a swap partition
4 GB harddisk at least.

Compaq's tend to be generic hardware wise so Ubuntu should be able to run on it without problems.  Unless you have hardware problem.

---

### Post by Mazorca Jones on 2007-05-06
Thanks for responding, It's not that old of a desktop, about a year and a half. It's a [COLOR="Red"][Compaq Presario SR14280M]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00306966&lc=en&jumpid=reg_R1002_USEN")[/COLOR]. This has an Athlon 64 3300+ 2.4GHz, The motherboard is an Asus K8S-LA. I upgraded the RAM to 1.5GB  DDR PC3200, and the hard drive to a SATA 320GB 7200rpm. The cd-rom in question is an HP 16x DVD(+/-)R/RW DL LightScribe drive. The case inside is pretty clean. It had an other CD-ROM preinstalled but I disconnected it. The graphics chip is an integrated SiS 760 Mirage 2 with 64MB of shared video memory.

---

### Post by nonlinear on 2007-05-06
i'm having problems like this too (usually a crc error while loading initrd.gz, althouhg some commands allow me to get further).  i've been working on this install for like 30 hours now and so far have only been able to install using the WABI installer, but still trying to work on a real install.  my next step is to try the dapper release and see if that works.

i've done a ton of reading, and it seems that there are A LOT of people having errors at this point in boot/install.  the problems and solutions seem to vary, so it's important to try and identify exactly what is happening and where you are getting the error.  you might want to try the dapper release really quick and just see what happens...

It would be useful if there was some way to log the progess of each boot, does anyone know how to do this?

---

### Post by Neuralgia on 2007-05-06
In my case, I downloaded the Feisty install CD.

Checked for erros, none.

I checked my .iso, no errors

Installed perfectly in my Desktop.

When installing in my laptop, I get an error saying the xorg.conf file ins not configured correctly, with a blue screen.

Tried to use the "alternative" CD, and the same thing.

I could install perfectly my Edgy (6.10), why is Feisty giving me errors

-*-*-*-*-*-*-*-

My systems:

Desktop> Dell Dimension 8400

Laptop > Dell Inspiron 6400

---

### Post by Mazorca Jones on 2007-05-06
OK the error messages are such:> 
[   105.482628] SQUASHFS error: sb_bread failed reading block 0x4ff1x
[   105.482655] SQUASHFS error: Unable to read page, block 12fb8ce, size 772c
[   105.483988] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd, srclength65536, avail_in 1017, avail_out 5818               [fail]
(note some of these numbers and characters might not be specifically accurate as they were hard to make out since my inefficient way of logging these incredibly fast screens of errors was with my digital camera,)
I get about 4 screenfulls of those errors with the numbers varying with each one. Then it shows> 
Starting HP Linux Printing and Imaging System
Autoloader.pm did not return a true value at /usr/lib/perl/5.0/POSIX.pm line 7.
BEGIN failled --compilation aborted at /usr/lib/perl/5.0/POSIX.pm  line7
Compilation failed in require at /usr/sbin/dpkg-statoverride lin3.
BEGIN failed --compilation aborted at /usr/sbin/dpkg-statoverride line 3
You are missing a dpkg-statoverride on /var/run/hplip. Fix it otherwise you risk silent breakage on upgrades. If you have no idea what to do, just reinstall hplip and it will fix itself.
dumpkeycodes: No such device [OK]
Starting powernowd [OK]
Starting bluetooth services
*more of those errors from the first quote*

Then deffered  execution scheduler atd and periodic command scheduler croad load fine.
then:
> 
Enabling additional executable binary formats binfnt-support {note not sure on accuracy there}
Autoloader.pm did not return a true value at /usr/lib/perl5.0POSIX.pm line 7
BEGIN failed--compilation aborted at /ur/lib/perl/5.0/POSIX.om line 7
Compilation failed in require at /usr/sbin/update-binfnts line 22
BEGIN failed--compilation aborted at /usr/sbin/update-binfnts line 22
[fail]
Loading, please wait...
Permission denied {repeat  for about 10 times}

And then it just stays there... Can you make sense of this?

---

### Post by Xyhthyx on 2007-05-10
All I can think of is trying the alternate CD and hope it will work.

---

### Post by tgalati4 on 2007-05-10
I have a similar Lightscribe drive.  It was a replacement for a wonky HP/Compaq drive that was also a little over a year old when it failed.  HP replaced it for free, but this new drive (the Lightscribe) acts up sometimes.  I have an older CD reader that I put in the machine for those situations.

Unfortunately it looks like it might be a hardware failure.  The disk(s) check out on other machines and Linux comes up with odd errors because it always expects perfect hardware.  Lately, I'm finding the quality of computer components is poor, while the new Linux distros are becoming more reliable.  Hence we have more posts such as yours.

Grab an old CD drive from another machine and try again.  Let us know how it turns out.  Don't forget to do a google search on your drive model and summarize what problems other folks are having.  You are not alone.  That's the Ubuntu spirit.

One final cheesy suggestion.  Let the disk heat up in the drive for 10 minutes before using.  Sometimes the disks expand and the newer DVD drives have trouble tracking.

---

### Post by Mazorca Jones on 2007-05-12
tgalati4's suggestion worked. I disconnected the DVD drive and instead connected a CD-ROM and it has booted and installed successfully. The only problem I'm having now is that it won't recognize the ethernet (integrated to the motherboard). Network Manager reports no network devices have been found. and Network Settings only finds the 56k modem.

---

### Post by say.xen on 2007-05-12
I have a SR1235IL desktop and everytime i try installing ubuntu it restarts.  Tried other Linux and distributions but the same problem continues. Please help me on this.

---

### Post by Mazorca Jones on 2007-05-12
I googled my motherboard and found that the onboard ethernet card is a "Realtek RTL8201CL LAN PHY Fast Ethernet LAN controller". Checked the compatible Realtek cards on the Ubuntu wiki [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek") and it's not in the list of cards (supported or not supported). I tried using a Fedora Core 6 Live CD and it did not detect it either. Tried a DreamLinux Live CD as well and the ethernet was detected but not functional. I'd hate to give up on this desktop and go back to Windows on it, so any suggestions?

---

### Post by lbthrice on 2007-05-12
tgalati4....

your 'cheesy' suggestion actually worked for me!

my dell inspiron 8000 was giving squashFS errors 4eva until I restarted approximately 4 times.  Then liveinstall feisty Kubuntu CD actually started working!
:guitar: 
I realize the definition of insanity is repeating the same behavior repeatedly and expecting a different result...apparently being crazy paid off for once. 

I suspect my disk heated up in the drive and expanded to the correct size for me to use it to install.  

I've got to stop buying the cheap CD-R's!

---

### Post by ThePickler on 2007-05-20
I am experiencing the same problem on my old Compaq Deskpro Pentium III.  

Currently Windows XP Professional is running on the machine and it runs like a dog.  I originally installed it so that I could guarantee all the drivers worked.  All that we want to do is be able to browse the Internet, e-mail and word process.

I've already tried booting to the installer with Edgy and Feisty with similar results.  I got further with Edgy but it never completely loaded the desktop and then went to a blank blinking cursor.  

I have tried swapping out the old disc drive with a newer one and even trying out the "crazy" suggestion of letting the disc heat up and expand with no luck.  I blew out all the computer innerds with compressed air and still no go after multiple attempts.  I figure if the computer can run WinXPPro it should be able to run Ubuntu no sweat. 

Do older Compaqs just not like Linux?   I am beginning to suspect it won't install any of the other distros either.

---

### Post by haze4b6 on 2007-05-21
This is a weird one for older cd drives: finalizing.

I have an old compaq (4 years or so) that would only boot off one of my Linux cds; it would just stall or fail to install any other cd, including XP. 

It was an old FC4 cd. Nothing worked except for that one cd. The installs failed at the same place on each individual cd, but not at the same place on all of them.

After a long string of coincidences, I came to realize that my burner was no longer finalising the cds it was writing. While this may be fine for every other modern cd drive, this old compaq would have none of it. So I burned Feisty Server to 2 cd's, one finalized, and one not to test my theory.

The finalized one worked.

Hope this helps.

---

### Post by haze4b6 on 2007-05-21
> **Mazorca Jones said:**
> I googled my motherboard and found that the onboard ethernet card is a "Realtek RTL8201CL LAN PHY Fast Ethernet LAN controller". Checked the compatible Realtek cards on the Ubuntu wiki [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek") and it's not in the list of cards (supported or not supported). I tried using a Fedora Core 6 Live CD and it did not detect it either. Tried a DreamLinux Live CD as well and the ethernet was detected but not functional. I'd hate to give up on this desktop and go back to Windows on it, so any suggestions?

Why not just grab a 5$ network card on ebay...solve all your problems.

---

