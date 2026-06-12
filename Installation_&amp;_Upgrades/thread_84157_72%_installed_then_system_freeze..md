---
title: "72% installed then system freeze."
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by Stereotypical Rage on 2005-10-30
I've installed Warty, Hoary and Breezy Preview on this machine (Long time, newbie Ubuntu user) with no problem installing (DWL-520+ doesn't work in Preview, it did in Hoary.)

I'm booting off a Sony DVD R/W drive. The install gets to 72% and then freezes with acpi_support showing on the graphical screen. So, I reboot, it loads up the gdm, I enter my user name, then it shoves me out of the password screen, back to the installer screen. Then it freezes at 5%.

 I reboot into recovery mode and run 'dpkg --configure -a'. It goes about it's business and finishes installing Ubuntu. ( I do notice that acpi_support does get configure here, but not on the graphical installer.)Brings me back to the bash prompt. I type "gdm' and can go about my business. 

Although my screen res sucks, I reconfigure X to get the max res. (1280 x 1024) and restart the whole thing. I go to run Breezy normally. (Not hitting escape to get the grub menu) It loads, then does the same thing when I get to the password screen. (Dumps me to the installer again), so restart in recovery mode and can go about my business as usual.

What's going on here? Did I miss something? Can I disable acpi_support before install?

Anyone else get this error?

Specs: 
AMD64 3200+ (754) using Breezy-i386 (AMD64 support isn't quite up there yet.)
512 MB DDR PC 3200
Chaintech nForce3-250 Mobo
500+ GBs of HDD space.
Chaintech GeForce FX5200 128 MB

---

### Post by jvictor on 2005-10-31
I'd say the DVD drive is the villian, when u reach the first screen in install where u select the language, type Ctl+Alt+F2 , and enable DMA using hdparm... I use AMD 64 and find it damn stable. Ive the same DVD-RW , and lost quite of my hair trying installing from it coz , the install used to hang @ 13 % :-D

---

### Post by Beggar on 2005-10-31
I actually had my first attempt at an install freeze at 71%, I just restarted the computer, tried again and everything worked fine.

---

### Post by aleyah on 2005-11-26
[QUOTE=Stereotypical Rage]I've installed Warty, Hoary and Breezy Preview on this machine (Long time, newbie Ubuntu user) with no problem installing (DWL-520+ doesn't work in Preview, it did in Hoary.)

I'm booting off a Sony DVD R/W drive. The install gets to 72% and then freezes with acpi_support showing on the graphical screen. So, I reboot, it loads up the gdm, I enter my user name, then it shoves me out of the password screen, back to the installer screen. Then it freezes at 5%.

 I reboot into recovery mode and run 'dpkg --configure -a'. It goes about it's business and finishes installing Ubuntu. ( I do notice that acpi_support does get configure here, but not on the graphical installer.)Brings me back to the bash prompt. I type "gdm' and can go about my business. 

Although my screen res sucks, I reconfigure X to get the max res. (1280 x 1024) and restart the whole thing. I go to run Breezy normally. (Not hitting escape to get the grub menu) It loads, then does the same thing when I get to the password screen. (Dumps me to the installer again), so restart in recovery mode and can go about my business as usual.

What's going on here? Did I miss something? Can I disable acpi_support before install?

Anyone else get this error?

Specs: 
AMD64 3200+ (754) using Breezy-i386 (AMD64 support isn't quite up there yet.)
512 MB DDR PC 3200
Chaintech nForce3-250 Mobo
500+ GBs of HDD space.
Chaintech GeForce FX5200 128 MB[/QUOTE]

i have exactly the same problem.
Specs:
AMD sempron 3400+ (754) (64bit enabled)
Gigabyte nforce3 - 250

did you solve it?

---

### Post by aleyah on 2005-11-26
[QUOTE=jvictor]I'd say the DVD drive is the villian, when u reach the first screen in install where u select the language, type Ctl+Alt+F2 , and enable DMA using hdparm... I use AMD 64 and find it damn stable. Ive the same DVD-RW , and lost quite of my hair trying installing from it coz , the install used to hang @ 13 % :-D[/QUOTE]
it is not a DVD drive problem: the freeze happens when all the installation files are yet copied in the hd (the final configuration stage...).

---

### Post by bwog on 2005-11-26
@SterotypicalRage: To answer one of your questions: yes, you can disable acpi support before install.

Edit: this is a 3 weeks old post hijacked by users with similar problems :)

