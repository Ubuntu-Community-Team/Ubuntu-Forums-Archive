---
title: "Ubuntu Server standard setup"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by Jorel on 2012-07-17
Hi guys,

Im not yet decided on how i will build my Ubuntu Server,, im currently running it on a i386, RAM 4gb, 1 LAN card and i build it as a ext4 File server having:

Primary / (20gb)
Primary /boot (500mb)
Primary /swap (2gb)
Logic /home (5gb)
Logic /opt (5gb)
Logic /srv (5gb)
Logic /tmp (5gb)
Logic /usr (5gb)
Logic /usr/local (5gb)
Logic /var (5gb)
Logic /jorel (100gb)

and apps of OpenSSH and Samba server...

That probably in the future i'll upgrade it on to 64 bit Ubuntu Server, amd64 (i3 or i5), RAM 6gb, and i dont know yet if ill include web server, cacti for monitoring, fire wall and gateway build...

so can you suggest me something that can be my basic for all that ill be adding in the future?? because its like a one-server-for-all type build (if it can be)...

Thanks in advance... :)

---

### Post by Lars Noodén on 2012-07-17
I would recommend doing a throw-away installation with everything in one partition.  Install everything you want and then see how the storage is used.  Then wipe it and do a re-install setting the partitions based on your actual usage.  

For example /usr and maybe /usr/local are going to be much bigger.  Nearly all programs without exception that come from the repository are going there.  On the other hand /opt is not going to be used at all unless you are going to run [VistA](http://www.ashinstitute.harvard.edu/Ash/pdfs/VAVistAreleasefinale.pdf) or other unusual packages.  

What are you planning to achieve with your partition layout?  W^X ?

---

### Post by Jorel on 2012-07-17
Hi Lars,
because these coming days ill be upgrading my server, but everyone especially my boss is not yet decided on what to do on it yet, because i think it can be more useful to add extra functions on the server in the near future than just being a file server alone.

> **Lars Noodén said:**
> I would recommend doing a throw-away installation with everything in one partition.  Install everything you want and then see how the storage is used.  Then wipe it and do a re-install setting the partitions based on your actual usage.  

so you mean here is that on my current server, i'll install everything that i wanted then (df -h) to see how it occupied my HDD?

> **Lars Noodén said:**
> What are you planning to achieve with your partition layout?  W^X ?

can we be not so technical in this thread? coz im still a newbie on handling Server especially Ubuntu and this is my 1st break on handling one (and hope to last)...

thanks..:P

---

### Post by Lars Noodén on 2012-07-17
You can use [du](http://manpages.ubuntu.com/manpages/precise/en/man1/du.1.html) to measure how much specific directories and subdirectories use.  

```

du -sh /usr/local

```

Once you've installed everything including the kitchen sink, you can visit the various directories with du and see how much they use.  Then base your partitioning scheme on the usage.  Be sure to pad a bit to leave room for updates.  Your data directories (/var and /home) might not be amenable to that method and you'll have to make your best guess instead.

(Write XOR Execute ([W^X](http://en.wikipedia.org/wiki/W%5EX)), mean that either a file is writeable or it can be run, but not both.  At the level of detail you seem to be looking at for your directories, it is easy to set up.  As a beginner it is something your should know about so that later when you have become comfortable with things, you can set it up.  It's not hard once you understand the [layout](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) of the system.)

---

### Post by TheFu on 2012-07-17
> **Jorel said:**
> Hi guys,

Im not yet decided on how i will build my Ubuntu Server,, im currently running it on a i386, RAM 4gb, 1 LAN card and i build it as a ext4 File server having:

Primary / (20gb)
Primary /boot (500mb)
Primary /swap (2gb)
Logic /home (5gb)
Logic /opt (5gb)
Logic /srv (5gb)
Logic /tmp (5gb)
Logic /usr (5gb)
Logic /usr/local (5gb)
Logic /var (5gb)
Logic /jorel (100gb)

and apps of OpenSSH and Samba server...

That probably in the future i'll upgrade it on to 64 bit Ubuntu Server, amd64 (i3 or i5), RAM 6gb, and i dont know yet if ill include web server, cacti for monitoring, fire wall and gateway build...

so can you suggest me something that can be my basic for all that ill be adding in the future?? because its like a one-server-for-all type build (if it can be)...

Thanks in advance... :)

I've been building and running servers since 1996 and only once did I need something with lots of different partitions.  To me, and this is just an opinion, you are over complicating it A - LOT.

/
/boot
/var
/home (or /u/ to keep the path shorter) 
/data ( or /d/ to keep the path shorter)

Covers just about everything people need these days.  You can use softlinks to force any directories that get really large over to /data somewhere.

If you are mounting all these from a SAN and want the LUNs to be small as possible, then getting complicated might make sense.

If you want to split out different major apps, then perhaps making a KVM virtualization server would make sense instead? Then you could easily create small VMs to try new applications without much risk to other, running apps.  Just a thought.

FYI, even our Zimbra VM doesn't use 4GB of RAM, just 1.8G.  The server runs about 5 other VMs running CRM, DMS, and a few other major apps too. It is very happy with 4GB of total storage for each VM in a single partition.

---

### Post by Jorel on 2012-07-17
probably thats the thing i needed to know,,, i will dig on those and will return on this thread one of these days for my progress...

still im open on any suggestions especially on hardware that i'll be including on my upgrade (like having 2 LAN card for setting up a firewall and gateway, if what i know is correct)

thank you very much Lars...

Hi TheFu,

sorry im slowly digesting things here,, these is the basic set-up that i know for a file server,, and im beginning to understand that i may need to exclude some mounts (due that they are not useful)...

thanks TheFu....

---

### Post by TheFu on 2012-07-17
> **Jorel said:**
> probably thats the thing i needed to know,,, i will dig on those and will return on this thread one of these days for my progress...

still im open on any suggestions especially on hardware that i'll be including on my upgrade (like having 2 LAN card for setting up a firewall and gateway, if what i know is correct)

thank you very much Lars...

Having 2 physical NICs for a firewall is required.  Firewalls generally need to be single-purpose devices, especially for a business. Firewalls need to be locked down much more than internal servers.  Adding other services to a firewall machine is an added risk that is easily avoided.

I'm not saying that you can't do it, just that it is a really, really, really, bad idea.

---

### Post by Jorel on 2012-07-17
> **TheFu said:**
> I'm not saying that you can't do it, just that it is a really, really, really, bad idea.

ahhhh that's why sometimes i seeing a typical computer for Firewall/gateway,,,

---

