---
title: "Upgrade to 10.04 - kernel panic"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by marcslater on 2010-10-19
FYI, this thread also belongs in the Absolute Beginners forum.

I haphazardly did the recommended upgrade to 10.04 without really reading into it. This box is a headless media server for me, not a lot in the special configuration department, but obviously a TON of files I don't want to lose.

Regular boot brings me to the "Kernel panic no sync" issue. After doing some reading I found out about Grub, was able to 'esc' into it, which gave me a bunch of options, each one leading to a different scent of 'this machine ain't working':

```

ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-28-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-26-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-24-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-23-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-22-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-22-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-21-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-21-generic (recovery)
ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic
ubuntu 10.04.1 LTS, kernel 2.6.24-19-generic (recovery)
ubuntu 10.04.1 LTS, memtest86+
```

If I ever get the xubuntu splash loading screen, it will bring me to a screen stating

```

libudev:udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2544) killed by ABRT signal.
General error mounting filesystems
```

and brings me to 

```

root@mediaServer:~#

```

As a side, I've moved this computer up to my desk where I use a wireless adapter for internet access, this adapter has never been installed on this machine, so I only have access from my laptop. Is there an easy way to install this adapter so I have access if necessary?

---

### Post by marcslater on 2010-10-19
I should note, this thread seemed promising to me, but my file system is now read-only: [http://ubuntuforums.org/showpost.php?p=9898231&postcount=16](http://ubuntuforums.org/showpost.php?p=9898231&postcount=16)

---

### Post by marcslater on 2010-10-20
Can anyone help? I'm really stuck :(

---

### Post by marcslater on 2010-10-20
One more bump for hope

---

### Post by bobwyajnr on 2010-10-20
> **marcslater said:**
> One more bump for hope

Can you not boot from a live CD or USB and pull the files you need? Then do a clean install. No?? I presume you have a monitor rigged up to the machine now - right??

Also if you have a root shell access can you not move your critical files to a backup harddisk, etc.?

I think you need to be a bit clearer about what you want to do/achieve - rather than going into detail about how broken GRUB is!! You might get some more responses to your thread (except for you talking to yourself... :lolflag:)

Bob

---