---

### Post by gigamike on 2005-11-30
I just posted a thread with the same issue - guess I should have looked in here first.

I'm using the same motherboard, and a DVD drive.
Mine freezes at 73 - 74%

I've had issues with other distro's being unstable too.

---

### Post by haiku on 2005-12-01
I have the same issue.  I've had previous versions of ubuntu installed on this machine, just decided to upgrade for xorg and better fglrx.

I too have the chaintech vnf3-250, this must be the problem.

The install gets to about 71-72% then freezes up.  When i reboot i get a blue screen complaining about package errors, and the system immediately locks up.  I've tried installing 4 or 5 times now tonight.  I also tried installing the breezy prerelease candidate from a disc I had lying around, same issue.

If anyone has figured out how to get this to work I would be very grateful for the solution.

---

### Post by butter on 2005-12-01
Try the netinstall with the mini.iso located here, [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso)
Burn to cd and boot.  Worked on a computer i had with a similar problem on Hoary.

---

### Post by GrayB on 2005-12-01
Hmmm...  I seem to be following gigamike around here withthe same issue.  However, I don't have a DVD drive and I have been able to login, although without bennefit of a desktop.  From the prompt I've tried manually running the update, but it craps out and tells me I need to run 'dpkg --configure -a'.  Doing so yields yet another failure in which it turns out I don't have superuser access, which is required to complete the process.  Oy.

Now, I'm new to Ubuntu and I've come to hate Windows enough to slog through this.  At this point in my non-installation, I figure I need to log in as a default administrator ('root'?), since I can only create a user level account during install.  Is there a default password to go with it, or am I barking(mad) up the wrong tree?  Any ideas?

---

### Post by haiku on 2005-12-01
[QUOTE=GrayB]Hmmm...  I seem to be following gigamike around here withthe same issue.  However, I don't have a DVD drive and I have been able to login, although without bennefit of a desktop.  From the prompt I've tried manually running the update, but it craps out and tells me I need to run 'dpkg --configure -a'.  Doing so yields yet another failure in which it turns out I don't have superuser access, which is required to complete the process.  Oy.

Now, I'm new to Ubuntu and I've come to hate Windows enough to slog through this.  At this point in my non-installation, I figure I need to log in as a default administrator ('root'?), since I can only create a user level account during install.  Is there a default password to go with it, or am I barking(mad) up the wrong tree?  Any ideas?[/QUOTE]

Hey greyB.  You should be able to run a command as an administrator by prefixing the command with sudo (super user do)try:

sudo dpkg --configure -a

it will prompt you for a password that should just be your user password.

---

### Post by taygan on 2006-02-05
try enabling dma on your dvd drive (you can do it from the expert install.. when it gets to cdrom parameters type in -d1 or, you can get to the console (alt-f2?) during the beginning of the regular setup and type sudo hdparm -d1 /dev/hdd (or whatever /dev your dvd drive is, and then alt-f?? to get back)  

It's been months since I had this problem, sorry I forgot the exact details.

Then make sure you permanently enable DMA after you're installed:

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

### Post by Adamal on 2006-02-18
I am also having this issue.  I have the chaintech vnf3-250 mobo.  I've gotten around the install by doing a server install.  I have also been able to install dapper.  However after I get everything installed I get random lockups when using Gnome and/or KDE.  Sometimes it will lockup at the kdm or gdm.  Any solutions.  BTW other linux distros work just fine

---

### Post by aleyah on 2006-02-19
try removing the Powernowd package: everything is working fine without it...

---

### Post by Adamal on 2006-02-19
[QUOTE=aleyah]try removing the Powernowd package: everything is working fine without it...[/QUOTE]
That seems to have done it.  Has this been logged as a bug?

---

### Post by aleyah on 2006-02-19
[QUOTE=Adamal]That seems to have done it.  Has this been logged as a bug?[/QUOTE]
don't know..
i've found powernowd was the problem by doing a server installation, followed by a one to one package installation :P

---

### Post by andlinux21 on 2006-02-22
I finally got it to install I ended up doing a server install and then from the command line doing

sudo apt-get install ubuntu-desktop

works fine now wonder why it hangs up the regular way though...



AMD64 3200+ (754) using Breezy-i386

---

