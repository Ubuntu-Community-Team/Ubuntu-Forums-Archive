---
title: "Updating from 6.06 to 6.10"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by PasiM on 2008-01-19
I'm trying to upgrade my Ubuntu 6.06 to 6.10. In terminal I type 'gksu "update-manager -c"', password is asked, update-manager starts, but there's no option to upgrade. Actually no any kind of updates are available.

I asked this in IRC #ubuntu channel, and got quick answer that "6.06 and 6.10 are not an upgrade path due to one being lts and non-lts the other" and "you need to change the repo's manually". However, I do not have any idea how to "change repo manually" :-)

However, from pages [https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes) and [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) I understood, that it should be enough to execute command mentioned above and update-manager should offer to upgrade to 6.10?

PS. I do not mind to update directly to 7.xx if it's possible from 6.06.
PSS. If I run 'gksu "update-manager -c -d"', updatemanager is offering upgrade to 8.04

---

### Post by PasiM on 2008-01-21
No ideas from anyone? Problem still exists :-(

Can anyone using Ubuntu version 6.06 try to type that **gksu "update-manager -c"** to console and see if update manager offers to upgrade to 6.10? Or is problem only with my Ubuntu installation? Or have I just totally missed something here. I've also tried to run updtmngr with command 'gksu "update-manager --check-dist-upgrades"' even though I guess it doesn't mean anything different than just -c.

If this is any help, I get this kind of warnings to console. Appear after password is asked but before update-manager starts.

pasim@Moya:~$ gksu "update-manager -c"
  warnings.warn("apt API not stable yet", FutureWarning)
pasim@Moya:~$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
pasim@Moya:~$

Thanks!

---

### Post by abatis on 2008-01-29
gksu "update-manager-d -c"  worked for me. I am going from 6.06 LTS directly to 8.04LTS. Thought I would have to 7.04 etc but that is not the way it happeded. use the -d in front of -c.  Good Luck

---

### Post by zvacet on 2008-01-30
If you don´t have some special reason to upgrade wait until april and upgrade to Hardy wich is also LTS.

---

### Post by PasiM on 2008-01-31
Thanks to both! I guess I'll wait for (final) 8.04... Hopefully my update-manager just offers to upgrade to it then :-)

---

