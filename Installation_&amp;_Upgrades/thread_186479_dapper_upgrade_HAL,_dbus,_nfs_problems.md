---
title: "dapper upgrade: HAL, dbus, nfs problems"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by DaveQB on 2006-06-02
Well I have managed to fix the first two by installing them :) 
Somehow HAL and dbus were removed and not updated :-?

Read my blog for more details about this, here: [Link to blog on above issues.]("http://www.dward.us/archives/2006/06/index.html#e2006-06-02T14_41_54.txt")

But for some reason my NFS mounts won't auto mount on boot.  fstab hasn't changed from what I can see, here's an example:

```
10.1.1.1:/home/david /home/david/server_home nfs rsize=8192,wsize=8192,soft,nolock,atime,auto,rw,dev,exec,suid,user 0 0

```

I guess I could add a mount line to the bottom of rc.local but this shouldn't be needed.
My first thought to troubleshoot this would be to find out when in the boot process /etc/fstab is executed, anyone ??

---

### Post by rcarring on 2006-06-02
Hal is deprecated in Dapper, replaced with udev.

---

### Post by dmalinovsky on 2006-06-02
[QUOTE=rcarring]Hal is deprecated in Dapper, replaced with udev.[/QUOTE]
Maybe you mean hotplug is deprecated and replaced with udev?  Because ubuntu-desktop package depends on hal&#8212;obviously it won't depend on deprecated package.

---

### Post by DaveQB on 2006-06-02
Yeah, thats what I thought, HAL is new :D 

I have been poking around and found /etc/rcS.d/S45nfswait.sh 

Seems to not be what I am after.  Just need to know when NFS mounts are attempted to be mounted in the boot and I should be right from there...... for a little while anyway.....

---

### Post by DaveQB on 2006-06-02
Well it seems to be a known bug in Dapper :(
[https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/46516](https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/46516)

Hope there's a fix soon, I imagine its just a simply scripting error in the RC scripts, perhaps something is done out of order, I think.

---

