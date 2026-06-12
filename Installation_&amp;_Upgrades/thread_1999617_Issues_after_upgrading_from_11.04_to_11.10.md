---
title: "Issues after upgrading from 11.04 to 11.10"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Shdwdrgn on 2012-06-08
I have four servers which have been upgraded to Oneiric in the past week.  The first three servers went smooth, however I have two major issues with the last server which I have been unable to resolve.

The first issue has to do with software raids.  The server does not boot from a software raid, it merely uses them for storage space such as backups, however like many others when I boot my system since upgrading to 11.10, it always drops into an initramfs prompt.  For whatever reason, mdadm has not correctly assembled my arrays at boot since I upgraded to natty, so I dropped in a script under rcS.d that drops md127 and assembles md0.  Now under oneiric, the server cannot restart unattended.

The solutions I have tried are to run "dpkg-reconfigure mdadm" and choosing to boot the system even if the raid is degraded... and also in /etc/default/grub I have added GRUB_CMDLINE_LINUX="bootdegraded=true" and run update-grub.  Both of these solutions failed, and the server still halts at the initramfs prompt at boot.  Ideally I would prefer finding out how to get mdadm to correctly assemble the drives at boot like it used to, but all attempts at changes to mdadm.conf have failed.

My second problem after upgrading to oneiric has to do with IPv6 networking.  I run a dedicated firewall with shorewall6 and an HE tunnel set up.  All of my servers have static IPv6 addresses assigned.  The first three servers worked fine after upgrading, but on the last server, after rebooting, I am unable to send any outbound IPv6 packets outside of the machine's /64 network.  The machine still receives incoming IPv6 packets, and IPv4 works normal.  It is also able to communicate via IPv6 with the other servers in the same /64.

In trying to resolve this issue, I spent many hours going over my network settings, reviewing the IPv6 routes, and finding nothing wrong with what I expected the configuration to report.  Finally I tried simply restarting networking, and IPv6 started working properly.  When I rebooted the server, IPv6 failed again, but once it was booted I manually restarted networking, and IPv6 worked normal once more.  I have to conclude that something in networking is not being started correctly during the original boot?

I would like to get these issues resolved so that the server can correctly boot up unattended again, but cannot seem to find any new info on google that I have not already tried.  Any further help would be appreciated.

---

### Post by dino99 on 2012-06-08
during oneiric to precise, which is LTS, transition, this mdadm were fixed, so setting Precise as your os might be better. Precise has 5 years support.

otherwise try to clean as much as you can the systems, removing the deprecated settings or orphaned libs.

---

### Post by Shdwdrgn on 2012-06-09
Natty has been out for over a year, and oneiric for over 8 months.  Why were the problems with mdadm not addressed when those versions were still fresh?  The issue with dropping to initramfs has been a constant complaint almost since oneiric was released, and yet I still find discussions of folks fighting with the problem up through last month despite having functional raid arrays.  I have spent weeks trying various suggestions to make mdadm recognize my arrays at boot - arrays which were working without error through lucid and maverick - but when it comes down to it, my mdadm.conf matches the output from mkconf (and the info given about each drive in each array), and that should be all that matters.

As far as the networking issue goes, I have compared all the files involved with the network startup... /etc/init/network*; /etc/init.d/networking; /etc/network/if-*.d/*; and /lib/init/upstart-job... All of these scripts have the same size and creation time between the servers that work, and the one which doesn't.  So what has changed in the network startup process on oneiric that breaks outgoing ipv6 on some machines and not others?

---

