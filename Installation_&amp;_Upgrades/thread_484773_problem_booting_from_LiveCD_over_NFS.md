---
title: "problem booting from LiveCD over NFS"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by bartzitz on 2007-06-26
hello,

i've setup an install server to boot and install many clients in the local network. the following steps are succesfull:

- PXE boot
- kernel and initrd boot
- squashfs filesystem mount over NFS
- unionfs writeable points

then in the very bottom of init script in the initrd image the following is called:

run-init /root /sbin/init

which should pass the boot process to init from squashfs filesystem. when it comes to "Checking filesystems..." step it doesn't see /dev/shm and complains some /dev/shm/var.* dirs can't be created and drops to BusyBox shell. i think init still looks in the / instead of /root.

any ideas?

---

### Post by steveMyatt on 2007-08-28
hi bartzitz, sounds like you're just a little further along than me, I haven't got squashfs mounted yet so i can't tell what happens at your fail point on my box yet.

I got a busybox during client boot from 7.04 desktop iso over nfs. Checking in casper.log the nfsmount failed. I tried executing same command manually, it failed. Executed mount (not nfsmount) with same parameters and it succeeded. Maybe nfs client in casper isn't compatible with Universal NFS Server 2.2beta47 in my Linux ubuntu 2.6.15-28-386 server?

:S

---

### Post by bartzitz on 2007-08-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/122821](https://bugs.launchpad.net/bugs/122821) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				hello,

unfortunately i don't remember how exactly was the NFS server set up, and i don't have any records :( i remember i had some problems with it as well, but i've fixed it. if you ever succeed in this kind of installation, please let me know, because i've tried all the means - google, mailing list, irc, even a ticket in launchpad. you're the first person who replied, and this LiveCD usage scenario may be interesting to many ppl out there i think.

---

