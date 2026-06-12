---
title: "Upgrade from 14.04 to 15 - failed"
date: 2016-01-12
forum: Installation &amp; Upgrades
---

### Post by thanealex on 2016-01-12
Hello all, 
I had ubuntu 14.04 and when attempted to upgrade to the newest 15.xx disrto yesterday the following happened:

1. It downloaded the newest packages OK.
2. The installation started in about an hour OK.
3. The the screen locked, only showing the username and password box as well as Guest login prompt. Neither worked, the screen remained locked. Left it for the rest of the night but no change until this morning.
4. Attempted using boot-repair (as explained here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))
5. It didn't work and the error URL is this: [http://paste.ubuntu.com/14476569/](http://paste.ubuntu.com/14476569/)

Your ideas are welcome as I'm not quite an expert in ubuntu.
Thanks

---

### Post by kansasnoob on 2016-01-12
The boot info summary shows you did upgrade to 15.04, at least partially, which is what currently happens if you change the software update settings to show upgrades from an LTS to any new version rather than the default LTS only:

[ATTACH=CONFIG]266700[/ATTACH]

That was a rather bad choice anyway since 15.04 will reach end of life later this month:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So within just a couple of weeks you'd have needed to upgrade to 15.10. That being the case, and since Ubuntu appears to be the only OS installed on that computer, if you create a 15.10 (Wily) live DVD or USB the installation process should offer an upgrade similar to this:

[ATTACH=CONFIG]266701[/ATTACH]

Note; I realize that's an old screenshot but the UI has not changed significantly.

Of course anytime you mess with the installer you should first create a backup of anything important.

---

### Post by thanealex on 2016-01-13
Understood. Thanks a lot Kansasnoob. I lost nothing for it was a fresh installation of the 14.04 over which I attempted to instal the 15.
Admins can lock the thread.

---

