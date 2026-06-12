---
title: "SVN server not responding after upgrade to 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Falc on 2008-04-26
I have a little home server, which among other things runs an svn server for me.

It was configured to run using inetd:
[QUOTE="inetd.conf"]svn stream tcp nowait falc /usr/bin/svnserve svnserve -i -r /home/falc/subversion[/QUOTE]

However, since my upgrade to 8.04 two days ago, it no longer works this way. When I try, it tells me that the server 'actively refused' the connection. Starting the server manually (svnserve -d) does work, so my conclusion seems to be that it's this whole inetd functionality that's no longer working...

Has there been a change in syntax? Something else?

EDIT:

Aha, there was indeed an upgrade from inetd to xinetd. For some reason, the upgrade copied my svn config to the new format but added a 'diasble = no' line to it... After correcting the typo it's now working.

---

