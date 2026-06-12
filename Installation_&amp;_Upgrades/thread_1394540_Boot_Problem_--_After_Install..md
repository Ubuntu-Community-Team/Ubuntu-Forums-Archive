---
title: "Boot Problem -- After Install."
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by YourMomsASmurph on 2010-01-30
New Problem :::
 
Hokay so Fixed the boot error last time by resinstalling ubuntu and not encrypting harddrives.

Now, Have been on the system for a few hours now, installed basic programs like wine,flash,divx,Ajour(what ever the cpp ide is called)

I then went to customize my desktop -- and there was an option to enable desktop effects. -- I did so it said it needed to install a NVIDIA driver.

After the driver installed I reset my computer and when starting a prompt came up saying there was something wrong with the display settings -- It gave me the option to run in low-quality for one session, and i took it. I then restarted again, and now after the ubuntu splash screen my moniter shuts off...

Any idea how to use recovery mode (using terminal) to reset it to a default video driver, thus solving this problem.

---

### Post by kansasnoob on 2010-01-30
Look at these two notations in the early release notes:

> Login screen presented before optional filesystems are mounted

With the new upstart-based boot process in Ubuntu 9.10, the X server will be started, and the login screen launched, as soon as the core filesystems are available. This means that optional filesystems, mounted at locations not required for the system to boot, may not be mounted yet at login time, and may even fail to mount in the case of a filesystem check error.

Users who prefer the previous behavior of waiting for all filesystems to be mounted before launching the login screen can add the bootwait option to these filesystems in /etc/fstab. (439604)
Optional encrypted partitions must be marked bootwait in /etc/fstab

In addition to the above, users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab if they are not mounted at a standard system mountpoint. Failure to do this on a desktop system will lead to problems from the X server and cryptsetup trying to control the console at the same time. At best, this will prevent the user from seeing the passphrase prompt; at worst it will also cause the X server to spin and consume 100% CPU. (430496) 

Link:

[http://www.ubuntu.com/getubuntu/releasenotes/910#Optional%20encrypted%20partitions%20must%20be%20marked%20bootwait%20in%20/etc/fstab](http://www.ubuntu.com/getubuntu/releasenotes/910#Optional%20encrypted%20partitions%20must%20be%20marked%20bootwait%20in%20/etc/fstab)

The bug reports they refer to (pay close attention to the latter):

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604)

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430496](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430496)

Also here:

[http://www.firmotech.com/lurker/message/20091207.081616.f10108c1.en.html](http://www.firmotech.com/lurker/message/20091207.081616.f10108c1.en.html)

And here:

[https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Optional%20encrypted%20partitions%20must%20be%20marked%20bootwait%20in%20/etc/fstab](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Optional%20encrypted%20partitions%20must%20be%20marked%20bootwait%20in%20/etc/fstab)

Why encrypt SWAP?

---

### Post by YourMomsASmurph on 2010-01-30
New Problem :. Thread Bumped.

---

### Post by kansasnoob on 2010-01-31
> **YourMomsASmurph said:**
> New Problem :::
 
Hokay so Fixed the boot error last time by resinstalling ubuntu and not encrypting harddrives.

Now, Have been on the system for a few hours now, installed basic programs like wine,flash,divx,Ajour(what ever the cpp ide is called)

I then went to customize my desktop -- and there was an option to enable desktop effects. -- I did so it said it needed to install a NVIDIA driver.

After the driver installed I reset my computer and when starting a prompt came up saying there was something wrong with the display settings -- It gave me the option to run in low-quality for one session, and i took it. I then restarted again, and now after the ubuntu splash screen my moniter shuts off...

Any idea how to use recovery mode (using terminal) to reset it to a default video driver, thus solving this problem.

Gosh I'm woefully ignorant regarding graphics problems.

I would however recommend starting a new thread with an appropriate title to draw the attention of those who do know their way around Xorg.

Oops, I see you did change the title. Consider this just a bump.

---

