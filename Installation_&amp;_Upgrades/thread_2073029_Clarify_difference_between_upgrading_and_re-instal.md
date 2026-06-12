---
title: "Clarify difference between upgrading and re-installing?"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-10-18
I know there are a lot of threads about this, but there seems to be no clear consensus (at least to me) as to what the advantages/disadvantages of upgrading vs doing a clean install as a new version comes out.  I've heard two sides.  One says that a clean install has only two advantages, preventing dependency problems (which may or may not occur at all), and to prevent the build up of cruft.  The other side says that a clean install is necessary to take full advantages of new features, such as a change to the filesystem or changes to *every* package, such as adding PIE which may happen in the near future.  This is what I'm specifically curious about.  

Ubuntu currently uses PIE for only a few, security-focused executables (like sshd), but most aren't using PIE because of the large performance penalty on 32-bit systems.  However, 64-bit computers don't have the same performance penalty.  According to [this](https://wiki.ubuntu.com/Security/Features#Built_as_PIE), using PIE with everything "will eventually be made the default, but more testing is required".  This seems like a pretty big change.  So would simply upgrading be able to accomplish this, or by "made the default" does it mean only a clean install will have this?  When the version of Ubuntu comes out with 100% PIE support, will I have to do a clean install or will the upgrade alone replace every file in /usr/bin, /bin, etc with the PIE version?

---

### Post by cybrsaylr on 2012-10-18
I've always preferred doing a clean install. Clean install just seems to work better. Been using 64 bit versions for years. Know nothing about PIE.

I just save my Home folder on another partition or external drive keeping files desired or needed.

---

### Post by Stonecold1995 on 2012-10-18
> **cybrsaylr said:**
> I just save my Home folder on another partition or external drive keeping files desired or needed.
That's what I would do too, but the problem is that I've made a lot of config modifications specific to my hardware that won't be preserved unless /etc is kept, not /home.

---

### Post by fdrake on 2012-10-18
> **Stonecold1995 said:**
> That's what I would do too, but the problem is that I've made a lot of config modifications specific to my hardware that won't be preserved unless /etc is kept, not /home.
You can not have /etc folder on another partition since it is needed at boot time.you can have the files in /etc/conf_files  sym lynk to /home/etc/conf_files.

---

### Post by oldfred on 2012-10-19
A lot of custom settings in /etc can be a real can of worms.

I used to do upgrades and settings I had in /etc would get the question do I want the user maintainer's version or my version. What ever you answer is wrong. Sometimes only the maintainer's version works with a new version software, sometimes you old settings are not required or even make it worse, and usually you need both but the merge option may or may not work. But with each piece of software it can be different on what is correct.

I backup /etc any file I manually edit with a copy in a folder in /home. Then my standard backup of /home has my settings so I can copy those I really need back again when I do a clean install. But I know I am starting with the standard set of options/configurations.

---

### Post by Sophont on 2012-10-19
The reason that there is no clear consensus is because both sides are right.

Both options involve trade-offs and have their own advantages and disadvantages.

Most of the time an upgrade will work fine (at lest that has been my personal experience over many years and machines). But sometimes old config files and custom settings can be problematic.

Fresh install ensures the use of the newest file system (including the risk of fresh bugs/regressiions) and that the best new config are used.
Of course when people keep their home partition for easier "fresh installs" that partition will stay with the old file system anyway. OTOH a lot of customization and installations might have to be done again. And if you don't have a seperate home partition, then making a complete backup and copying everything back afterwards is a hassle.
And if you do keep home and only re-install the system then a lot of old stuff remains anyway.

I tend to do upgrades because it almost always worked fine for me and I can always do a fresh install afterwards if it doesn't.

---

### Post by Stonecold1995 on 2012-10-19
> **Sophont said:**
> Fresh install ensures the use of the newest file system (including the risk of fresh bugs/regressiions) and that the best new config are used.

I'm using Kubuntu 12.04, which I upgraded a while ago from 11.10, and I plan to upgrade to 12.10.  What filesystem upgrades, etc am I missing from 11.10 to 12.10?

---

### Post by Sophont on 2012-10-20
Probably nothing (but didn't check). The drivers get updated with your new kernel anyway and the filesystem laout doesn't change much after the initial design.

The next big thing would be btrfs instead of ext4.

---

### Post by funicorn on 2012-10-20
The real problem of upgrade is, your system will be dirtier after upgrade if it was dirty before upgrade, which means you have to clean it a little bit.

But for people whose system is dirty, I don't think he cares so much about how dirty it is, bearing the thought that he can clean it as he will. I enabled over ten ppa's in Ubuntu 12.04, and installed many packages from outside the repository. After upgrading to 12.10 I found wired things from time to time. But it's OK. I fixed them when I felt uncomfortable.

So it's rather the user himself than the upgrade making the system dirty, on which upgrade or fresh install makes no difference.

---

### Post by Stonecold1995 on 2012-10-21
> **Sophont said:**
> Probably nothing (but didn't check). The drivers get updated with your new kernel anyway and the filesystem laout doesn't change much after the initial design.

The next big thing would be btrfs instead of ext4.

Why btrfs?  Benchmarks show brtfs is much slower than ext4.

---

