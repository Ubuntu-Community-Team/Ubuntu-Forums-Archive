---
title: "Upgrade failed: 6.06 to 8.04"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by JohnLauritsen on 2008-07-05
I tried upgrading from 6.06 to 8.04 using the alternate install disk (which checked OK using MD5SUM).  Within Ubuntu and with the modem on, I put the disk in and followed the prompts.  Everything seemed to go all right, though I'm not sure if I selected the right keyboard.  Then it got to the point where I had to choose either RESTART or something else.  I restarted.
The installation had put the new GRUB on a floppy (without being asked to), which is what I wanted.

When the bootup started, there were messages:
  - harware drivers  - failed
  - setting kernel variable -- failed

and various other failure notices.

Then, when it got the the USERNAME login, there was no response from the keyboard, and the mouse didn't work.  I couldn't key in my username.

At this point, what should I do?  I have both the alternate desktop install disk and the regular one.  I was able to run Ubuntu from the regular (live) CD, but of course I couldn't get into my customized versions of Firefox or Thunderbird.

Should I try a re-installation using the regular disk?  Should I have installed outside of Ubuntu?  Any help would be appreciated.

JL

---

### Post by Pumalite on 2008-07-05
Use your Live CD to save data and /home
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by JohnLauritsen on 2008-07-06
Thank you.  I did backup crucial stuff.  My mistake was stupidly trying to do the install when Dapper Drake was running.  The next day I did it the right way, booting from the alternate disk, and everything went smoothly.  Everything's fine, except for a little tweaking.

JL

---

### Post by Dale61 on 2008-07-07
> **JohnLauritsen said:**
> 
The installation had put the new GRUB on a floppy (without being asked to), which is what I wanted.

A floppy? Do they still exist? [img]http://bestsmileys.com/thinking/6.gif[/img]

---

