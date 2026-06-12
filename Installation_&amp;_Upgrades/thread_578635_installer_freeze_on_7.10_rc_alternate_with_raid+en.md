---
title: "installer freeze on 7.10 rc alternate with raid+encryption"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by kingpaul on 2007-10-17
Installing kubuntu-7.10-rc-alternate-amd64.iso on an intel quad core, with 2 250GB drives I experienced several problems with the install.

First I planned to install with a 1GB /boot (sda1) software a 9GB raid0 swap (sda2 4GB, sdb1 5GB), then 245GB raid1 (sda3 245GB, sdb2 245GB). I set up a random key on the raid0 and a passphrase on the raid1, after accepting the changes the installer works for a few seconds then the screen becomes corrupted and the installer freezes. 

After many (many many) reinstall attempts, this seems to be caused by selecting the random key instead of a passphrase for swap. I omit the swap partition and I can continue the install.

Once the encrypted partition based on the raid1 is created, I create a new partition table with one partition of the max size (245GB) mounted at /. The install proceeds and finishes without problems, however on reboot it seems the encrypted partition is never mounted, I am not asked for a passphrase and after ~5 minutes or so I am dropped to an initramfs shell.

The installer freeze is no big deal for me as I can set up the swap later, however it is really a deal breaker that the encrypted partitions are not mounted correctly after the reboot!

Anybody had similar experiences to this? Or tips/solutions?

Cheers, Paul

---

### Post by kingpaul on 2007-10-18
solved:

It seems the alternate installer for 7.10 is taken from Debian Etch, so I looked for the problems I was having on some Debian forums instead.

I read here: [http://www.debian.org/devel/debian-installer/News/2006/20060811](http://www.debian.org/devel/debian-installer/News/2006/20060811) that "random keys cannot be used for dm-crypt" and since dm-crypt is the only supported encryption option it could partially explain the crash/freeze when using this.

There is a bug in the installer when combining RAID and crypto together. I think the sensible place to put the encryption is between the RAID layer but before the actual partitions will mount (whether just a normal partition or LVM). But when you set this up in the installer it seems to forget that you configured the encryption layer. A workaround (for Debian but it worked for me with 7.10) can be found at: 

[http://wiki.debian.org/DebianInstaller/RAIDvsCrypto](http://wiki.debian.org/DebianInstaller/RAIDvsCrypto)

Cheers, Paul

---

### Post by Shadows Friend on 2007-10-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/148560](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/148560) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In my opinion the problem with the random key is a bug. I tried the Debian-installer and there it worked with random key and dm-crypt. It's the Ubuntu version of the Debian-installer which has the problem. The restriction you mentioned only applies to the graphical Debian-installer, not to the textbased one. So it definitely should also work in Ubuntu. I attached the bug-report that deals with the issue.

---

### Post by kingpaul on 2007-10-18
Yes the screenshot looks very similar to the problem I had. The screen was corrupted slightly differently, but at the same place so I would say this is certainly the same bug.

Cheers, Paul

---

### Post by Prometheum on 2008-01-02
If you hit alt-contrl-fX, then go back to f1, the lines disappear, and it just hangs nicely on 50%.

---

