---
title: "Need to reinstall when Jaunty is released?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by whitefort on 2009-04-05
Hi,

I've been a Ubuntu fan since Dapper, but this is the first time I've dared to run a pre-release version.

I love Jaunty so far, but I just got to wondering... when it's finally released, do testers need to download and re-install that version, or will just running update manager do the trick?

Thanks!

---

### Post by zekopeko on 2009-04-05
> **whitefort said:**
> Hi,

I've been a Ubuntu fan since Dapper, but this is the first time I've dared to run a pre-release version.

I love Jaunty so far, but I just got to wondering... when it's finally released, do testers need to download and re-install that version, or will just running update manager do the trick?

Thanks!

no need to reinstall. you'll be auto updated to the final version

---

### Post by linux6994 on 2009-04-05
All of the updates should keep you current with the release, so re-installing should not be necessary.

---

### Post by Lunx on 2009-04-05
> **whitefort said:**
>  or will just running update manager do the trick?

Thanks!

That's what I'm led to believe (change a couple of settings in Synaptic for updates as far as I'm aware and should be good to go) I'm only new 'round this OS and Jaunty upgrade will be my first via that method, all my experience so far has be installs from CD.

---

### Post by whitefort on 2009-04-05
Cool!  Thanks for the speedy replies, guys.

---

### Post by MaxCarnage on 2009-04-05
Unless of course you want the new filesystem, right?

---

### Post by taavikko on 2009-04-05
> **MaxCarnage said:**
> Unless of course you want the new filesystem, right?

And that doesn't require fresh installation ;)

That can be done via liveCD and does not require new install.

---

### Post by Eclipse. on 2009-04-05
> **taavikko said:**
> And that doesn't require fresh installation ;)

That can be done via liveCD and does not require new install.

Actually it does it you want _all_ your files running off of ext4, converting your filesystem to ext4 means that only files created after that are ext4.

---

### Post by taavikko on 2009-04-05
> **Eclipse. said:**
> Actually it does it you want _all_ your files running off of ext4, converting your filesystem to ext4 means that only files created after that are ext4.

and then again it doesn't, since migrating to ext4, on near future the onlinedefrag tool will "convert" these old files 

[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

> There's another thing that must be mentioned. All your existing files will continue using the old indirect mapping to map all the blocks of data. The online defrag tool will be able to migrate each one of those files to a extent format (using a ioctl that tells the filesystem to rewrite the file with the extent format; you can use it safely while you're using the filesystem normally)

Might be wrong?

---

### Post by FuturePilot on 2009-04-05
> **Eclipse. said:**
> Actually it does it you want _all_ your files running off of ext4, converting your filesystem to ext4 means that only files created after that are ext4.

If you convert, existing files just won't use [extents]("http://en.wikipedia.org/wiki/Ext4#Extents"). However new files will. But once the Ext4 defragger becomes available it will allow you to move all files over to extents.

---

### Post by Eclipse. on 2009-04-06
> **FuturePilot said:**
> If you convert, existing files just won't use [extents]("http://en.wikipedia.org/wiki/Ext4#Extents"). However new files will. But once the Ext4 defragger becomes available it will allow you to move all files over to extents.

The ext4 defragger wont be in jaunty and noboy really knows when its going to be ready.

Extents is by far the biggest features of ext4 and provides a large performace improvement compared to ext3.

---

