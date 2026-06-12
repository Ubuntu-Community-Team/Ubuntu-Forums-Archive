---
title: "Curious email from root about font paths in XF86Config-4"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-03-31
I just realised today that I was sent this email locally back when I installed ubuntu.

What's it about?

> 
From [email]root@localhost.loca[/email]ldomain  Fri Feb  4 17:23:27 2005
X-Original-To: root
To: [email]root@localhost.loca[/email]ldomain
Subject: Debconf: Configuring x-ttcidfont-conf -- FontPath of TrueType and CID managed by defoma is changed
Date: Fri,  4 Feb 2005 17:23:27 +0000 (GMT)
From: [email]root@localhost.loca[/email]ldomain (root)

TrueType and CID font paths which defoma manages have changed again.
Please add these entries to the "Files" section of /etc/X11/XF86Config-4:

  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"


Also add these two directories to the "catalogue" path lists in
/etc/X11/fs/config and/or /etc/X11/fs-xtt/config, and delete any mention
of /usr/lib/X11/fonts/CID in any of these files.

--
Debconf, running at localhost.localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]



---

