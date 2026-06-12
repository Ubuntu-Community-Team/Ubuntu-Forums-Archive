---
title: "Upgrade to 22.04 gets AUFS error"
date: 2022-10-11
forum: Installation &amp; Upgrades
---

### Post by Seamless in Northampton on 2022-10-11
Hit upgrade, got this:

> Sorry, this storage driver is not supported in kernels for newer
releases

There will not be any further Ubuntu releases that provide kernel
support for the aufs storage driver.

Please ensure that none of your containers are using the aufs storage
driver, remove the directory /var/lib/docker/aufs and try again.

Been using Linux for a long, long time, but I have absolutely zero idea what this means or how to fix it. 

How in Hades does one "ensure that none of your containers are using the aufs storage," and if whatever a "container" is *is* in fact using aufs, what then?

Haven't felt like this much of a Linux newbie since 2008. Really unclear how to proceed here, so any help appreciated. Searching for these terms opens up more questions than answers.

I don't want to disable something I need, but there is no /var/lib/docker/ folder at all.

---

### Post by TheFu on 2022-10-12
If you don't use docker, you can ignore this.
If you don't use aufs, you can ignore this.

If you use either, time to start researching the error to see what others did to get around it.  I don't use either. [https://askubuntu.com/questions/1361206/docker-upgrade-failure-the-aufs-storage-driver-is-no-longer-supported](https://askubuntu.com/questions/1361206/docker-upgrade-failure-the-aufs-storage-driver-is-no-longer-supported) was found by google. It assumes you are using docker for the solution.  Some of the 1-click installers might use docker, though on Ubuntu systems, I'd expect that a snap package would be used instead.

Docker is a popular Linux Container management tool.  You can google for answers on what that means, if you care.  I use lxd, which is a 1000x less popular Linux Container management tool.  Most of the industry has switched to the docker format, if not using docker management tools.  For example, every search performed on google is each a tiny "linux container" that is started, does the work, returns results, then adds information to google's tracking related to the search, then closes down.  There are different types of containers ... a snap package being run is another type.

Aufs is an overly file system.  There are all sorts of uses for that both in and outside of linux containers.  Like when we run from an Ubuntu installation ISO in "Try Ubuntu" mode.  [https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

---

### Post by Seamless in Northampton on 2022-10-12
Thank you so much for the info. I know I don't personally use Docker, but I wonder if programs I have use it behind the scenes? I did a search for Docker, and got a long list of files of several kinds, including "dockerfiles."

Would all of this be solved by a completely new installation? I was considering that. I barely have the time, but I'm getting some weird issues with 20.04 these days, so it may be worth it.

---

### Post by Seamless in Northampton on 2022-10-12
I did see that post that you mentioned -- and was ready to implement that. But I don't have a /var/lib/docker file, so my fix ended there! The only docker folder I found is in /snap.

I've always just slogged through learning whatever I need to with Linux, but this one calls for a lot of knowledge. So appreciate your explanation.

---

### Post by Seamless in Northampton on 2022-10-12
Also, I do have a fair number of aufs folders. Not certain if that means it's in use anywhere. If all of this would only be in effect as a manual thing, then I definitely don't use it, having never come across it. 

Please pardon my going on! Just really flustered by this one.

---

### Post by TheFu on 2022-10-12
The only aufs stuff I have on 18.04 is kernel drivers and headers. 
Same on 20.04.

Let me check 22.04 ... 

xubuntu 22.04 (fresh install, not upgrade) has a small group of headers for the kernel.  Ah .. needs to be patched (I seldom use it) ... patching ... lots-o-updates ... after all the patching and old kernel removal ... no aufs headers remain, so something definitely changed over the last month or so.

Let's look at an ubuntu 22.04 server ... I'll take better notes this time:
```
$ locate aufs
/usr/src/linux-headers-5.15.0-46/fs/aufs
/usr/src/linux-headers-5.15.0-46/fs/aufs/Kconfig
/usr/src/linux-headers-5.15.0-46/fs/aufs/Makefile
/usr/src/linux-headers-5.15.0-46/include/uapi/linux/aufs_type.h
/usr/src/linux-headers-5.15.0-47/fs/aufs
/usr/src/linux-headers-5.15.0-47/fs/aufs/Kconfig
/usr/src/linux-headers-5.15.0-47/fs/aufs/Makefile
/usr/src/linux-headers-5.15.0-47/include/uapi/linux/aufs_type.h
```

There are some updates, but nothing like with Xubuntu. All those GUI programs have lots of huge updates. Servers don't have GUIs. The full-upgrade took about a minute.  Did get an ugly TUI reminder that a new kernel needs a reboot.  Meh.  I'm not a noob.  Need to find how to suppress that crap.
```
$ locate aufs
/usr/src/linux-headers-5.15.0-47/fs/aufs
/usr/src/linux-headers-5.15.0-47/fs/aufs/Kconfig
/usr/src/linux-headers-5.15.0-47/fs/aufs/Makefile
/usr/src/linux-headers-5.15.0-47/include/uapi/linux/aufs_type.h
```

At the next boot, the kernel will be v5.15.0-50, which doesn't seem to have any aufs in the headers or kernel modules.  This server is used for playing with storage stuff, but I've never used aufs on purpose and I don't use docker, as said previously.

---

