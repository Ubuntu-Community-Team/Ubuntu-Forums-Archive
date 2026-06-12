---
title: "I Want Uninstall The Existing Version of Ubuntu (14.04) and Install Clean"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by terry16 on 2015-01-21
Hello All,
As the heading states, a friend of mine had 12.04 installed (somewhat successfully) on my laptop.  It had consistent error messages, so I decided to upgrade to 14.04.  As is well-documented, that upgrade made things even worse.  I am currently limping along with the goofed-up upgrade, but i want to simply uninstall the current OS, then turn around and reinstall 14.04 with hopefully better results.I have tried various methods to reformat the hard drive, but I consistently get error messages ("device is busy," or "cannot show display.")  Is there a way to completely remove the existing OS and replace it with a version that actually works?

Any help would be appreciated.

Terry

---

### Post by kerry_s on 2015-01-21
install unetbootin, make your self a usb installer, boot from usb, follow directions.

---

### Post by deadflowr on 2015-01-22
> **terry16 said:**
> Hello All,
As the heading states, a friend of mine had 12.04 installed (somewhat successfully) on my laptop.  It had consistent error messages, so I decided to upgrade to 14.04.  As is well-documented, that upgrade made things even worse.
Firstly, where is this well-documented?
As you only have participated in [one other thread]("http://ubuntuforums.org/showthread.php?t=2231950"), which does not mention upgrading or problems thereof.
And secondly
 > I consistently get error messages ("device is busy," or "cannot show display.") 
This is typical if trying to reformat the disk that you are using.
Download a copy of Ubuntu, if you do not have one already, and boot into a live session.
Then you can reformat the disk to your liking.
A live cd/dvd/usb, session comes with a disk management tool called gparted(it does not get installed, though, when you install ubuntu; it is in the live session so you can use it to do what you are wanting to do. There is normally no reason to fiddle with your partitions after the system has been installed, so there is no reason for it(gparted) to be installed. If that makes sense.

Lastly, and sort of off topic here, but did you ever figure out a solution to your networking problem?

---

### Post by terry16 on 2015-01-22
Thanks for your responses so far.
By "well-documented," I was referring to the various posts, threads, etc. by the numerous people on various forums who encountered the same problem.

I previously downloaded gparted; when I try to run it I get the error message "cannot show display."
I have a copy of ubuntu on a flash drive; I've tried to get it to run.  I'll try it again.
The networking problem was on another computer; that problem has been resolved.  Thanks.

Problem resolved.

---

### Post by mörgæs on 2015-01-25
Good, now it's a polite gesture to describe the solution and mark the thread SOLVED using Thread Tools.

---

