---
title: "Issue with older packages on 6.06 LTS (dapper)"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by stmurray on 2008-02-13
I have a machine running Dapper that I use as a firewall, ids, etc.  In the past I have run into issues that the current version of a package in Dapper is dated and wouldn't work when it interacted with other machines (Tor was one of those packages).

Now I have installed Prelude on a Gutsy box as a log consolidator and I want to send my snort and syslogs from my dapper box to that.  I am having an issue getting the prelude to connect from my Gutsy to my Dapper box.  From various sources it looks like it may be a problem with the version of gnutls that Prelude uses to communicate.  The older version (although it is the latest that apt-get shows me from the Dapper sources) has a problem with the newer version (the current version for Gutsy) 

As I see it here are my options:
1)  Upgrade Dapper-  I tried to do this by runninng gksu "update manager -c", but the option to upgrade to Edgy does not appear (if I do a gksu "update mangager -d" the option to upgrade to hardy does appear, but I'm don't want to run that, yet, on this box).  I could try the manual method of upgrading and hope for the best
2) Install the later versions of Prelude and gnutls manually outside of apt-get.  I'm hesitant to do that, because then I have to make sure it stays up to date and there are several other packages that have to be upgraded in order for the Prelude update 
3) Somehow go back to the older versions of Prelude and gnutls on the Gutsy box.  I am unsure how to go about this, as I sure there will be dependancy problems.

Is there any option I am missing?  What is the best option?  Does this happen often when use the TLS ubuntu distro?

All help appreciated

Thanks!!

Sean T Murray

---

