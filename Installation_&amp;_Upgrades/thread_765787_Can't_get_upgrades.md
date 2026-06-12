---
title: "Can't get upgrades"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Kingdavid216 on 2008-04-24
I can't download from synaptic manager or even use the terminal to update anything. Anyone else having this problem? Could it be the server is screwed up?

---

### Post by jery_wang2002 on 2008-04-24
I am using Hardy Beta update to RC. I can't see any update in update-manager.

It is blank since two days ago.
The update-manager doesn't ask me to upgrade to released version when I click "Check"

---

### Post by Kingdavid216 on 2008-04-24
I am on hardy heron RC right now, I just can't download anything because it says it can't connect it always says:


0% [Connecting to us.archive.ubuntu.com (91.189.92.2)]

it can't connect, anyone else have this problem?

---

### Post by skoorbevad on 2008-04-24
Same problem here -- I'm using an apt-repository on the local network that's up-to-date completely with the main Ubuntu mirrors.  I've updated my 7.10 distribution completely, but I never get any sort of option to upgrade to 8.04.

Tried an apt-get update && apt-get dis-upgrade, no dice there, either.

Tried changing my servers back to the primary Ubuntu servers, no dice.

This didn't even work for me for the 7.04 -> 7.10 upgrade, either -- do we need to modify our sources.list to show a Hardy source?  Anybody have any ideas?

---

### Post by Awperator on 2008-04-24
> **Kingdavid216 said:**
> I am on hardy heron RC right now, I just can't download anything because it says it can't connect it always says:


0% [Connecting to us.archive.ubuntu.com (91.189.92.2)]

it can't connect, anyone else have this problem?

Yeah the servers are probably a bit stressed right now, I mean a lot of people are playing with Hardy right now so it will definitely put some strain on them as people try to install programs and stuff etc. after they install fresh.

Oh btw, I'm on Hardy final, and us.archive.ubuntu.com is very very slow for me

---

### Post by Joeb454 on 2008-04-24
Server's are running slow still, expect this until early next week :)

And if you are running the Hardy Beta **or** RC and have kept it up-to-date, you are already running Hardy Final, and have been for around 38 hours ;)

---

### Post by Tuxaby on 2008-04-24
My Update Manager gives me access to the upgrade then freezes when I activate it.   Also tried to install a package through Add/Remove to see what would happen.   It performed all functions as expected but downloaded no files.   Next I changed servers and reloaded my Repos and noticed that many failed to load.    Is it likely that the server problems are causing this or do I have my own set of problems?    Lee

---

### Post by Zack McCool on 2008-04-24
You might find it worthwhile to try changing servers.

Go to System | Administration | Software Sources, enter your password, click on the box for "download from:", and select "other...".  Now click on the box to "Select Best Server".  Once it completes, click "Choose Server" and then close the Software Sources window.  There will be a pop-up asking you to update, let it complete.

Now you will have the server that is responding to you with best speed.  This should help a lot.

---

### Post by rafucho on 2008-04-24
Hi!

I was having the same problem with us.archive server. I'm in Colombia, and I ran the "Choose the best server" button from the "Software Sources" menu, and it did ping tests on every server, and now I'm installing with a pretty good downrate...
Regards!

PS: I'm running Hardy final

---

### Post by mrfajita on 2008-04-24
my update manager freezes when it gets to downloading 19th package of repositories, cant install anything with terminal, and everything in add/remove applications says it doesnt support my computer type (i386)

if this isnt because of loaded servers, i will be very disappointed with this LTS release

for the record i am on Hardy Final LTS

---

### Post by Tuxaby on 2008-04-24
Thanks, will give it another try.   Lee

---

### Post by Pumalite on 2008-04-24
Wait a week or so before getting worried. In any case, post:
cat /etc/apt/sources.list

---

### Post by rafucho on 2008-04-24
It should work with pinging the servers....
about your i386 problem... did you upgrade or fresh installed?

---

### Post by rafucho on 2008-04-24
> **mrfajita said:**
> my update manager freezes when it gets to downloading 19th package of repositories, cant install anything with terminal, and everything in add/remove applications says it doesnt support my computer type (i386)

if this isnt because of loaded servers, i will be very disappointed with this LTS release

for the record i am on Hardy Final LTS

try activating the backports (multiverse) repositories...
report to know your stat

---

### Post by bat21win on 2008-04-24
I'm still on 7.10, and no luck with updates or new program installs. I'm assuming it's the server. I'm currently downloading 8.04 via torrents.:)

---

### Post by Techman010 on 2008-04-24
Was having the same problem, then did the "Find Best Server" thing and that fixed it kinda. (Thanks Zach McCool.)  Still slow when installing programs from terminal, but it's something.  It seems like the more popular files, such as my video card drivers are even slower.

But this should straighten out in a couple of days I would think.

Otherwise, it seems pretty solid so far.

---

### Post by m.j.h3@hotmail.com on 2008-04-24
update manager hanging on 15 of 24
mjh

---

### Post by ptcbus on 2008-04-24
I used torrents instead and had no problems downloading the packages for upgrading from 7.10 to 8.04. It was very fast and simple. I have listed my steps here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by mrfajita on 2008-04-24
ok for the update manager hanging, its because of some severe server lag.  i rebooted and everything is working fine now (though its taking about 40 minutes to install 5 applications)

servers are bogged down.  i had to torrent my iso of Hardy as well

---

### Post by denham2010 on 2008-04-24
I had a similar problem with the "downloading x of x" and the updater hanging and then eventually failing. The same issue when I upgraded to Gutsy back in October.

The update manager seems to have issues with non-standard repositories being present in your sources.list.

To fix the problem, I backed up my sources.list file, and then reverted my repositories to the default (and had to remove the additional repositories, including GPG keys, even though they were disabled).

The upgrade process is now running. In the middle of downloading the files at the moment.

---

### Post by Dale61 on 2008-04-24
Sorry, my bad.  I posted a reply, but it was the wrong forum.

However, I tried to bring my HH up to date before the rush, but some servers appear to be down.

No biggie, as I can wait a few days.

---

