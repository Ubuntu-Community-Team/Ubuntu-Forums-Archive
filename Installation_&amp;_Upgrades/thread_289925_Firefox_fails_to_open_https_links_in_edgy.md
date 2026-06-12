---
title: "Firefox fails to open https links in edgy"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Master Ar2ro on 2006-10-31
Yes, I know this issue was reported before, but nothing helped me so far and those threads died some time ago.
The problem: after upgrading to edgy firefox stopped opening https links.
I have already tried: reinstalling firefox, installing mozilla-psm package (along with mozilla-browser), removing physically all firefox and mozilla files and installing them again, but so far nothing helped.
I noticed that Mozilla browser does open https websites, to the question is - why doesn't firefox do so anymore? Can anyone help?

---

### Post by gguy on 2006-10-31
Same thing. I've had this problem right along, tried reinstalling, etc. I thought with 2.0 it might work now but no. Konqueror works OK.

---

### Post by Elshadii on 2006-10-31
> **Master Ar2ro said:**
> Yes, I know this issue was reported before, but nothing helped me so far and those threads died some time ago.
The problem: after upgrading to edgy firefox stopped opening https links.
I have already tried: reinstalling firefox, installing mozilla-psm package (along with mozilla-browser), removing physically all firefox and mozilla files and installing them again, but so far nothing helped.
I noticed that Mozilla browser does open https websites, to the question is - why doesn't firefox do so anymore? Can anyone help?

Can you describe how you are getting this error?  I have been trying to reproduce the error by typing some different https url's but they are opening fine.  In what way are you seeing the error?

---

### Post by eholly on 2006-11-01
Firefox loads [www.google.mail](www.google.mail) bookmarked to my mail, the first page showes up, the completeion bare hits 100%, and the window dissapears. When restarting, I get Firefox -Restore Previous session screen. Picking either choices results in the same thing.

Other sites have the same problem.

 E Holly

---

### Post by Master Ar2ro on 2006-11-01
> **Elshadii said:**
> Can you describe how you are getting this error?  I have been trying to reproduce the error by typing some different https url's but they are opening fine.  In what way are you seeing the error?

I get an error every time I try to open ANY https link. It's not on a specific website, but like NO HTTPS links work. The error is a page template in firefox saying that I should make sure I have PSM installed and that this can be a server configuration error. However I don't encounter situations such as the one described by eholly.

---

### Post by simoncullen on 2006-11-05
Bump.  Same problem here.  Nothing I've found so far has helped.  Thunderbird now will not work either.  I cannot check my mail -- also IMAP with SSL auth.  So I think it might be a problem with the SSL libs but again nothing has helped. . . ](*,)

---

### Post by aysiu on 2006-11-05
I experienced it for a little bit--turned out one or more of my extensions were interfering, for whatever reason.

I think the culprit was TabMixPlus, but there may be other extensions as well.

---

### Post by simoncullen on 2006-11-06
Do other people with this problem also find that Thunderbird wont connect to IMAP servers using SSL?  What components are common to the two?  I have tried downloading and using non-Ubuntu versions, but they too wont work.  I thought it might have been a problem with my IP Tables --- but this seems to be ruled out by Konquerer working all right?

Simon

---

### Post by Metlin on 2007-02-03
I'm facing the same problem - I've tried everything with no luck whatsoever.

Everything works perfectly fine on Opera, but it just does not seem to work with Firefox. Any ideas?

I [posted this question elsewhere]("http://www.ubuntuforums.org/showthread.php?t=352686"), but I am hoping folks here might have an answer.

Thanks.

---

### Post by kvorion on 2007-02-04
I just got connected to the internet from my edgy box. My firefox is fresh, without any plugins whatsoever. Even I am facing the same problem. Has anybody found out a solution yet?

---

### Post by kvorion on 2007-02-04
I have tried reinstalling firefox but it still gave me the same problem. One of my friends suggested I try using swiftfox (Swiftfox is an optimized build of Mozilla Firefox for Linux). Even that did not work. I have run out of options now except installing some other web browser.

---

### Post by Metlin on 2007-02-04
I found a fix - I am not sure where I saw it (think it was on the forums here), but I basically wrote the following script - 

[INDENT]     #!/bin/sh
    killall firefox-bin
    mv .mozilla .mozilla-old
    firefox &[/INDENT]

I have that in my home directory and everytime FF acts up, I execute it and things seem to work fine.

---

### Post by kvorion on 2007-02-06
Even that is not working for me. I really want to stick to firefox if possible. Trying to avoid other browsers.  But its getting more painful with the day not being able to check mail when working with linux.

---

### Post by ozPATT on 2007-02-08
wow, I upgraded to edgy some time ago, and I have had no problems until a couple of days ago. I am wondering if there has been some update that has killed it... I can't access any https sites at all through mozilla... and all the forms which should automatically remember my login details, no longer do..

bring on the feisty fawn I say...

---

### Post by jbozster on 2007-02-10
My firefox installation appeared to break after I upgraded to the new ubuntu provided kernel 2.6.11. I fixed the problem by re-installing the firefox packages via synaptic package manager.

---

