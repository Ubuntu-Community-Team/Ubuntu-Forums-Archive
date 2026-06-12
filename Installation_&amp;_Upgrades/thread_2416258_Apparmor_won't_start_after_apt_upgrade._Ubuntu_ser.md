---
title: "Apparmor won't start after apt upgrade. Ubuntu server 18.04"
date: 2019-04-08
forum: Installation &amp; Upgrades
---

### Post by cookie505 on 2019-04-08
[FONT=Arial][COLOR=#242729]I am running Ubuntu server 18.04. It's just a web server with apache and PHP. I just updated everything. After I restarted it says Failed to start apparmor initialization. When I try to start it manually it fails again and tells me to run systemctl status apparmor.service. When I run that this is the result:[/COLOR][/FONT]

```
&#9679; apparmor.service - AppArmor initialization
   Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2019-04-07 06:48:34 UTC; 3min 10s ago
     Docs: man:apparmor(7)
           http://wiki.apparmor.net/
  Process: 2913 ExecStart=/etc/init.d/apparmor start (code=exited, status=123)
 Main PID: 2913 (code=exited, status=123)


Apr 07 06:48:34 webserver apparmor[2913]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Apr 07 06:48:34 webserver apparmor[2913]: AppArmor parser error for /etc/apparmor.d/usr.lib.snapd.snap-confine.real in /etc/apparmor.d/usr.lib.snapd.snap-confine.real at line 11: Could not
Apr 07 06:48:34 webserver apparmor[2913]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Apr 07 06:48:34 webserver apparmor[2913]: AppArmor parser error for /etc/apparmor.d/usr.lib.snapd.snap-confine.real in /etc/apparmor.d/usr.lib.snapd.snap-confine.real at line 11: Could not
Apr 07 06:48:34 webserver apparmor[2913]: AppArmor parser error for /var/lib/snapd/apparmor/profiles/snap-confine.core.6130 in /var/lib/snapd/apparmor/profiles/snap-confine.core.6130 at lin
Apr 07 06:48:34 webserver apparmor[2913]: AppArmor parser error for /var/lib/snapd/apparmor/profiles/snap-confine.core.6130 in /var/lib/snapd/apparmor/profiles/snap-confine.core.6130 at lin
Apr 07 06:48:34 webserver apparmor[2913]:    ...fail!
Apr 07 06:48:34 webserver systemd[1]: apparmor.service: Main process exited, code=exited, status=123/n/a
Apr 07 06:48:34 webserver systemd[1]: apparmor.service: Failed with result 'exit-code'.
Apr 07 06:48:34 webserver systemd[1]: Failed to start AppArmor initialization.

```

I also tried uninstalling apparmor and reinstalling, and running apt clean.  Didn't change anything.

How can I fix this? Should I even worry about it?

---

### Post by Rubi1200 on 2019-04-08
Hi and welcome to the forums :-)

Start by taking a look here [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1756800](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1756800)

If there are profiles no longer needed or perhaps corrupted it shows those errors.

There are discussions in the thread of what to do.

Hope this helps.

---

### Post by cookie505 on 2019-04-10
Thank you for replying, sorry I have been busy I haven't been able to mess with this. Nothing on the page seemed to help. I tried replacing those 2 profiles, as well as the ones listed in my error but it didn't change anything. I'm not sure what else to do.

---

### Post by eduardorq on 2019-04-10
Hi cookie505,

Can you solved it? I've the same trouble and dont fix yet :confused:

---

### Post by cookie505 on 2019-04-11
I have not discovered a solution yet

---

### Post by cookie505 on 2019-05-02
I figured it out

I had to install snapd

```
sudo apt install snapd
```

Don't know why this didn't happen automatically but it is what it is

---

