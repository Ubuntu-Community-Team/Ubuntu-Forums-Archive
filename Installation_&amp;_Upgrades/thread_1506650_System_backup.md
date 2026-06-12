---
title: "System backup"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Werm on 2010-06-10
Hello,

My current setup is dual boot win7 and ubuntu. I want to back up ubuntu complete, every last file. A full backup.

The primary drive is starting to fail and needs to be replaced, I don't want windows on my new drive it's just a waste of space and I never use it anymore.

Do you guys know of anything I should know before doing this? Like does the backup also backup the boot files/etc.

The commands I'll be using for the backup:

```

cd /

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

Thanks :)

---

### Post by anglican on 2010-06-11
> **Werm said:**
> Hello,

My current setup is dual boot win7 and ubuntu. I want to back up ubuntu complete, every last file. A full backup.

The primary drive is starting to fail and needs to be replaced, I don't want windows on my new drive it's just a waste of space and I never use it anymore.

Do you guys know of anything I should know before doing this? Like does the backup also backup the boot files/etc.

The commands I'll be using for the backup:

```

cd /

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```Thanks :)
Since you don't want Windows, why not use mondorescue to create your backup. That will give you a set of CD/DVD's from which you can restore onto a new disk. Mondo is in the repo. It can also backup to various other media and the network.

H

---

