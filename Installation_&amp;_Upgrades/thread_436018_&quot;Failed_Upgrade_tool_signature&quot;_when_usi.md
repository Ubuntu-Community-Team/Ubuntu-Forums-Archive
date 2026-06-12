---
title: "&quot;Failed Upgrade tool signature&quot; when using do-release-upgrade"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by JonathanRRogers on 2007-05-07
I'm trying to upgrade an Edgy system to Feisty using do-release-upgrade from the update-manager-core package version 0.56~edgy4. I'm not sure if this is the correct version, since the official instructions indicate that the correct version of update-manager is 0.45.2, though they don't indicate what the correct version of update-manager-core is. Here's what I get:
> jrogers@marvin:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmpFZmo2K/feisty.tar.gz'
authenticate '/tmp/tmpFZmo2K/feisty.tar.gz' against '/tmp/tmpFZmo2K/feisty.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpFZmo2K'

gpg: can't open `/tmp/tmpFZmo2K/feisty.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.

Obviously, the first problem is "Failed Upgrade tool signature", but I'm not sure what that means. Does it mean that the signature doesn't exist or couldn't be downloaded? I think the rest of the errors just result from the first one.

I have exactly the same problem on two Edgy systems. Both were installed using an Edgy alternate install CD, but one is amd64 and one is i386. I was able to upgrade another amd64 Edgy system to Feisty using update-manager 0.45.2, which was installed from the same CD as the amd64 system I can't upgrade.

---

### Post by JonathanRRogers on 2007-05-07
Well, I dug deep enough to figure out the origin of the problem. I dug through the source of update-manager-core and discovered how to enable debugging: I added 'Debug::Acquire::http"1";' to my /etc/apt.conf. Then, I was able to see that downloading of the upgrade script signature was failing, though downloading of the script itself was succeeding. I also realized that in my /etc/apt.conf,

I was also setting an http proxy, which is the apt-cacher tool running on another server on my network. I disabled the http proxy setting, and downloading of the signature works. What's odd is that I thought I'd done that before, but I guess I thought I had commented out that line when I really hadn't, since I'm not too familiar with Perl syntax.

It seems that apt-cacher, which I'm using to avoid downloading the same debs multiple times for my several machines, works just fine for most files, but not for ones ending in ".gpg". It's been working for quite a while for "*.deb" and "*.tar.gz".  So, it seems my problem stemmed from stepping outside of the Ubuntu core tools and using a Debian one which wasn't entirely compatible.

---

