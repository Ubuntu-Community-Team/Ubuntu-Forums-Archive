---
title: "Ubuntu Reformatting On Legacy Laptop"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by blitzracer on 2009-12-02
Events leading up to the problem

Alright, Here goes the explanation. This morning I had a working Toshiba Satellite A-15 running well on 9.04, it was slower than I would like it to be (always has been) so I proceeded to install the LXDE desktop environment (a lightweight alternative to GNOME) the problem was the internet failed to work, I installed the Network manager it has but read that the GNOME NM works just fine. I try and reinstall that one since I know it will work with my network card and its basically plug and play. (for some reason the Linksys wusb54g works without any modification or input just plug it in...) Since this failed to continue to work that way in 9.10 and I couldnt resolve the issue I kept 9.04 (this was on another box)

The way I had installed Linux on THIS laptop was via Windows XP since it has no option to boot from CD there was a option to "help computer boot from cd" I used that it booted and I was freeing my laptop from windows. It worked, has flawlessly for months (except for speed) now today I decided to just reinstall a fresh copy... That is a problem all its own.

After pressing all the F keys during 20 reboots i found no way to boot from cd called tech support and they say "That laptop has no ability to change boot priority" WOW so how would my windows xp recovery disc (which Ive used before) work.

Solution: remove the hard drive and wait for it to boot from CD 

one step forward as they say...

now I get the Live CD running Ive never had it load that slow but no worries, if it installs ill be happy again :)
well, heres the Kicker after waiting 30 minutes to get to the 4th screen in the installer in wont see the hard drive... 

One Step back. ](*,)

My theory is that the hard drive wont activate after being unplugged then plugged back in while the computer is on. it would explain why the live cd is so slow (since it will use SWAP if available) 

another notable irregularity is a series of errors that have to do with the system tray at startup of the live session. so theory 2 is a bad CD burn...

Im going to try and burn a new image on a cd-r this time in stead of a DVD-RW ill let everyone know how that goes. If someone has some info on this help would be nice. Thank you.

---

### Post by efflandt on 2009-12-02
You can check the files on the CD if you can get to a term or console on a working linux system.  Mount the CD, cd to it, then do **md5sum -c md5sum.txt** (it may take awhile, and might even appear to be doing nothing while checking a large file).

I had one CD (Qimo for kids based on Xubuntu 8.10) where md5sum of the iso matched, but one file failed when checking CD files against md5sum.txt.  I loop mounted the iso and got the same answers, so I figured someone had changed a file at the last minute and forgot to update md5sum.txt in the iso

---

### Post by blitzracer on 2009-12-02
Okay so, I burned it onto a cd, it works much faster (yay!) but that still didnt resolve the one final problem. In the need to remove the HD to boot from a cd It fails to find my harddrive later after being plugged in. so, I am going to try something kind of odd. 
 
Using Grub Im going to make an option to boot from the CD (hopefuly it works) does anyone have any Idea what a CD drivbe might be named? my HD is SDA so is my cd CDA? or something along those lines? Ill check my Media file and see what that says.
 
Luckily the install I have still works, but no internet :P
 
Ill report on my findings later today
 
30 MINS later...
alright, so Ive been looking for a tutorial on grub booting CD's, some report it works some dont, a lot of it is from 2005 and may not be relevant anymore... Its Grub Legacy on this laptop since it has no dual boot like my desktop I saw no reason to upgrade to grub 2... A lot of people just ask "why if the bios does that?" I read somewhere on these forums of a guy who had the same story as me, used windows wubi.exe used the option to force load the cd and install linux, now it comes time to reformat and force boot is no longer possible because it has a linux system now why will this option work on windows but not natively (hmm sounds like an Idea to sugguest for the next release) well back to work reading up on it.

---

### Post by blitzracer on 2009-12-02
Alright, it worked, Grub booted from the cd and im loading the live desktop now :) one step forward :P I had to play around with grubs command line to find the right root harddrive 
 
for anyone who wants a tutorial on this operation I tested it on legacy grub, Ill experement with grub 2 when I get back to the appartment on my desktop but:
 
[http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)
 
theres the link. im going to save this tutorial and the files there for future reference on booting cd's in grub. its fairly straight forward though and a great too for these old relics :)
 
we'll see how the install goes now... cross you r fingers

---

### Post by blitzracer on 2009-12-02
Great News, its installing ubuntu right now :) Lesson of the day: if it ain't broke dont fix it :P okay well maybe yesterdays lesson.... Hopefuly some chap who need the some info finds this thread, it may be very helpful when getting Ubuntu onto a dinosaur!
 
Problem: Solved

---

