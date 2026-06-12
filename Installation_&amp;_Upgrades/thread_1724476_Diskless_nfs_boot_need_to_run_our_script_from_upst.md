---
title: "Diskless nfs boot: need to run our script from upstart before parallel"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by aaminoff on 2011-04-08
We have a diskless setup that we have used for several years for FreeBSD and Fedora.  (Here is a  [semi-relevant description]("http://www.nber.org/sys-admin/FreeBSD-diskless.html")). I need to port this system to Ubuntu. I have ubuntu booting off the NFS server.

The hard part now is to have it run our cross-platform diskless initialization script, which is derived from FreeBSD's [rc.initdiskless. ]("http://src.gnu-darwin.org/src/etc/rc.initdiskless.html")This script sets up in-memory file systems for /etc, /var, and others, then copies in appropriate contents. There is a lot of logic for configuring individual diskless-booted machines to do particular things, so this system also provides configuration management sort of like cfengine or similar, especially by building the contents of /etc.

Things just aren't working right. I'm concerned that upstart is reading /etc/init/*.conf in parallel with my script replacing /etc with an empty in-memory fs and then copying in the contents. In FreeBSD and Fedora it was pretty easy to ensure that our script got run before everything else: the boot process was basically sequenctial. However, upstart (or rather, init, which then fires off things based on upstart in parallel) starts before the end of the initramfs.

My questions are:

 - Am I right that upstart starts while we are still running the init script from the initramfs? Looking in the initramfs it seems as though the real root fs has been mounted (nfs in our case) by that point, so we are reading from nfsserver:/path/to/root/etc/init/*,conf?

 - How can I get my script to run before anything else that wants to look up config in /etc? In particular, what if some script running in parallel wants to look up a uid with getent, but there is no /etc/nsswitch.conf?

 - I have looked at the [Upstart cookbook]("http://upstart.ubuntu.com/cookbook/"), but can not figure out the answer from that. Upstart is all about running stuff in parallel.

 - Should I ask on the upstart-devel list instead? Is there some better place?

---

### Post by psusi on 2011-04-08
This script does not make sense.  You can not have an init script that sets up /etc because the init scripts themselves live in /etc.

Mounting the root fs ( and /etc must be part of that ) is the job of the initramfs scripts.

---

### Post by aaminoff on 2011-04-08
This is diskless booting over nfs. So we start with the root filesystem as a read-only NFS mount. /etc is just the contents of the /etc directory on that NFS mount. Then /etc/rc.initdiskless runs, mounts an empty in-memory fs on /etc, and copies stuff into it. (Most of the stuff it copies is just the underlying /etc from the nfs mount, or a copy thereof).

I actually have this nearly working. I used an /etc/init/diskless.conf like this:
[INDENT]description     "NBER diskless setup"
author          "Alex Aminoff <aminoff@nber.org>"

start on starting mountall

console output
env INIT_VERBOSE

task

script
 /bin/sh /etc/rc.initdiskless >>/dev/.initramfs/myjob.log
end script
[/INDENT]At the end of rc.initdiskless I have it run ps to see what else is running. Results (snipped for brevity):
[INDENT]USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1  15152  1440 ?        Ss   13:32   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    13:32   0:00 [kthreadd]
...
root       240  0.0  0.0   4096   580 ?        Ss   13:32   0:00 /bin/sh -e /proc/self/fd/8
root       244  0.0  0.0   4096   652 ?        S    13:32   0:00 /bin/sh /etc/rc.initdiskless
root       246  0.0  0.0  25616   948 ?        S    13:32   0:00 /sbin/plymouthd --mode=boot --attach-to-session
root       250  0.0  0.0  18956   204 ?        S    13:32   0:00 /sbin/ureadahead --daemon

[/INDENT]I am heartened by the fact that so few other processes are running at this point. However, I am very worried about ureadahead. Since the point of ureadahead is explicitly to read stuff in advance, won't it read stuff in that will be different from what I want later on?

Should I change /etc/init/ureadahead.conf to something like start on (starting mountall and stopped diskless) ?

---

### Post by psusi on 2011-04-08
Why do you want to copy /etc to ram instead of just continuing to use it via nfs?  Doing something like that still needs to be done in the initramfs, before upstart runs, not while upstart is running.

---

### Post by aaminoff on 2011-04-11
> Why do you want to copy /etc to ram instead of just continuing to use it  via nfs?

We use one NFS root for multiple servers, each has different configuration which is handled as files are copied into the in-memory /etc.

> Doing something like that still needs to be done in the  initramfs, before upstart runs, not while upstart is running.

OK, I will take your advice and put it into the initramfs. It looks like the /etc/initramfs-tools make it remarkably easy to do this, more so than in other distros.

---

### Post by psusi on 2011-04-12
> **aaminoff said:**
> 
We use one NFS root for multiple servers, each has different configuration which is handled as files are copied into the in-memory /etc.

Where do you copy them from?  You must already have several different etc directories set up for each configuration of server, so why not just mount that directly instead of copying it to a ram based /etc on each machine?

---

### Post by aaminoff on 2011-04-13
> why not just mount that directly instead of copying it to a ram based /etc on each machine?

This is where the configuration management aspect comes in. The way it actually works is there are a bunch of directories each with different pieces, which all get copied over one on top of the other according to membership of this particular server in various classes as defined in a config file. So if the server is a web server, we might copy in base-Linux/etc/..., default/etc/..., webserver/etc/... (including webserver/etc/httpd...). There is also some fancy footwork that lets the contents of a file vary depending on what class the machine is, so default/etc/ssh/sshd_config.dlcpp gets pre-processed by a perl script that knows that if this machine is in the "restricted" class, insert "AllowUsers ..." into the sshd_config.

It is the same stuff that a config management system like cfengine handles, or on RHEL there is something called puppet. We ended up rolling our own to work tightly integrated with the diskless boot setup. It works on FreeBSD and FC13.

Unfortunately I had to give up on calling rc.initdiskless from the initrd. rc.initdiskless makes the assumption that the NFS root is mounted on / in too many places to be adaptable. However, I made progress on a /etc/init/diskless.conf that calls rc.initdiskless. It says "start on startup mountall" to run before mountall. There are some remaining issues, I think I need to post to the upstart-devel list.

We just adapted the FreeBSD rc.initdiskless: [http://src.gnu-darwin.org/src/etc/rc.initdiskless.html](http://src.gnu-darwin.org/src/etc/rc.initdiskless.html)

---

### Post by psusi on 2011-04-13
Interesting... you could have the initramfs run the script in a chroot maybe?

---

### Post by aaminoff on 2011-11-03
Just to follow up on this, we eventually got the advice to just replace /sbin/init with out own script that does what we need and then calls the real init. This actually works quite well to ensure that our copy-stuff-into-in-memory-etc happens before upstart begins.

Now we are just stuck with other upstart-related problems, which will need a separate thread.

Thanks to all for helpful suggestions.

---

