---
title: "Bad Archive Mirror - while preseeding"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by rahmath on 2008-08-05
Dear Techies,

I am trying this preseeding for the first time. Now when i started from the ubuntu client with netboot image with the url=server/path-to-preseed.cfg, it connects to web server where i stored the preseed file and the installation source, and go up to the
"choose a mirror of the Ubuntu archive"

there, it say's the following error message and stop.

Bad archive mirror
The specified ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.

Anybody have any idea... how to get moved from this stage???


I tried;

In the log file, (Alt-F4) it shows wget -q [http://.](http://.)...... Release.... 

first, i thought it might be some problem in accessing this file, but when i opened the console (Alt+F3) and executed this same wget command, things are working, so i am 100% sure, its not the problem in accessing this file... 


From this same LAB settings, i can boot from this same ubnutu client with this same netboot image, and can do the normal installation (without preseeding) by connecting to this same web server.

So, we can't conclude that, the problem is with;
1, Release file
2. Installation Server
3. netboot image
4. network settings

then i guess it should be some where in the preseed file ( but the information regarding the wget which it fetched from preseeding manually works in the console!!!!!!!!!!!!)

Now i am totally unreachable!!!!!!!!!!! out of coverage!!!!!! lost the control.... i cant find out where the problem is.....

almos for the last 5-6 hours i am stucked with this probs.... 

I tried googling, but no hope....

Awaiting some inputs to this procedures...

Thanks in advance...

---

### Post by felixvah on 2008-09-18
I'm having the same problem if you find out the answer can you please let me know.  I've been stuck on this proble for 24 hours now.  send me the answer to [email]info@shopcheaply.com[/email].  thanks in advance.

---

### Post by skmah on 2013-03-14
> **felixvah said:**
> I'm having the same problem if you find out the answer can you please let me know.  I've been stuck on this proble for 24 hours now.  send me the answer to [email]info@shopcheaply.com[/email].  thanks in advance.


A little late on the reply but...
I've been searching the answer for a while. Hopefully this will help someone that runs into the same preseed problem.
Make sure you use the correct proxy setting.

d-i 	mirror/http/proxy 		string
leave it blank if you install from a local mirror, and use a proxy if your network uses a proxy server.

-Steve

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

