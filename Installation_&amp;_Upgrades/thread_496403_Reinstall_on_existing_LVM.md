---
title: "Reinstall on existing LVM"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by ftmch on 2007-07-09
Hi There,

I recently had a power outage whilst my Dapper system was installing some updates and as a result my system is an unstable state. By this I mean that on booting up some drivers fail to load (a bunch of other stuff is reported to fail also), xwindows will not start, I get a text login and when i do I get a /dev/null: permission denied messages over and over until I hit ctrl-c.

I originally installed the system using LVM to set up the hard drive, and I made a volume group for the / and /home and a volume group for my /data. 

I am looking to perform a reinstall over the existing LVM setup with out changing it so I can keep the data on the /data volume group, and reinstall / and /home.

Has anyone had any experience with this, or know if it is possible with the Dapper alternative CD installer?

Cheers,

Mike.

---

### Post by ftmch on 2007-07-10
Anyone?

---

### Post by rockyl on 2007-07-11
I tried to install Feisty a few weeks ago on an existing LVM disk.

There is a known problem where it takes a long time to read the LVM volumes, something like 5 minutes per. I have 7 volumes and it took about 30 minutes. This is after rebooting a number of times because I thought had died, before I check here to find the bug had already been reported.

I also had a problem where my LVM info was swiped out, but I think that was because the preceding partition was swap and I told it to format. I reported a bug on that but never heard anything more.

---

