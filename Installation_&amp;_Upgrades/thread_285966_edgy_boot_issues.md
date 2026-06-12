---
title: "edgy boot issues"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ejo on 2006-10-27
Here's my situation: I have an older Gateway machine.  500Mhz, Voodoo3 video card, 384mb Ram, Gateway VX700 Monitor, etc.  

Last month, I wanted to test Ubuntu out and begin playing with and learning linux.  I installed Dapper from a live cd without much issue.  Once I got it up and running properly, I was pretty happy with it.  I upgraded using the guide on here from the command prompt to Edgy last nite.  The install went fine, but when I rebooted at the end, it would not load the OS.  So I just decided it would be easier to do a fresh install.  

So I downloaded Xubuntu instead on a live cd.  When I placed this cd in and booted from it it would do all of its loading, get to the end and begin to load the OS and the screen flickers a couple times and it pushes me back out to a Login screen.  I allow it to log in the user "Ubuntu" but as its loading X again, the screen flickers a few more times and kicks me back to the Login screen.  This repeats indefinitely.  Changing the session information does nothing as well.  

These are the other things that I've tried:  Deleting the partition completely and starting from scratch - same thing happens.  Downloaded an Ubuntu live cd for Edgy and tried it - same thing happens.  Downloaded the alternate Ubuntu install cd - the install actually completes correctly and when I try to load Ubuntu for the first time...the same thing happens.  

Interestingly, I can still use my Ubuntu cd from Dapper and it loads X just fine and will begin the install process without problem.  I just stopped it since I'm interested in getting Edgy running instead.  Can anyone help out a relatively new user?

---

### Post by ejo on 2006-10-27
A correction to my previous note: On my currently installed version of Ubuntu (the version of Edgy that I got to completely install via the alternate cd, but still has the same login issue), I CAN bring up a failsafe terminal session window.  But don't have a clue as to what to do here to make things better.

---

### Post by ejo on 2006-10-28
I'm going to update this thread in hopes that someone who can help me sees it sometime.  

I've ran thru the commands at the recovery session to reconfigure xserver-xorg.  I tried both the vesa and the vga drivers, but to no avail.  Neither even loaded a readable screen.  An interesting side note, however: it tells me that I cannot reconfigure gdm (which was the next step in the walkthrough on this site).  Anyone?

---

