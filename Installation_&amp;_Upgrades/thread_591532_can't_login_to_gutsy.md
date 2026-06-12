---
title: "can't login to gutsy"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by n0idbi0n on 2007-10-25
Hi all, 

I'm new to this linux thing and had installed 7.04 as a dual boot on my Dell laptop along with XP to give it a try.  I added the Beryl stuff to play around with the effects - pretty cool - and thought I'd give gutsy a try.  After upgrading, which seemed to go smoothly, I'm no longer able to login to Gnome.  I get to the login screen, but after giving my username and password, it thinks for a bit, briefly shows a terminal screen and then goes back to the login screen.  The only way to get in is if I select the "failsafe Gnome" session, but this looks the same as 7.04 - no desktop effects or anything - I'm assuming this is like safemode in windows?  Any ideas how to fix?  

TIA.

---

### Post by Pumalite on 2007-10-25
Memory?. Graphics?.

---

### Post by scottmuz on 2007-10-25
I had a similar issue caused by my /home partition not being mounted.
If this is the issue you see some error messages about no home
directory after you log in from gdm.

But anyway removing the evms package was the solution to my problem, see:
[http://ubuntuforums.org/showthread.php?t=583003](http://ubuntuforums.org/showthread.php?t=583003)

---

### Post by tipiglen on 2007-10-25
I get all the way through to login, but without a display.  I can hear the drums, log in and then the music, but no display..  Now I can't even get a terminal with ctrl/alt/f2.  ctrl/alt/backspace reboots but without display.

Before this I had a screwed up display like an old tv out of horiz hold, and I tried getting rid of fglrx.  Now, of course, I can't get it back.

help!!!
Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by n0idbi0n on 2007-10-25
> **Pumalite said:**
> Memory?. Graphics?.

For graphics it says Radeon RV250 [Mobility FireGL 9000].  503 Mb RAM.

---

### Post by Pumalite on 2007-10-25
I have the feeling that is time lost. You'll probably need a fresh install. But lets try and see if we can save this situation first.
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver. then: startx
Let's see.

---

### Post by tipiglen on 2007-10-25
"I have the feeling that is time lost."

I haved the feeling you're right!

"You'll probably need a fresh install. "

Tricky, because the box I'm setting up refuses the cdrom as boot, no matter how I tweak setup

"But lets try and see if we can save this situation first.
Ctrl+Alt+F1 to get command line"

I can't get a command line any way!  Can get reboot (in the dark - no display) with ctrl/alt/backspace, but no terminal, ctrl/alt/f1, f2, f3.....

Elsewhere someone mentioned he had mounted the cdimage he had copied to his HDD.  I may try that in the morning (2AM here now)  Any suggestions how to proceed that way?

Presently have been booting from a grub floppy quite happily to win/ME (can't wait to finally chuck that), Dapper (most of the time) and Dyne:bolic (useful access to all filesystems)

Thanks for keeping on

ed

(laptop works fine with gutsy, though haven't tried the fancy 3d stuff - why bother?)

---

### Post by n0idbi0n on 2007-10-25
tipiglen:  I might be wrong, but I think that comment was directed to me (you know, the guy who started this thread).  In any case choosing the vesa driver seem to work as far as letting me login without selecting the failsafe session.  Thanks!  
Now the problem is that the Visual Effects don't work - if I select anything besides "None" in the appearance preferences, it tells me "Desktop effects could not be enabled".  Any ideas?

---

