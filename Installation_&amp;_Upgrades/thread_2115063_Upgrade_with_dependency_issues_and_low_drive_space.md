---
title: "Upgrade with dependency issues and low drive space"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by maja_z on 2013-02-11
I realise there are many similar threads, but I think my situation warrants a separate one - following suggestions on others also didn't help much :(

Anyway, I upgraded from 10.10 to 12.04 (I'm pretty sure).
During the upgrade there were several warnings that I had to click through (there was no other option).
Two were of the "pre-dependency error" type and said "not installing" ntfc-3g and resolvconfl.
The other error was a low disk space error - at least that was written in the title of the error box - the box itself was filled with those blank squares that you sometimes see when characters aren't rendered properly. I couldn't really do anything about it at that point. It was my mistake though, since I had had problems before with that partition being too small, and have had to delete old kernels and stuff from it. I just didn't think to make extra room before the upgrade.

Soo, after the reboot I get:

The disk drive for / is not ready yet or not present. Continue to wait; or press s to skip mounting or M for manual recover

I press M, and this is where I am out of my comfor zone...
Here's a few things I've tried - sorry this is manually copied, so I hope I got the important bits:

```
~# ls
Desktop

~# sudo apt-get upgrade
...
The following packages have unmet dependencies.
 ntfs-3g: depends : libntfs-3g75 but it is not installable
 ubuntu-minimal: depends: resolvconf
Unmet dependencies. Try using -f

~# sudo apt-get -f install
...
following will be installed:
resolvconf 
following will be upgraded:
ntfs-3g
... do you want to continue?y/n
Y
E: Internal error, No file name for libuuid1

```
This is as far as I've got. Any help will be greatly appreciated!
Thanks!

---

### Post by ibjsb4 on 2013-02-11
If your out of disk space you need to fix that.

```
df -TH
```

Whats that say?

If you can fix the disk space problem maybe a dist-upgrade would work.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by maja_z on 2013-02-11
Thanks ibjsb4, Here's what I get:
```

~# df -TH
Filesystem          Type      Size  Used  Avail Use%  mounted on
/dev/mapper/ZH-root ext4      50G   13G   35G   27%   /
none                devtmpfs  2.0G  4.1k  2.0G  1%    /dev
none                tmpfs     390M  189k  389M  1%    /run

```
Also, its a 640G disk if that's relevant :)

---

