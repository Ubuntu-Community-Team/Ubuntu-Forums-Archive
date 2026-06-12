---
title: "I screwed up my installation of Ubuntu! Can I save it?"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by inverser on 2010-12-20
Per the recommendation, I shrunk my Windows7 NTFS partition by 10.1 gigs so I could install Ubuntu via WUBI. 

Where I screwed up is, I choose a mere 5 GB during WUBI installation. I was under the impression that choosing a smaller installation was akin to installing a "lite" version of Ubuntu. I figured that updates and misc applications would cause my installation to grow and that I'd have a 5 GB cushion to grow into. 

Unfortunately, I was mistaken and it looks like I'm wasting 5 GB of space. I'm constantly running out of disk space after only installing a small handful of applications. How can I merge the unused 5 GB back into the Ubuntu installation without reinstalling? 

I booted with gparted CD and didn't see anything that could accomplish this.

Any ideas would be greatly appreciated. Thanks.

```
dragonfly@ubuntu:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/loop0    ext4    3.6G  2.6G  858M  76% /
none      devtmpfs    996M  272K  996M   1% /dev
none         tmpfs   1002M  212K 1002M   1% /dev/shm
none         tmpfs   1002M   96K 1002M   1% /var/run
none         tmpfs   1002M     0 1002M   0% /var/lock
/dev/sda2  fuseblk     11G  4.7G  5.5G  47% /host
/dev/sdb1  fuseblk     43G   24G   20G  55% /media/ExpressCard
dragonfly@ubuntu:~$
```[IMG]http://i.min.us/ib4W7a.png[/IMG]

---

### Post by bcbc on 2010-12-20
The simple answer is - you can't. At least not by any reliable method I am aware of.

a) if you use Wubi you don't need to partition. Wubi uses a virtual disk so it can be placed anywhere.
b) Wubi's virtual disk is fixed. It's possible to resize it, but this is in fact a net new disk that is larger - and then the old one is copied to it. It doesn't absorb remaining space - so won't work in your case as the remaining space is the same size as the current virtual disk.
c) since you went to the trouble of creating a partition, why don't you just install Ubuntu directly to it. You can either use the whole 10gb or you can replace it with an extended partition and create two logical partitions, one for Ubuntu and the other for swap.

---

### Post by inverser on 2010-12-20
> **bcbc said:**
> The simple answer is - you can't. At least not by any reliable method I am aware of.
Really?! That's the worst news I've heard all week. I've been tweaking and personalizing my desktop for nearly two weeks now. And it took forever being that I'm a total Ubuntu newbie. Is there anyway to save all my settings and preferences? Export them to file and import them when I reinstall?

> c) since you went to the trouble of creating a partition, why don't you just install Ubuntu directly to it. You can either use the whole 10gb or you can replace it with an extended partition and create two logical partitions, one for Ubuntu and the other for swap.I tried. I couldn't get it to install via CD. I tried for two days and then I was like screw it. WUBI is good enough for now.

Thanks for the input. I guess I'm looking at a reinstall. Sigh. Hopefully someone else can chime in with an idea.

---

### Post by bcbc on 2010-12-20
> **inverser said:**
> Really?! That's the worst news I've heard all week. I've been tweaking and personalizing my desktop for nearly two weeks now. And it took forever being that I'm a total Ubuntu newbie. Is there anyway to save all my settings and preferences? Export them to file and import them when I reinstall?

I tried. I couldn't get it to install via CD. I tried for two days and then I was like screw it. WUBI is good enough for now.

Thanks for the input. I guess I'm looking at a reinstall. Sigh. Hopefully someone else can chime in with an idea.

There are ways to do it - definitely. It depends on your comfort level. Let me come up with some suggestions.

---

### Post by inverser on 2010-12-20
> **bcbc said:**
> There are ways to do it - definitely. It depends on your comfort level. Let me come up with some suggestions.
Thanks man I appreciate your help! :)

---

### Post by bcbc on 2010-12-20
The easiest is to create a separate virtual disk for /home. There is a script in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"). (Just note that there are links to lvpm there, but lvpm doesn't support Ubuntu after version 8.04 so ignore that)

If you're ok running Ubuntu off an external USB drive it's possible just to [migrate your Wubi install to it with a script]("http://ubuntuforums.org/showthread.php?t=1519354"). The script will install the grub bootloader on the external drive, so - provided your computer can boot from USB - you leave your internal drive untouched. Only issue is you'd have to lug around an external if you have a laptop and you need mobility. (I  have a script that moves normal Ubuntu installs around as well, but it's not 'production-ready' - the idea is you could migrate wubi to external - and then move it back later to your internal). 

