---
title: "Upgrading 6.06 SERVER"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by pleb on 2007-05-05
Is it just me, or is there absolutely no documentation on how to upgrade the 6.06 server distro?
I've officially given up googling, and that's why I'm here.
Can anybody give me a reliable method of upgrading 6.06 to at least 6.10 so I can use the update package to further upgrade?
The only upgrade threads I can find are for the GUI, or the solution being to apt-get the desktop disto...

Failing a reliable upgrade, I can go ahead and install from scratch, I guess. So, can anyone confirm for me that Feisty doesn't have that issue when syslog restarts at 6:30am everyday, causing other processes to restart?

---

### Post by Big Ed on 2007-05-06
I haven't tried this myself.  I was running my server on Slackware until a few months ago.  But this seems to be a working solution:

# cd /etc/apt
# cp sources.list sources.list.dapper
# sed 's/dapper/edgy/g' sources.list > ed
# mv ed sources.list
# apt-get update
# apt-get dist-upgrade

Found it at the bottom of this page:
[http://www.odrakir.com/blog/category/computer-stuff/linux/](http://www.odrakir.com/blog/category/computer-stuff/linux/)

Note that this example shows a root shell.  As a user, you'll need 'sudo'.

HTH,
Ed

---

### Post by pleb on 2007-05-08
Nice find! Thanks for that. I'll give it a shot tonight perhaps and let you know how I went.

---

### Post by pleb on 2007-05-08
Hmm.. Well that ended up destroying my kernel.. I think..
There was some bs error about a cache file when dpkg was cleaning up. Being unsure as to whether or not the distro had upgraded fully or not, I foolishly rebooted. Now I get booting kernel and nothing more. No error occurs. Without an error, I'm fked for a solution!
Oh well, it was worth a shot. I'll go ahead and mark down 6.06 server as non-upgradeable in the history books.

---

### Post by Big Ed on 2007-05-08
> **pleb said:**
> Hmm.. Well that ended up destroying my kernel.. I think..
There was some bs error about a cache file when dpkg was cleaning up. Being unsure as to whether or not the distro had upgraded fully or not, I foolishly rebooted. Now I get booting kernel and nothing more. No error occurs. Without an error, I'm fked for a solution!
Oh well, it was worth a shot. I'll go ahead and mark down 6.06 server as non-upgradeable in the history books.

Can you boot from a live cd then reinstall both the kernel and grub?

Ed

---

### Post by pleb on 2007-05-09
That's the plan! I should be right from here. Thanks for your help though.

---

