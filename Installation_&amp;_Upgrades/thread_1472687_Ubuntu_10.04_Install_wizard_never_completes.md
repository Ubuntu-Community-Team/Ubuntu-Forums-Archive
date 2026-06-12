---
title: "Ubuntu 10.04 Install wizard never completes"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by vandy-sj on 2010-05-04
First tried to online upgrade from Ubuntu 9.10 to 10.04 LTS which resulted in GRUB problem, but having already saved my data I decided to do a fresh install. Using the default Desktop 32-bit CD iso (burned at a slow speed to ensure reliablility), and low-level formatting my target hard drive in advance (to give it a 'fresh' drive), I started the 'Install 10.04' process. After proceding through the initial 7 steps and starting the Install Wizard, it is currently at 79% - showing 'Retrieving file 4 of 4' - and it has been at 79% for the past 24 hours. It does not appear to be locked up or frozen, and I get mouse and desktop response, but this is 'way too long' to install from a CD. My system is an older Intel P3, 386MB system memory, 10GB hard drive system that has run every version of Ubuntu from 6.x through 9.10 - until now. Fortunately I still have a Windows system to write on this forum. Is there a problem here? Is this Install Wizard install time typical? Did I do something wrong with this fresh install? Thanks for your help!
 
UPDATE: Install Wizard still at 79%, now showing 'Retrieving file 5 of 6', so the install is still running. Why is this install running sooo slow on my system? This is well over 30 hours into this install.
 
UPDATE 2: Well, the Install Wizard marathon continues - Day 2. Install Wizard still at 79%, now showing 'Retrieving file 1 of 10', so the install is still running (and running, and running) but snail-pace slow. I'll be glad when I can get back to an Ubuntu desktop and my other work projects.
 
UPDATE 3: OK, it's been nearly a week since my original post. As you can see no responses. I've not been sitting still. To make sure I did not have a hardware-related problem, I replaced my older hard drive and CD drive with a new hard drive and a DVD-RW drive, then tried installing 10.04 from a CD again. Still no go. To verify the new hard drive and DVD drive were working OK, I installed Ubuntu 9.10 from CD on the new hardware - and that worked perfectly. I then retried installing 10.04 from CD and that did not complete - hung at 79% completed, last shown status was "Configuring network". Next I deleted the partitions and reinstalled 9.10 - again, that worked OK. I then tried an online 10.04 Upgrade using the 9.10 install, and at 82% completed I got the following message: "Missing resources - The Network Manager applet could not find some required resources. It cannot continue." with an 'OK' button. So, now both incomplete installs balk at the 'network configure' portion of both the 'Install' and 'Upgrade' attempts. Odd that booting from the 10.04 CD gave me a valid network interface and connection to the Internet, but the CD Install and Online Upgrade had problems at the network portion of the process. Just so you know, my network interface - that has worked flawlessly with all previous Ubuntu versions - is a Netgear FA-311 10/100 Mb/s PCI card. I'm letting the online Upgrade complete, and I'll deal with the initial reboot, post-install issues later. I hope this info helps somebody. I wish I knew what it is about my system that causes this 'network configure' error with 10.04.

UPDATE 4 - FINAL: After letting the online Update run to completion - even though I got the "Missing resources..." error message - upon reboot I finally got a successful restart and login to my Ubuntu 10.04 Desktop. I'm using 10.04 now, but have not configured or tested everything yet. Just wanted you to know that despite the error message during the online Upgrade, it finally did complete successfully. Now that I have my 10.04 desktop, I'm ending this thread. Cheers!

---

### Post by berwyn on 2010-06-03
I have the same problem.  Gets to 78 or 79% and either says "Copying Files 1/10" or "Retrieving files 11/12" but progresses very slowly -- so far only tried up to 3 days.

I'm running a 3GHz desktop machine with 1G memory and doing a clean install.

I've removed my CD/DVD drives to make sure it's not them (I'm booting from USB).  If I boot the live CD first and install from that, same problem.  But the live CD detects my wireless network card and nvidia graphics card just fine so it isn't them.  Not much else to remove!

I've checked dmesg and /var/log/syslog and /var/log/dpkg.log but don't see anything untoward.

If you have any further information on this, I'd be keen to know it.

---

### Post by berwyn on 2010-06-07
As followup, I've had some success with this problem now.

I ran 'top' during the 78% install hang and noticed that the Xorg process was taking 99% or 100% of the cpu time.  Google said that that kind of behaviour can be caused by any old process polling X windows, so it wasn't conclusively an X windows issue, but I figured I'd try removing my graphics card anyway.  I also disable the floppy disk drive controller in the bios at the same time.  Seems to work now.

I have some sort of unmarked graphics card that detects as an nvidia card.  But I had the option of removing it because my motherboard also has a graphics card built in.

After making these two changes, I was able to install ubuntu 10.04 without it slowing to a crawl at 78%.

Now that ubuntu is installed, I've re-installed my graphics card.   Then I let the hardware manager automatically find and install the proprietary nvidia driver, and it seems to be working fine now.

:)

- Berwyn

---

