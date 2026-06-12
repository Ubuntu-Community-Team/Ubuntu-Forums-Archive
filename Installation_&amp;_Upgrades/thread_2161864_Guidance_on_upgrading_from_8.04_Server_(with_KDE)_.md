---
title: "Guidance on upgrading from 8.04 Server (with KDE) to something more current"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by Chris of Arabia on 2013-07-12
Hi all,

It's a long time since I've posted round here, so excuse my tardiness in saying hello.

My 8.04 server has been somewhat neglected for a while due to life getting in the way, and I can't help feeling it's time it was moved up to something more current - probably to the 12.04.2 LTS version. Whilst it is a server I'm running, I do have the KDE installed on it, as it makes my relatively inexperienced dabblings somewhat easier. Mostly I use the box as a webserver for testing a few things out, so it's not in anyway accessible to the world, or in any way productionised.

What I need is a little guidance on how to move it up to 12.04.2. Whilst I've gone through Adept and tried to follow the 'Version Upgrade' route, this isn't working, as I keep getting a message saying "Could not download upgrade tool. Please check that your Internet connection is active" - rest assured, it is, it's where I'm typing this post from.

So what would your approach for this be? I guess the least complicated route would be the best for me, given me relative novice status.

All help appreciated. :)

---

### Post by p-dh on 2013-07-12
Hi,
I first installed Ubuntu 9.04 as a server for my eeebox. It's a great little box and ran just fine. When 10.04 came out, I upgraded it from 9.04 (through 9.10). A few months ago, I upgraded it from 10.04 to 12.04. I have not had any problems upgrading this way. There's not a lot of cruft as I use it as a file-print server. I have not wanted to do a new installation as it's pretty tweaked with Samba, etc. and I didn't want to go through the trouble of reconfiguring everything - especially rights.
On other computers (including servers), I have blown away everything and reinstalled (after having backed up everything first). I have had no real problems and have been able to get everything reinstalled and configured within a couple of hours.
From the sounds of it, you should probably back up what you don't want to lose, and reinstall. If not, you will need to do in-place 8.04 to 10.04 to 12.04 upgrade - an all-day (at least) process. This may be the cause of the error message - if you're trying to go directly from 8.04 to 12.04. 
If you decide to do a complete reinstall, I'd encourage you to install webmin on your server. You can also install basic x-windows. These two things will allow you to remotely manage the server, rather than having to install a complete graphic shell like KDE.

Hope this helps.

Peace,
Paul :cool:

---

### Post by Chris of Arabia on 2013-07-30
I ended up doing a complete reinstall and ended up with the 64-bit 13.04 server installation, plus the KDE. There are a few tweaks needed to get it exactly where I want, but I'm up and running. Thanks

---

