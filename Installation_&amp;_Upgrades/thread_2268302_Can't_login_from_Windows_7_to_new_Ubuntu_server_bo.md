---
title: "Can't login from Windows 7 to new Ubuntu server box"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by dadu007 on 2015-03-07
Hi All,
Totally new to Ubuntu.  My company unloaded a lot of old PC hardware and I nabbed a Dell Precision 3500 Xeon machine, which I am trying to set up as a personal web server.
I searched for tutorials on this and ended up following this one:

[http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/2/](http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/2/)

I easily made it to point where I can paste the ip of the new server in the address bar of IE on my Windows 7 (64-bit) machine and get the "Welcome to nginx on Debian!" message.  So far, so good.

Now, just so this will be a "black box in a closet server", I am trying to login to the server from my Windows 7 machine and I am not having any success...Started out trying it with Putty and then Cygwin and then combo of the two, but I only end up with "Network Error: Connection refused" all the time

I've tried adding port 22 in my router to port forwarding, but no success with that.

Please help!  I can't seem to find the magic tutorial for that one...  (the arstechnica.com tutorial sure seems to imply you know a lot of stuff!)

Thanks for any help for this newbie.

---

### Post by DennisFolsom on 2015-03-07
In a prior life, I did something like you are trying to do with VNC.  That might work for you.

Also, more recently, I had a Terminal set up from my Android tablet to my older Ubuntu PC using Juice on the Android and an SSH connection.  However, something broke in my configuration and I haven't gotten around to trouble-shooting it.  Anyway, a terminal program on your Win7 machine and an SSH connection might do the trick, if you only need character terminal access.

---

### Post by dadu007 on 2015-03-07
It always happens this way...I struggle and struggle for a few days, then post to a forum.  Shortly after posting, I find the solution elsewhere!

And the solution was:  Added the server's ip address and host name to the Windows host file in C:\Windows\System32\drivers\etc.   Argghh...

I am now able to log in. 

Thx!

---

### Post by DennisFolsom on 2015-03-07
dadu007 -
Good to hear that your problem is fixed.
Meanwhile, I have worked out my SSH connection problems and can now easily connect form my Android Tablet to either my Ubuntu 14.04 machine or my Ubuntu 12.04 machine.

---

