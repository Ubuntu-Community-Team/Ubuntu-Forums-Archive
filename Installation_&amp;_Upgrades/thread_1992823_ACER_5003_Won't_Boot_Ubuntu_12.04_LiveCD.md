---
title: "ACER 5003 Won't Boot Ubuntu 12.04 LiveCD"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by Robbobden on 2012-05-31
Howdy,  -  I have an older ACER laptop that's been running Ubuntu 10.10 for a couple years.    Now that I'm getting the no support notices, I want to install Ubuntu 12.04.   The boot freezes just after I get a notice about b43 drivers.   I've tried various combinations in the F6 menu with no luck.    Here's something strange:   I have a Dell Mini9 with a blown SSD.   I have 12.04 installed on an 8G USB.     When I boot the ACER with this USB stick, it runs great.    No WiFi and probably other hardware inop, but it looks pretty good.    Is there something I can look at while it's running from this USB that might tell me how to get success with the LiveCD ?

Thanks !
RDL

---

### Post by Robbobden on 2012-06-01
Well, I stumbled on something that worked for me.    It's from a post Apr 27th, 2012 by someone with the screen name of 'Powered Descent'.    Here's the link:
[http://forums.somethingawful.com/showthread.php?threadid=3481578&pagenumber=1](http://forums.somethingawful.com/showthread.php?threadid=3481578&pagenumber=1)   

Just scroll down until you see the post from 'Powered Descent'.

He tells us there's a bug in 12.04 having to do with the B43 driver.    What I did varies only slightly from what he suggests.    Since my ACER halted and never made it to the TRY or INSTALL screen,  as soon as the purple splash screen appeared with the rectangle and little stick figure in the circle, I hit the space bar.   Then enter at the keyboard screen.   Then F6, escape, and then typed:   b43.blacklist=yes    As 'Powered Descent' suggests, leave a space after the end of the line.   In my case, there were two dashes  --  

Then I hit the enter key again.     The LiveCD   then booted up to the Ubuntu 12.04 Desktop.   Success !    The install is in progress right now and I don't anticipate any problem getting the B43 driver installed after everything finishes.   

RDL

---

### Post by morhin on 2012-09-18
I tried this on my 2 year old Acer Aspire 5250 and it didn't do anything. I'm still stuck at the "dots".
Didn't happen to see any other work arounds did you?

Thx
Morhin

---

### Post by Bucky Ball on 2012-09-18
Good news! Please mark thread as solved to help others. ;)

---

### Post by Robbobden on 2013-01-11
I stopped looking for the solution after what I did to get around the b43 problem.   Now we're in 2013 and I hit this thread by accident and found I didn't mark it as solved for me.  But, I might leave it open a while longer as I just tried to get the Xubuntu 12.10 Desktop i386 iso to run on this same ACER.   It appears to have the same b43 problem, but when I add that b43.blacklist=yes entry as above, it still fails.   Checking that out now.

RDL

---

### Post by Bucky Ball on 2013-01-11
Good work. Keep at it and post back. You may help others with your investigations ... ;)

You haven't tried Xubuntu 12.04 LTS?

---

### Post by Robbobden on 2013-01-13
Good suggestion !  I only downloaded Xubuntu 12.10 because it was there on the first page.   Earlier today, I downloaded Xubuntu 12.04 LTS.    After tweaking the boot options with that     b43.blacklist=yes   command, it booted up normally.    Something in Xubuntu 12.10 causing trouble with this old ACER 5003 and its SIS chipsets.  

RDL

---

### Post by nightwolf2k5 on 2013-04-06
I seem to have a similar problem with my acer laptop. But after entering the b43.blacklist=yes, it reboots, goes to the desktop where i can just see a mouse pointer, then a blank screen and again the desktop with the mouse pointer. This just goes on forever. Is this the same problem you were facing?
I am trying to install ubuntu 12.10 though not xubuntu.

Any suggestions?

Thanks

---

### Post by Bucky Ball on 2013-04-07
> **nightwolf2k5 said:**
> 
Any suggestions?



Yes. Post a new thread about your issues rather than jumping on this one which has been inactive for three months. You will greatly improve your chances of getting help. Similar is not the same so it doesn't belong here. Please use a descriptive thread title. Good luck.

---

### Post by nightwolf2k5 on 2013-04-08
You misunderstand. I did ask if he has the "same" problem.
Robbobden mentions thet "Something in Xubuntu 12.10 causing trouble with this old ACER 5003 and its SIS chipsets". So i wanted to know if the problem i mentioned while installing ubunutu 12.10 on my acer 5004 laptop was the same kind of problem he was facing while installing xubuntu 12.10.
The only reason i didnt post a new thread was that if he had a solution, i would've used it and if there wasnt a solution i would wait and try 13.04 later this month and check.

---

