---
title: "Can I force upgrade to 14.10 and not to 15.* (from 14.04)"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by klemen3 on 2015-11-03
Can I force upgrade from 14.04 to (just) 14.10 and not to 15.04 or 15.10 (as the update managers want to)?

---

### Post by sudodus on 2015-11-03
Welcome to the Ubuntu Forums :-)

The Ubuntu version 14.10 has passed end of life and is no longer supported, not even security updates. I would recommend that you keep the version 14.04 up to date or make a new installation of 15.10. 14.04 LTS has long time support. The next version with long time support will be 16.04 LTS, to be released in April 2016.

If you still want 15.10, try it before you install it.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by klemen3 on 2015-11-03
Yes, I understand all of that.

The upgrade process (this is a virtual machine) doesn't go through (14.04 to 15.04), so we are wondering if maybe (14.04 --> 14.10 --> 15.04) would work.

Don't ask me about the error (for now), I will post that later and elsewhere.

---

### Post by sudodus on 2015-11-03
It was a recommended path before the end of life of 14.10. But I think the repositories are closed for 14.10, so you cannot update/dist-upgrade it to make it up to date, which is important before the next step to 15.04.

An alternative that is used by many users and might work well for you too:

1. Backup your current system, because upgrading to a new version is risky.

2. Make a copy of your /home directory to a separate partition.

3. Start a fresh installation of 15.10. Select ***Something else*** at the partitioning window.

4. Select the root partition, '/', and format it.

5. Select the home partition, '/home', and do ***not*** format it.

6. Select the target for the bootloader. It should be the head of a drive, for example /dev/sda or /dev/sdb. (Do ***not*** add any partition number except in very special situations.)

7. The swap will be selected automatically (if there is a swap partition).

This way you will use your old /home directory in a separate partition. Many people use this method to keep their data files, tweaks and settings. But of course, you must reinsstall program packages. It is a good idea to look at the current installed system and write a list of the packages that you really need. There are probably some old packages that you have stopped using. You can also look for installed PPAs. It is convenient to use ***synaptic*** to check for installed sources.

---

### Post by klemen3 on 2015-11-03
That's one way.

But, old repos are probably here ; [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/) ?

---

### Post by sudodus on 2015-11-03
If you start by backing up your current system, you can try via 14.10 :-)

---

