---
title: "Do I have to use the repositories for the version ubuntu I'm running?"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by chamstar on 2008-07-17
I have two server installs, one is Dapper, one is Hardy... On the Hardy install I can apt-get denyhosts (ie. its in the repos) but on Dapper it cannot be found. Can I update the Dapper repos to some newer version or is each repos particular to the installed version?

If this is the case I guess I will have to download and install a .deb 'manually' on Dapper?

Cheers Cham!

---

### Post by tuxxy on 2008-07-17
Just add the repo in software sources :)

---

### Post by Archmage on 2008-07-17
You can't mix the repos of different versions. Consider upgrading your Dapper to the next LTS (Hardy).

---

### Post by Sef on 2008-07-17
> Archmage  	
Re: Do I have to use the repositories for the version ubuntu I'm running?
You can't mix the repos of different versions. Consider upgrading your Dapper to the next LTS (Hardy). 

Archmage is correct. If you mix version repositories, you will need to reinstall your system.  If you don't want to upgrade your system, you could download the [tarbell]("http://sourceforge.net/project/showfiles.php?group_id=131204&package_id=143910").

---

### Post by chamstar on 2008-07-17
Thanks for the replies people. I downloaded the tar and installed. Of course I dont get automatic updates this way but still it works :)

I would like to upgrade but its a production web server and i'm a bit worried incase anything goes wrong. I could cope with a bit of downtime but I dont think would be too easy to reverse a broken upgrade.

I've upgraded my desktop ubuntu several times and only ever had problems with my dual monitor (nvidia) drivers. Of course this would not be a problem on a server!

To upgrade or not?!?

I would use: [http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/](http://ubuntu-tutorials.com/2008/04/03/dapper-to-hardy-direct-server-upgrade-works/)

---

### Post by timcredible on 2008-07-17
.

---

### Post by chamstar on 2008-07-18
Sorry I didnt hear what you said Tim :)

---

### Post by louieb on 2008-07-18
> **chamstar said:**
> ...its a production web server ..... but I dont think would be too easy to reverse a broken upgrade.

I use partimage on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  to backup my machine before version upgrades and kernel updates. The machine is down for an hour or so for the backup. 
If the upgrade work fine. If not complete restore is just another hour or so away.

---

### Post by chamstar on 2008-07-18
Unfortunately the machine in question is a virtual machine on a server to which I have no physical access otherwise your suggestion would be perfect, I've used SystemRescueCd before and its great for working with partitions.

I might have to see if the hosting company will do a one time backup...

---