Honestly, if you're planning on using Ubuntu long term I'd probably bite the bullet and reinstall. Replace the 10GB partition with an extended partition and create logical partitions within that so you can have a swap partition (and perhaps a separate /home which is useful if you need to reinstall).

Finally, there are some manual techniques to list what packages you have installed and backup /home etc. I haven't used these but I'll link you to a current thread that I found. [http://georgia.ubuntuforums.org/showthread.php?p=10254352](http://georgia.ubuntuforums.org/showthread.php?p=10254352)

Hope that helps.

PS depending on what's taking up all that space - if it's files within /home, you can probably move some of that data to the /host folder (the host ntfs partition that has 5GB free space). That will give you some temporary relief as well.

---

### Post by inverser on 2010-12-20
> **bcbc said:**
> The easiest is to create a separate virtual disk for /home. There is a script in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?"). (Just note that there are links to lvpm there, but lvpm doesn't support Ubuntu after version 8.04 so ignore that)

If you're ok running Ubuntu off an external USB drive it's possible just to [migrate your Wubi install to it with a script]("http://ubuntuforums.org/showthread.php?t=1519354"). The script will install the grub bootloader on the external drive, so - provided your computer can boot from USB - you leave your internal drive untouched. Only issue is you'd have to lug around an external if you have a laptop and you need mobility. (I  have a script that moves normal Ubuntu installs around as well, but it's not 'production-ready' - the idea is you could migrate wubi to external - and then move it back later to your internal). 

Honestly, if you're planning on using Ubuntu long term I'd probably bite the bullet and reinstall. Replace the 10GB partition with an extended partition and create logical partitions within that so you can have a swap partition (and perhaps a separate /home which is useful if you need to reinstall).

Finally, there are some manual techniques to list what packages you have installed and backup /home etc. I haven't used these but I'll link you to a current thread that I found. [http://georgia.ubuntuforums.org/showthread.php?p=10254352](http://georgia.ubuntuforums.org/showthread.php?p=10254352)

Hope that helps.

PS depending on what's taking up all that space - if it's files within /home, you can probably move some of that data to the /host folder (the host ntfs partition that has 5GB free space). That will give you some temporary relief as well.
That doesn't sound that bad. I'll look into it. Is it possible for me to migrate WUBI to an ExpressCard? Permanently? Can GRUB boot ExpressCards? That would be pretty sweet actually. It's a SSD.

---

### Post by bcbc on 2010-12-20
> **inverser said:**
> That doesn't sound that bad. I'll look into it. Is it possible for me to migrate WUBI to an ExpressCard? Permanently? Can GRUB boot ExpressCards? That would be pretty sweet actually. It's a SSD.

Sorry I have no idea. I did a quick search and found this thread [http://art.ubuntuforums.org/showthread.php?p=9144022](http://art.ubuntuforums.org/showthread.php?p=9144022)

But I didn't see a definitive answer.

---

### Post by inverser on 2010-12-20
> **bcbc said:**
> Sorry I have no idea. I did a quick search and found this thread [http://art.ubuntuforums.org/showthread.php?p=9144022](http://art.ubuntuforums.org/showthread.php?p=9144022)

But I didn't see a definitive answer.
Found that thread myself. Sounds like dualbooting it is problematic and unfortunately I can't leave behind Windows right now for work. 

Thanks again for your help. :)

---

### Post by bcbc on 2010-12-20
> **inverser said:**
> Found that thread myself. Sounds like dualbooting it is problematic and unfortunately I can't leave behind Windows right now for work. 

Thanks again for your help. :)

OK no prob... 

PS for Wubi installs, updating packages grub-pc and grub-common are a problem. In your case, with an install on a separate partition, it will prompt you where to install the grub bootloader. Don't install it anywhere - if you install it to your drive nothing will boot.
It' best to just avoid updating these packages.

---

### Post by inverser on 2010-12-20
> **bcbc said:**
> OK no prob... 

PS for Wubi installs, updating packages grub-pc and grub-common are a problem. In your case, with an install on a separate partition, it will prompt you where to install the grub bootloader. Don't install it anywhere - if you install it to your drive nothing will boot.
It' best to just avoid updating these packages.
Roger that.

---

