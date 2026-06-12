---
title: "ati graphics card"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2008-11-03
Hi,

I have an acer laptop with an old ATI radeon 128MB  something like RV300, and according to the DRI webpage the radeon driver does support 2D and 3D with this chipset.  I have a desktop with a Radeon that is a year older with 128MB.  Im sorry I dont know chipsets in my head, but the chipset is beside the point...

I can boot the Live 8.10 i386 CD and get GUI and it looks fine.  It is using 3D desktop and even get wobbly windows.  However, when I install Ubuntu, and boot, I get a black screen with Xorg.

Now, im sort of used to this, but before, I would ctrl-alt backspace, edit xorg.conf to use vesa driver, logon to X and then install fglrx driver (with dapper drake), but since they got rid of the xorg.conf file, I no longer know how to do this?

But my main question is, why do I get a black screen when the Live CD works fine in 3D and is obviosly using the radeon driver?  Why doesnt the radeon driver work after installing?

2. How can I check and change the driver I am using with xorg 7.4?

This must work: must be a config thing, as chipset is so old now (bought 2005)

Any tips much appreciated.

---

### Post by dsmithhfx on 2008-11-03
Here's what worked for me:

apt-get update
apt-get upgrade
apt-get remove --purge xserver-xorg-video-ati (then do -radeon and -fglrx, just to be sure)
apt-get install xserver-xorg-video-ati
dpkg-reconfigure xserver-xorg (I had to do this one twice)

Once you get a graphical desktop, go into settings/hardware drivers, and enable proprietary video driver (for fglrx), cross your fingers and restart xserver by logging out and back in.

This worked for me with a 9550, same vintage and chipset as yours, apparently.

---

### Post by finite9 on 2008-11-07
half worked for a while then back to black screen.

I realised I was running beta version of intrepid, so i did a dist-upgrade from tty which automatically started gdm, and it displayed ok, but no mouse or keyb input, so i had to reboot.  Upon reboot, I got gdm and could login and got desktop effects with ati/radeon driver...all well.  Then I decided to log out, do another update/upgrade/dist-upgrade, and removed xserver-xorg-video-ati and radeon and -all and then reinstalled all 3 and restarted GDM...black screen.  reboot black screen, nothing else seems to work.

Actually unsure right now if my monitor is fully working.  I started to get a vague memory that when I ran XP 4 yrs ago with this monitor, it would sometimes flip out when mode switching from login screen to desktop, and I had to power off the monitor (doing this does not have any effect now).

Will have to check using another monitor.

---

### Post by finite9 on 2008-11-09
think it was monitor.  cannot handle mode switch to X.  If I turn it on after PC has booted into gdm, then turn on monitor it is OK.

---

