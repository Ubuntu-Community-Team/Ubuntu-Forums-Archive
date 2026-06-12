---
title: "Problems installing 9.10 onto Win 7 laptop &quot;No OS exists&quot;."
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2009-12-29
I have a Toshiba Satellite A100 with a fresh install of Windows 7 Professional.  I burned a 9.10 CD and it works OK in live mode, but when I try to install I get a "No operating system exists on this computer" message.

This is a problem because I want to dual boot 7 and 9.10, and I don't believe Grub will give me the option if it can't even find Windows.

Perhaps related (or perhaps not) is a problem that my USB HDD gives the whole process.  If the external drive is not connected, the 9.10 CD won't even start, I just get a black screen with a pulsing cursor.  If the external drive is connected, the CD boots fine, but the installer wants to put Ubuntu there (SDB1).  It recognizes the main drive as SDA, but to install there I'd have to manually partition, something I've never had to do before.

---

### Post by phillw on 2009-12-29
Hi,

Win in genral, and specifically vista and win7 are best re-partitioned within win.

It's not as scary as it sounds, but, as with any disk-disecting, have a backup of your hard-drive.

What you need to do is shrink your Win7 area & leave the 'extra' area as un-allocated (no operating system etc on it), then reboot win (it may want to do a file check, that's okay)
Then, boot it again. once win7 is happy, you can use the liveCD to install & tell it to use the free space. you need, realistically about 10GB free space for ubuntu.
When you are asked for the amount to give swap, a simple rule of thumb is 1GB swap, or whatever amount of RAM you have - whichever is the GREATER.

The link to re-sizing with win, with screen-shots, well, thats over here -->  [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Post back if you do have a problem, but that's good How-To and Ubuntu should be happy once it sees the free area.

Regards,

Phill.

---

### Post by shaaaadoooow on 2009-12-29
Hmmm. Maybe it just doesn't detect any OS because it refers to the external HDD. Try running the live CD inside Windows 7 and let it restart your computer. Just a guess. :D

---

### Post by dishbert on 2009-12-29
I tried shaaaadoooow's suggestion, but the checking the "Reboot Now" option when running CD from within Windows 7 doesn't work at all on this machine.

I'm willing to try a manual partitioning from Windows or from Gparted, (thanks for the suggestions and the link phillw) but not until I figure out how to get the Ubuntu installer to recognize that there is an existing operating system on the computer.  

I can just imagine the world of hurt awaiting me if I install Linux and lose the Windows boot.  Screwing around with the new version of Grub is not how I want to start the new year!

---

### Post by dishbert on 2009-12-31
I gave up on 9.10 and burned a 9.04 disc.  I used the install feature from within the live session (selecting "install' from the first menu just gave me a black screen.)

Installing from the 9.04 disc found Windows 7 (but called it Vista) and offered me a side-by-side installation.  I resized the suggested Ubuntu partition using the slider, it installed flawlessly and rebooted with the Grub menu offering Win 7 or Linux.  At the first boot Win 7 wanted to do a disc check, but after that it was happy.

I updated 9.04, then upgraded to 9.10.  It's a long way around, but Koala didn't want to play nice with Windows 7 at least on this machine.

I hope this help someone else who's having problems installing 9.10 over Windows 7.

---

