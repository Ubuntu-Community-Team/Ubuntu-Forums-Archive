---
title: "multiple ubuntu and/or Gentoo dual boot?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by HankB on 2011-04-24
Hi folks,
I'm planning to carve out a couple of partitions on my HDs in order to allow for test installations of the newer Ubuntu versions as well as other distros such as Gentoo. At present my setup is:
```
hbarta@olive:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1               19G  6.3G   12G  36% /
none                  2.0G  332K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G  120K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/md0              958M  123M  786M  14% /boot
/dev/md2              170G   30G  132G  19% /home
hbarta@olive:~$ 

```

/boot and /home are  RAID1 (mirror) and / is RAID0 (stripe.) I would like the new root partitions to be RAID0 as well. AFAIK this means that I cannot boot directly from them, though it would be nice if I was wrong. ;)

My plan is to carve out 15G from my /home partition and use that space to create two 15G RAID0 partitions for alternate versions/distros root partitions.

Can I share /boot between multiple installations? It seems like each boot stanza in GRUB config specifies the root partition so that should work. But I will ask. I suppose I could create separate /boot partitions for each distro or version but that seems like it would just be more complicated.

Also I presently know nothing about Gentoo so any caveats about mixing that with Ubuntu would be appreciated!

thanks,
hank

---

### Post by rpm13 on 2011-04-24
Never used raid myself but I had asked a similar question on the grub list [link]("http://lists.gnu.org/archive/html/help-grub/2011-01/msg00017.html")

The long-and-short of the answer there is:
[LIST=1]
[*]Have a standalone boot which the mbr points to
[*]have embedded boots in each OS that is 'called' from the standalone one
[*]Call from standalone to embedded using configfile (earlier grub used to use chainload but that is unreliable and deprecated except for windows)
[*]Let the package updates of the OSes mess around with 'their own' boots and not the standalone one
[/LIST]

---

### Post by HankB on 2011-04-26
I can confirm that installing Gentoo with my boot partition mounted was a Bad Idea(tm). I did not even install grub for Gentoo because they have not yet migrated to grub2 and some part of the install still clobbered my ability to boot. (reinstall from Live CD was required to fix things.)

I think next time I will leave my /boot unmounted and either copy the necessary files to it from the other Linux install or call it as you suggested.

One issue is that the other install partitions are on RAID0 and it is not clear to me that grub 2 can see them, though it did seem to be able to do so from the rescue console.

thanks,
hank

---

