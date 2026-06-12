---
title: "SSH service/rc/init script doesn't run on/at boot time after upgrade to 9.10 Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by PorcelainMouse on 2009-11-14
1) Does anyone recognize this symptom?  It might not be sshd-specific.  It seems more init-script related.
2) Does anyone know how to get boot logs?

After upgrading to 9.10 Karmic Koala, sshd no longer starts on boot.  It starts without complaint when I issue 'service ssh restart' or 'service ssh start' or 'invoke-rc.d ssh start' or run it directly.  sysv-rc-init shows the right runlevel settings.  /etc/init.d/ssh looks okay and /etc/rc2.d/S*ssh points to it.  And (I think) upstart is running all the init scripts since the other runlevel 2 scripts are running. When runing, sshd logs authentication meessages to auth.log. But, there is no record of sshd starting or stoping in other syslog logs, which I am sure used to happen.  [CORRECTION: there are boot-time errors from sshd.  But, I don't know where they lead.  See later posts.]

```

> sysv-rc-conf --list ssh
ssh          1:off      2:on    3:on    4:on    5:on
> ls -l /etc/init.d/ssh
-rwxr-xr-x 1 root root 3878 2009-10-22 12:58 /etc/init.d/ssh
> ls -l /etc/rc2.d/S*ssh
lrwxrwxrwx 1 root root 13 2008-07-17 21:21 /etc/rc2.d/S16ssh -> ../init.d/ssh
> ls -l /etc/init/rc-sysinit.conf 
-rw-r--r-- 1 root root 1453 2009-10-15 12:19 /etc/init/rc-sysinit.conf

```


To complicate matters, I cannot find any boot logs.  I haven't needed them in so long that I'm not sure where to find them if they even exist (but I know this is a weak spot).  So, when I say the rc2 scripts are running, I mean I know some are running because I see their daemons running.  But, since ssh isn't running, it is possible other rc scripts are not getting run either.

Other background info:
After the upgrade, I also had a problem getting proper DNS server settings from my router (via DHCP), but networking always started on boot and I'm getting proper resolv.conf configuration now.  Other reported boot-time issues in 9.10 suggest problems during the conversion of /etc/event.d scripts to /etc/init, and I don't think that is my problem.

---

### Post by toammann on 2009-11-14
Have you tried running ```
sudo dpkg-reconfigure ssh
```?

What happens if you start sshd manually, does it run then? Otherwise there might be configuration/dependency issues with you ssh.

---

### Post by PorcelainMouse on 2009-11-14
No, I had not tried that.  What is that supposed to do?  What makes you think it would help?  I'm willing to try it, but I'd like to know a little more.

sshd runs fine and works great.  As I stated, I can start the service using all of methods I know.  It just will not start automatically on boot.

---

### Post by PorcelainMouse on 2009-11-15
I found fatal errors in auth.log.  (I could have sworn sshd logged to another facility for non-auth-related messages.)  Here they are:

sshd[1770]: error: Bind to port 22 on <ip> failed: Cannot assign requested address.
sshd[1770]: fatal: Cannot bind any address.

I think I know what's going on.  The interface isn't up yet when ssh server is starting.  But how could that be?  Ah, well that's a story: Previously, I was using a virtual interface to add a secondary service ip addr for my SSH daemon.  SOP.  But, ifupdown suddenly and without notice dropped support for virtual interfaces.  (See below.)  So, I had to find an alternate method using the 'up' action script in /etc/interfaces.  But, I'm guessing the 'up' script isn't completing before sshd is started.  Nice work.

This /etc/network/interfaces file, which has been working since  Feisty Fawn:
```
auto eth2
iface eth2 inet static
  address <ssh service ip>
  ...
auto eth2:2 inet dhcp

```

Now produces this error:
> sudo ifup eth2
/etc/network/interfaces:19: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"


And this:
```

auto eth2:local
allow-hotplug eth2:local
iface eth2:local inet dhcp
  up ip addr add <ssh service ip>/24 dev ${IFACE}

```
Correctly configures the interface with a second ip for SSH, but starts SSHD before the 'up' command completes.

What is best practice for virtual interfaces now?  What happened to virtual interface support?  ifconfig and ip still support it.

---

