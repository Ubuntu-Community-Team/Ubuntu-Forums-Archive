---
title: "Dapper DHCP Disaster"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by drstamm on 2006-06-15
I recently upgraded (technically clean install) my P4 Dell Dimension Desktop from Ubuntu Breezy to Dapper using the LiveCD.  Once the install was final, and I signed in to my new account, I attempted to use Firefox for some casual browsing.  When it appeared to take too long "Looking up www.google.com," I unplugged my ethernet cable and reinserted it.  The web site loaded nearly instantly thereafter.  I continued browsing for about three minutes until I encountered the same problem.  Again, re-plugging the ethernet cable works.  

Over the course of the past week, I have been trying to pinpoint the problem by reverting to Breezy (which worked), installing from a newly downloaded LiveCD (which did not), installing from a text-mode installer (again, no dice).  Preemptive note: I did check the MD5 checksums each time.  I am, in fact, posting this from inside the Dapper LiveCD environment, which supports my connection.

After looking through the forums (and trying the proposed solutions) I can perhaps place the issue at:
[LIST]
[*]A DHCP Lease inconsistent with the system time (maybe UTC issues)
[*]Driver conflicts (module unload solution ended in complete unusability of network)
[*]ifupdown errors (unsure how to fix, if so)
[/LIST]

The system monitor shows my network connection as consistently receiving data, but only showed information being sent in the periods immediately after un-/re-plugging.

My question:  
Is there a permanant change I can make to a config file or a console trick to correct this?

Thanks in advance to the Ubuntu community.

---

### Post by ljoris on 2006-06-15
Please provide your network-card type etc.

Also, run

    rcconf

as root to verify any 'odd' services running wich might interfere with your network/IP traffic. Also verify any settings in firefox.

---

### Post by drstamm on 2006-06-15
Network Card Info (from Device Manager):
   Vendor:  Davicom Semiconductor, Inc.
   Device:  21x4x DEC-Tulip compatible 10/100 Ethernet

rcconf Output:
   bash: rcconf: command not found

The settings in Firefox are all defaults; the same problem occurs when downloading packages with apt-get and other browsers, such as Opera.  This appears to affect any task trying to access the Internet.  I repeat that all Internet-related tasks work very well, but only for a short time after 'resetting' the connection.

The output is the same for the LiveCD environment (which does work).

Thank you Joris,

D. Stamm

UPDATE:  I was able to install the latest set of updates (after much un-re-inserting the ethernet cable) over the Internet, and the problem is no more.  Thanks.

---

