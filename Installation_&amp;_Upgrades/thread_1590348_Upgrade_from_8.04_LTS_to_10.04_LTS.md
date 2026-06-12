---
title: "Upgrade from 8.04 LTS to 10.04 LTS"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by josir on 2010-10-07
Hi folks, I want to upgrade 8.04 server to 10.04
I tried to to folow this tutorial:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

But when I issued:

  sudo do-release-upgrade --devel-release

I got:

Checking for a new ubuntu release
No new release found

I also try this instructions:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

But I got no clue.
Does somebody has any tip on how to do this upgrade ?



Thanks in advance,
Josir Gomes

---

### Post by josir on 2010-10-07
I fill the proxy configuration on the Gnome and I could use the graphical interface.

In the console, it did not work though...

---

### Post by corcomp84 on 2010-10-07
why are you using the server version? with 10.04 there is very little deference's between the server and desktop, other than the GUI and a few other things..  Plus when you upgrade with the update manager most of the time it crashes and you are left having to clean install anyways..

---

### Post by josir on 2010-10-08
Hi corcomp, 

because it's a server! :)

I just can access the machine remotely (via SSH) and most of the time, I don't have access to the physical server.

Even the machine is near, server edition is better for maintenance: 
when I upgrade it, I don't need to download OpenOffice, Rythmbox and all GUI stuff. 

And it doesn't load bluetooth, avahi and other desktop services!

Thanks for your reply anyway.
Josir.

---

### Post by corcomp84 on 2010-10-08
I am sorry for the crappy reply but you never know, I tried the server version and found little difference once configured right.. Did you check and make sure your software sources were ok, maybe they were disabled.  Its just an idea, I am not sure what its like for updates on a server, and how they work.

---

### Post by josir on 2010-10-10
Hi corcomp, 

no problem at all. We all are to share opinions!

The update process for server is exactly the same. The only difference is that you don't have the GUI tools. You have to count on console only.

Usually it works. But this 8.04 to 10.04 especifically didn't.

Health and freedom,
Josir Gomes

---

