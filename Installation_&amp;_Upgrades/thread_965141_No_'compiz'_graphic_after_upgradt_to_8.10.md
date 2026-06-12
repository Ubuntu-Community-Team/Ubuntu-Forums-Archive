---
title: "No 'compiz' graphic after upgradt to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by thered on 2008-10-31
I've just upgraded to Intrepid.  Everything went well, no errors.

Since then I notice I'm running with 'No visual effects' Trying to change this back to selection 3 -extra - I get a dialog box which says searching for driver.  It then disappears and is replaced with another dialog box telling me "The composite extension is not available" and it doesn't change.

I'm running a Dell Inspiron 6400 laptop with a X1400 ATI card - it worked before the upgrade.

I'm running the ATI propriety driver for FGLRX

Any ideas?

---

### Post by shankariyer on 2008-10-31
I've the same problem...
 
Immediately after upgrade, during reboot it kept throwing 1000's of lines of errors on
fglrx, couldn't read as it was spooling so fast. I restarted it anyway. There were no
problems to get back and when I logged in, it informed that its using 
'restricted; drivers from ATI.
 
But, when ever I open any application, it creates these ghost images or frills ( frame
by frame ), which I think is a video driver issue.
 
I do see that the restrcited driver is 'active', but I am unable to get compiz working or
even a smooth video rendering.

---

### Post by MickS on 2008-10-31
I'm another with the same problem, compiz was fine with Hardy but doesn't work with Intrepid.

Mick

---

### Post by jerrylamos on 2008-10-31
Some significant changes were made in compiz between 8.04 and 8.10 such that some video graphics hardware & drivers may even hang up or freeze the system.  The official 8.10 fix for my IBM Thinkpad with Intel graphics is to blacklist the Intel graphics so that compiz doesn't start.  No visual effects which doesn't mean anything to me since I run full screen internet, full screen Office, full screen photos, ....

The other fix is to use 8.04 since it has long term support.

Jerry

---

### Post by thered on 2008-11-01
Jerrylamos:

Thanks for that reply.  I too can live with it, just wondered why and if there was a fix.  At least I haven't got the severe symptoms that shankariyer has. 

Hope you get sorted shankariyer and Mick.

---

### Post by MickS on 2008-11-01
I have messed about for hours reinstalling drivers and so on, and have finally got it working. I only wish I could tell you what I have done because I'm not sure myself but it is worth persevering, it was for me anyway because it now works better than it did before, I'm on KDE 4.1 BTW.
I found all the information I wanted in various places on the forum so keep looking it's there, sorry I can't point you at the threads that helped me only I can't remember what they were :confused:


Mick

---

### Post by shankariyer on 2008-11-01
I gave up after a while. Decided that it was time for me to clean-up the system as I've upgrading over several releases. So installed Ibex all over again. After few hiccups, Ibex is up, but grub is screwed up for Windoze. Oh well, another set of issues.

---

### Post by ellalan on 2008-11-01
Hi
I hope this thread will help those who are having problem with Compiz:
[http://ubuntuforums.org/showthread.php?t=966030](http://ubuntuforums.org/showthread.php?t=966030)

---

