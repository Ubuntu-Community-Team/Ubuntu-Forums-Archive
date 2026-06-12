---
title: "Upgrade interrupted by power failure, login impossible"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Michael%S on 2006-06-05
So yesterday at school (where we have one Ubuntu machine and a couple of Windows machines) I initiated the upgrade through update-manager. By the end of the day it still wasn't done installing everything and I had to leave so I left it there. This morning when I came in I found there had been a power failure since school closed yesterday, and it is now impossible to log in there. gdm works fine, but once you log in it just stays with the blank brown background (ignoring the image selected by the user) and a black cursor and nothing seems to happen. Just to make sure it wasn't trying to do something I gave it a few hours, but nothing changed.
Is there some simple way to get it fixed up, or would it be best to use a boot CD to save the data onto a USB drive and install afresh?
I'm not afraid of some work, but I don't have endless time to pour into this problem and I'm not very adept at this kind of thing under GNU/Linux yet... If it can save me time (all later configuration included) I would prefer to just start from scratch and then get stuff back from a backup.

---

### Post by pwaldo on 2006-06-05
Apt is smart enough to know where it left off.  Try the same procedure again, and hopefully it should complete the upgrade.

---

### Post by zip_000 on 2006-06-05
Funny, the same thing happened to me last night - I started the install, and went to bed. The power went out during a huge rain storm. This morning, nothing but brown unresponsive screen. I just started from scratch, and everything went fine.

---

### Post by Michael%S on 2006-06-05
[quote=pwaldo]Apt is smart enough to know where it left off.  Try the same procedure again, and hopefully it should complete the upgrade.[/quote]
How can I get to it without logging in (or without loggin in through gdm, if that's the issue)?

And if I install anew, what should I do to make sure as little as possible data and settings are lost?

---

### Post by SkyNet2029 on 2006-06-05
If you used grub as a bootloader, you should be able to hit the 'ESC' key just as your machine boots up (right before the initial Ubuntu splash image) and choose the previous kernel image to boot from. Provided that is successful, you can then login using a console (ALT+F1 or 2, or 3, etc..) and force apt to
finish what it started with this command:
```
$sudo dpkg --configure -a
```
as for doing a fresh installation whilst retaining your data and settings, you can burn your data to either a Cd or Dvd, depending on your data size needs. The other option would be to use the 'copy data from another partition' option in the installer menu during the Disk partitioning phase. Yet another option would be to copy all of your data and settings to another HDD or partition prior to all of this, using a live CD to boot up if you still  can't login.

---

### Post by Michael%S on 2006-06-05
Between continued upgrade and fresh installation, which would you reccommend on a basis of least time required and least chane of complication (during and after the process)?
If I go with a fresh installation, what data would I need to copy over to retain documents and settings, besides the home directory? I have a USB drive I can use for this, the problem is just that I don't know what I should copy. Also, would it be best to format the USB drive via Ubuntu before using it to back up the data, or would it be fairly safe to use it with its current FAT32 filesystem?

---

### Post by Michael%S on 2006-06-06
Erm, bump?
I'm at school now for the next six hours or so, I'd really like to get that machine up and running today.
**EDIT**: Okay, I started the dpkg --configure -a, and it seems to be going smoothly so far...

---

### Post by crazybilly on 2007-10-19
well, you're a couple steps ahead of me--I accidentally pulled the power cord w/o my battery plugged in.  and now I just get a kernel panic.

I tried editing the grub line to use an old kernel (I'm assuming the new one's not configured yet), but I must be getting it wrong...something like 2.6.20-16-generic, maybe?

---

### Post by kentcyu on 2008-03-16
I am installing gui package in gutsy. My internet connection is snail speed and download is getting so long. 
I'm sure it will take more than 6 hrs to finish the download. 
My question is:
What happens if suddenly there is a power failure. My last command was aptitude ubuntu-desktop.
Will repeating the last command takes me to where there was power out or it starts from the beginning?
Is there a way not to start all over again?

thanks a lot

---

