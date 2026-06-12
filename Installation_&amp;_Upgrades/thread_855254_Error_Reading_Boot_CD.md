---
title: "Error Reading Boot CD"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by paulmcdonald on 2008-07-10
I tried to upgrade 7.04 to 8,04.1.  It froze the PC!  I tried to download 8.04.1 two different times and burnt a CD.  When I try to load the CD I get  "I/O ERROR:  Error Reading Boot CD"

Is there a problem with 8.04.1????

---

### Post by VMC on 2008-07-10
Burn the cd at slowest speed. Check the md5sum. Also can you use the Media check feature of the livecd or does the error show up immediately?

---

### Post by robnoyes on 2008-08-07
Same problem...

I'm trying to re-install because of the problems below, but I can't get anything to run, Live CD, Install, Check CD, Test Mem, or Boot from 1st HD.

Without the Live CD, I can get past Grub to an error reading: Error 15 File Not Found
- forums said to ensure boot disk is hd(0,0), not hd(1,0).  That wasn't the problem.

With the Live CD, I get to the menu choices, but as soon as any are chosen the following error occurs: I/O Error Error reading boot CD.

Help...thanks in advance.

---

### Post by robnoyes on 2008-08-08
Ok...can I put [SOLVED] if I didn't originate the thread?...because, in my case, this problem is solved.

I went to the MIT Media Lab site to re-download Ubuntu. It was up-to-date and went right on.

Now, I'm off the new problems.

---

### Post by LutefiskJoe on 2008-08-12
I'm having the same problem with the

[COLOR="Red"]**I/O ERROR: Error Reading Boot CD**[/COLOR]

I'm, using a  Thinkpad R31 with no operating system installed.


I've tried buring in Ubuntu using Brasero and in Windows using Nero, and have been burning at the slowest possible speed. 

It's the latest download of the alternate cd (the live cd would invaribly fail midway through the installation) that I'm using, and it's been md5'ed.

I had been using CD-R,s, but after so many failures, I'm now using CD-RW's... from other forum posts I've found, the CD-R's shouldn't be an issue...


any thoughts/suggestions??

thanks

---

### Post by Crafty Kisses on 2008-08-12
Have you tried the alternate CD?

---

### Post by LutefiskJoe on 2008-08-12
Yes, the above post was with regard to an attempt with the alternate cd.  The Live CD invariably croaks midway through partitioning.

More info, from my latest attempt:

I followed the instructions i found on this page:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The md5 sums check out fine.

This time, I used InfaRecorer, as instructed, and burned at the lowest available speed (4x).

Before attempting the install, I chose the Check CD for Defects option, and eventually got a red screen with the following error message:

[FONT="Courier New"]**./pool/main/g/gnome/glibmm2.4/libglibmm-2.4-1ca_2.16.0-1_i386.deb file failed the MD5 checksum verification. Your CD ROM file may have been corrupted**[/FONT]

Confusing... If the md5 sums check out, where might the problem be?

When I proceed with the install, I invariably get to another red screen with this message:
[FONT="Courier New"]
[B]Warning:
file:///cdrom/pool/main/g/glibc/libc6-i686_2.7-10ubuntu3_i386.deb was corrupt[/B]
[/FONT]

I choose to continue anyway, and immediately get this:

[FONT="Courier New"]
[!!][B] Intstall the base system
Debootstap warning
Warning couldn't download package libC6-i686[/B]
[/FONT]

and then....

[FONT="Courier New"]
**file:///cdrom/pool/main/g/glibc/libc6-i686_2.7-10ubuntu3_i386.deb was corrupt **
[/FONT]

again choose continue... Installation proceeds a few seconds, then 

[FONT="Courier New"]
**Warning: Failure trying to run: chroot /target mount -t proc proc /proc**
[/FONT]

choose continue, then

[FONT="Courier New"]
[B]Base system Installation Error
The debootstrap program exited with an error (return value 1).
Check /var/log/syslog or see virtual console 4 for the details[/B]
[/FONT]

choose continue, then
[FONT="Courier New"]

[B]Failed to Install the Base System

The base system installation into /target failed.

Check /var/log/syslog or see virtual console 4 for the details[/B]
[/FONT]continue again, then

[FONT="Courier New"]
**An Installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is:  Install the base system**
[/FONT]

Now, to a relative newb, most of this is greek to me, especially the only explicit instruction,


[FONT="Courier New"]
**Check /var/log/syslog or see virtual console 4 for the details**
[/FONT]

Is this a lost cause? Any suggestions? 

Please Help!!

---

