---
title: "Problem upgrading to Intrepid"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by lariosa42 on 2008-10-30
Hello,
I am trying to upgrade to intrepid from hardy using the update manager.  I haven't done anything fancy, just following the instructions on the Ubuntu homepage.  The update manager runs through the first steps, but it aborts when it tries to download the very last file, called something like "procps."  

I've tried this a few times with the same results, so I don't think it is my wireless cutting out.  Sometimes when I run the process, I get an "Authentication Failed" error message and have to do it again (which takes quite awhile since Update Manager wants to download the "Upgrade tool" every time).

Can anyone help?  Thanks in advance.

---

### Post by cariboo on 2008-10-30
The first thing to to do is go to System-->Administration-->Software Sources, then click on the Download From drop down and select Other, then click Select Best Server, this will run through the list of servers and select the fastest one. Click Choose Server. Next in a terminal type:

```
sudo apt-get update
```

After it has updated you can use your tool of choice to do the upgrade.

BTW it shouldn't have to download any packages that it has already downloaed, as they are cached and ready to install as soon as all the packages have downloaded.

Jim

---

### Post by lariosa42 on 2008-10-30
Thanks for the response.  I had already used the "Select Best Server," but still had the problem.  I fixed it by restarting and trying it again.  I'm not sure why it worked, but Intrepid is installed now.  Thanks again!

---

### Post by Skip Da Shu on 2008-11-02
> **cariboo907 said:**
> The first thing to to do is go to System-->Administration-->Software Sources, then click on the Download From drop down and select Other, then click Select Best Server, this will run through the list of servers and select the fastest one. Click Choose Server. Next in a terminal type:

```
sudo apt-get update
```

After it has updated you can use your tool of choice to do the upgrade.

BTW it shouldn't have to download any packages that it has already downloaed, as they are cached and ready to install as soon as all the packages have downloaded.

Jim

Disabled my apt-cacher. Tried two different servers. Put my apt-cacher back in (reboots after each change).  Still...

```
Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server. 
```

---

### Post by DaneM on 2008-11-26
I'm having the same problem upgrading from Hardy to Intrepid.  Any help would be great!

---

