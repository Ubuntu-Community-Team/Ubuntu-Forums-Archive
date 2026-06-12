---
title: "Cannot boot Hardy Live CD"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Mike Brennan on 2008-05-10
I think I've decided not to try to upgrade to Hardy. Some of the problems I see others posting about -- and my own problems -- have me worried. I can't afford to have downtime with my computer, right now, and I don't have any spare computers I can work with.

Nonetheless, I wanted to post about a problem I've experienced. I downloaded the Hardy Heron ISO file because I thought it may be safer to test drive it and then install from the live CD rather than try the update manager. I'm new to Ubuntu; I just bought a Dell with 7.10 pre-installed on it a couple of months ago.

Anyway, the download of the ISO (ubuntu-8.04-desktop-i386.iso) went fine. I used md5sum to check the MD5 hash and it checked fine. I burned it to a CD using Brasero, which went fine. When I try to boot from it, though, it starts to boot OK, I even get a screen with the Ubuntu logo and it shows a progress meter with an orange bar moving back and forth. Then it drops into the "ash" shell. After a few moments, all sorts of errors start appearing. I thought it may be the CD (even though the MD5 hashes check fine), so I burned a 2nd CD, making sure to select the slowest speed. This one produced the same results. I burned a 3rd CD -- this time, not with Brasero but by right-clicking the ISO file in Nautilus and selecting "Write to CD" -- and making sure to select the slowest write speed. Same results.

I wanted to isolate the problem, so I've tried two other experiments: 

I have an official Ubuntu 7.10 distribution CD that came packaged with my Dell. I tried booting from it and it did boot, and I got the desktop. However, the panels with the menus on it were not visible, so I could not access any menus. How do I deal with a situation like that? I pressed Ctrl-Alt-F1 to get a terminal window to reboot.

So I could boot from a live CD -- except for the problem with no visible panels (a screen resolution issue perhaps?). So I decided one more experiment: I downloaded the 7.10 ISO file and burned it to CD to see if I can boot from a CD I burned myself. It booted just like the distribution CD -- i.e. booted fine to the desktop, though with no visible panels/menus.

So what's going on here? Clearly, there is an issue when I boot a 7.10 live CD that I can't see the panels/menus. I'd like to know what's going on there and what I can do in a situation like that. But I *can boot* from a 7.10 live CD -- including one I burn myself. However, the Hardy Heron live CD won't boot at all -- it drops into the "ash" shell -- so there seems to be a specific problem in Hardy Heron in this regard.

---

### Post by Patb on 2008-05-10
Mike, try again from the Hardy live CD.  When you get the initial startup menu, hit F4 while your cursor is on "Try Ubuntu without changing anything..." and select the "Safe graphics mode".  Hit return to select that mode and start Ubuntu.  If it then starts okay, the install process should be intelligent enough to properly detect your screen.

Cheers, Pat.

---

### Post by gefloros on 2008-05-10
I would to like to report that the same thing happened with me. It's a graphics card xserver issue probably. I own an ACER Aspire 1353 with Ubuntu Gutsy. The 7.10 live CD was more flexible as it contained the F4 VGA option where i could choose 1024x768 and boot properly. My laptop can only operate on this resolution. Hardy has only got "Normal" and "Safe Graphics" option but none of them works.

The bottom line is, i also cannot boot a Hardy live CD. Only manage to get a command prompt. Probably from that there should be some way to initiate xserver (startx with appropriate options maybe?) or manually edit the xorg.xconf with setings similar with those on Gutsy. 

Anyway if anyone else has found a solution or workaround I'd be happy to hear. Once again this crappy Via card responsible i think.

---

### Post by Malibyte on 2008-05-10
I have the same issue on one of my desktops using a Radeon card.  It won't give me an X desktop even when using "Safe graphics mode"; after I get to the point where I know it's "booted", I can hit Ctrl-Alt-Fx and get a CLI...but it would be nice to be able to boot into the graphics mode with the live CD.  I'd like to do an install on this machine and it won't let me do it from the "Install Ubuntu" option either.

The monitor is an Acer wide-screen LCD panel (1680x1050?) and seems to be very picky about what resolutions it will display.  Is there any way to specify a resolution at bootup?  What resolution is it trying to use natively?  Looking at xorg.conf isn't very helpful.  :-/

Edit:  Plugged in another monitor and had the same issue...so it's not the monitor but the ATI card.  Any solutions?  BTW, this same live CD booted to a GUI just fine on another box.

Thanks
Bob

---

### Post by Mike Brennan on 2008-05-10
> **Patb said:**
> Mike, try again from the Hardy live CD.  When you get the initial startup menu, hit F4 while your cursor is on "Try Ubuntu without changing anything..." and select the "Safe graphics mode".  Hit return to select that mode and start Ubuntu.  If it then starts okay, the install process should be intelligent enough to properly detect your screen.

Thanks for the response. Unfortunately, that doesn't seem to make any difference. I hit F4, select "Safe graphics mode" and hit enter. It drops me back to the screen where I can select "Try Ubuntu without changing anything..." (is it supposed to do that, or is it supposed to start booting when I select "Safe graphics mode"?) I select "Try Ubuntu without changing anything...", and after watching the progress bar with the orange bar moving back and forth after a few moments, it drops to the ash shell.

Interestingly, if i type "exit" at the ash shell prompt, it just hangs. I have to press and hold the power-off button on the computer and shutdown in order to reboot. I seem to remember when I was trying this yesterday that sometimes typing "exit" at the ash shell prompt would cause it to reboot, and sometimes it would just hang as it did today. I haven't noticed a consistency, here.

Just for full info, I have an nVidia GeForce 8300GS graphics card. The monitor is a Dell "17 inch SE178WFP Widescreen Flat Panel Monitor" that came with the PC. I think the actual manufacturer is Samsung, though I"m not sure.

---

### Post by Mike Brennan on 2008-05-13
Well, I just successfully booted the Hardy Heron Live CD. The key that made it work for me is the "irqpoll" boot parameter. When I got to the screen asking if I want to start or install Ubuntu, I pressed F6 and added "irqpoll" at the end of the string of boot params and pressed ENTER. The Live CD then booted fine.

I'm glad this worked, but I'm not sure I fully understand the significance of this, so I'm still holding off installing. I don't want to install and then run into a bunch of problems.

In case anyone else runs into this, though, try the "irqpoll" boot parameter.

---

### Post by davemiles871 on 2008-05-14
I side with Mike, I have tried two different machines, one an old Arima P100B Pentium 2 and a slightly newer Dell C600 P3 with the live CD and it just wont install, end of story, except that on the Dell it does drop into the shell. It wont boot on the older machine. I tried the alt.install disk, and this reports problems with the CD on both machines !! in the Arima case CD not found, Dell error reading disk. Hello you just booted from it !! 

I downloaded Fedora 9 live CD this morning at 0600 hrs and by 6.54 it has installed on the Dell. I'll try the full install as soon as the download completes. 

Sorry Ubuntu, cant use if wont install.

Dave

---

