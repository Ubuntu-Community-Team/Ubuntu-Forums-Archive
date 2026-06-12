---
title: "Installing 10.10 &quot;Server&quot; with debootstrap on VServer"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by alex-s77 on 2011-01-26
Hello.

I've got a VServer, on which I'd like to install 10.10 Maverick "server". My problem is, that I can't boot from a CD/USB/ISO/whatever. My [hosting company]("http://netcup.de") does provide a "rescue system", where the vserver is mounted to /vserver directory and is running Debian 4.0.

Doing searches, I figured out that I have to use [[FONT=Courier New]debootstrap[/FONT]]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html") to do the actual basic install, correct? But…

```
server:/# /usr/sbin/debootstrap --arch amd64 maverick /vserver http://mirror.netcologne.de/ubuntu 
mknod: `/vserver/test-dev-null': Operation not permitted
```

Doesn't look good, does it?

```
server:/# mount
/dev/hdv1 on / type ufs (defaults)
none on /proc type proc (defaults)
none on /dev/pts type devpts (gid=5,mode=620)

server:/# mount -o remount,exec,dev /
mount: permission denied

server:/vserver# LANG=C mknod -m0600 GFOO b 1 9
mknod: `GFOO': Operation not permitted

server:/# uname -a
Linux server.message-center.info 2.6.35.10-vs2.3.0.36.33-netcup #3 SMP Tue Dec 21 06:50:01 UTC 2010 x86_64 GNU/Linux
```

I'm lost…

How can I proceed?

Thanks a lot,
Alexander

---

### Post by albinootje on 2011-02-03
> **alex-s77 said:**
> 
```

mknod: `/vserver/test-dev-null': Operation not permitted
```

It looks like you're not allowed to run "mknod". Ask your VPS hosting provider to help you with this.

---

### Post by alex-s77 on 2011-02-04
Hi!

I am allow to execute mknod. I'm "just" not allowed to create device files... 

Hence my question - how to install Ubuntu, if mknod fails? Is it possible at all to install Ubuntu in this case?

Regards,
Alexander

---

