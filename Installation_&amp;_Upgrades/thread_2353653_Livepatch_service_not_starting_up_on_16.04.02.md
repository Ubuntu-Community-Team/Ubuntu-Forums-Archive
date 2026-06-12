---
title: "Livepatch service not starting up on 16.04.02"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by mangoHead84 on 2017-02-23
Hi,

I'm trying to install/configure the [Canonical Livepatch service]("https://www.ubuntu.com/server/livepatch") on one of my servers, however whenever I try to run the livepatch service, I get the following error from the service startup logs:

```
snap[3949]: 2017/02/23 21:57:52 Only Ubuntu 16.04 LTS is supported, exiting.
```
My problem is that the server is running version 16.04.02:

```
root@ip-10-0-16-09:~# cat /etc/issue
Ubuntu 16.04.2 LTS

root@ip-10-0-16-09:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

root@ip-10-0-16-09:~# uname -a
Linux ip-10-0-16-09 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
Is this limitation on purpose? It seems to me that a minor version upgrade should be supported as well, or is this not the case?

---

### Post by howefield on 2017-02-23
From the page that you link to...

> System requirements
Canonical&#8217;s Livepatches are available for the generic flavour of the 64-bit Intel/AMD (aka, x86_64, amd64) builds of the Ubuntu 16.04 LTS (Xenial) kernel, which is a Linux 4.4 kernel. Canonical Live Patches work on Ubuntu 16.04 LTS Servers and Desktops, on physical machines, virtual machines, and in the cloud

Presumably you are running the 16.10 Hardware Enablement Stack (HWE) which uses the 4.8 kernel.

---

### Post by mangoHead84 on 2017-02-23
> **howefield said:**
> Presumably you are running the 16.10 Hardware Enablement Stack (HWE) which uses the 4.8 kernel.

From the output of "lsb_release" and "uname" I'm running 16.04 with a 4.4 kernel which is what I want (LTS). Is it possible that these are giving me the wrong information? How can I tell whether HWE is running/enabled?

---

### Post by howefield on 2017-02-23
> **mangoHead84 said:**
> From the output of "lsb_release" and "uname" I'm running 16.04 with a 4.4 kernel which is what I want (LTS). Is it possible that these are giving me the wrong information? How can I tell whether HWE is running/enabled?

Well, if you installed with the 16.04 or 16.04.1 iso image you will be running the 4.4 kernel which should allow the live kernel patching. If you installed from the 16.04.2 image or manually upgraded the HWE you would be running the 4.8 kernel. 

If uname is telling you that you are running a 4.4 kernel, I'd trust it but might be worth doing a 

```
ll /boot
```

just to check what you have in there.

---

### Post by mangoHead84 on 2017-02-23
'll' showing only 4.4 kernels. I might try a reboot, it's saying "system restart required" on boot, so maybe it refuses to run if a kernel update is pending and throwing a misleading/incorrect error message? 

```
ubuntu@ip-10-0-0-40:~$ ll /boot/
total 145524
drwxr-xr-x  3 root root     4096 Feb 23 19:23 ./
drwxr-xr-x 23 root root     4096 Feb 23 19:04 ../
-rw-r--r--  1 root root  1244118 Jan 18 15:59 abi-4.4.0-62-generic
-rw-r--r--  1 root root  1245512 Feb  1 19:39 abi-4.4.0-63-generic
-rw-r--r--  1 root root  1245512 Feb 20 13:40 abi-4.4.0-64-generic
-rw-r--r--  1 root root   190047 Jan 18 15:59 config-4.4.0-62-generic
-rw-r--r--  1 root root   190247 Feb  1 19:39 config-4.4.0-63-generic
-rw-r--r--  1 root root   190247 Feb 20 13:40 config-4.4.0-64-generic
drwxr-xr-x  5 root root     4096 Feb 23 19:23 grub/
-rw-r--r--  1 root root 37261196 Feb 11 02:23 initrd.img-4.4.0-62-generic
-rw-r--r--  1 root root 37254200 Feb 21 06:19 initrd.img-4.4.0-63-generic
-rw-r--r--  1 root root 37254861 Feb 22 01:32 initrd.img-4.4.0-64-generic
-rw-------  1 root root  3875553 Jan 18 15:59 System.map-4.4.0-62-generic
-rw-------  1 root root  3883990 Feb  1 19:39 System.map-4.4.0-63-generic
-rw-------  1 root root  3883990 Feb 20 13:40 System.map-4.4.0-64-generic
-rw-------  1 root root  7070992 Jan 18 15:59 vmlinuz-4.4.0-62-generic
-rw-------  1 root root  7087088 Feb  1 19:39 vmlinuz-4.4.0-63-generic
-rw-------  1 root root  7087152 Feb 20 13:40 vmlinuz-4.4.0-64-generic
```

---

### Post by howefield on 2017-02-24
> **mangoHead84 said:**
> 'll' showing only 4.4 kernels. I might try a reboot,

Can't hurt to reboot., there is also a 3 machine limit on the live patching, if I recall correctly.

---

### Post by mangoHead84 on 2017-02-24
Rebooted and it's still throwing the same error. It shouldn't be hitting the limit, as this is the first server I've tried to get to LivePatch. Opened a bug against the "snap" package for this [https://bugs.launchpad.net/ubuntu/+source/snap/+bug/1667553](https://bugs.launchpad.net/ubuntu/+source/snap/+bug/1667553)

---

### Post by howefield on 2017-02-24
Does

```
canonical-livepatch status --verbose
```

produce anything, if you haven't tried it already ?

---

### Post by howefield on 2017-02-25
Another thread on the same subject which has been solved, might be worth a try..

[https://ubuntuforums.org/showthread.php?t=2353734](https://ubuntuforums.org/showthread.php?t=2353734)

```
sudo /snap/bin/canonical-livepatch enable ID
```

---

### Post by mangoHead84 on 2017-02-26
So, to update this thread the SystemD init system periodically tried to start up the "snap.canonical-livepatch.canonical-livepatchd.service" and at some point around Feb 24th, 21:53 UTC time, it started working:
```
Feb 24 03:03:56 ip-10-0-16-09 /usr/bin/snap[5967]: cmd.go:111: DEBUG: restarting into "/snap/core/current/usr/bin/snap"
Feb 24 03:03:56 ip-10-0-16-09 snap[5967]: 2017/02/24 03:03:56 Only Ubuntu 16.04 LTS is supported, exiting.
Feb 24 03:03:56 ip-10-0-16-09 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Main process exited, code=exited, status=1/FAILURE
Feb 24 03:03:56 ip-10-0-16-09 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Unit entered failed state.
Feb 24 03:03:56 ip-10-0-16-09 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Failed with result 'exit-code'.
Feb 24 03:03:57 ip-10-0-16-09 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Service hold-off time over, scheduling restart.
Feb 24 03:03:57 ip-10-0-16-09 systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
Feb 24 03:03:57 ip-10-0-16-09 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Start request repeated too quickly.
Feb 24 03:03:57 ip-10-0-16-09 systemd[1]: Failed to start Service for snap application canonical-livepatch.canonical-livepatchd.
Feb 24 21:53:50 ip-10-0-16-09 systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
Feb 24 21:53:51 ip-10-0-16-09 systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Feb 24 21:53:51 ip-10-0-16-09 /usr/bin/snap[13457]: cmd.go:111: DEBUG: restarting into "/snap/core/current/usr/bin/snap"
Feb 24 21:53:52 ip-10-0-16-09 snap[13457]: 2017/02/24 21:53:52 open /var/snap/canonical-livepatch/common/config: no such file or directory
Feb 24 21:53:52 ip-10-0-16-09 canonical-livepatch[13457]: Starting client version 7.21
Feb 24 21:53:52 ip-10-0-16-09 canonical-livepatch[13457]: No machine-token. Please run 'canonical-livepatch enable'!
Feb 24 21:53:52 ip-10-0-16-09 canonical-livepatch[13457]: No payload available.
```
I have NFI what caused it to start working, neither the apt history or "snap changes" show anything being updated around that time:
```
root@ip-10-0-16-09:~# snap changes
ID   Status  Spawn                 Ready                 Summary
10   Done    2017-02-26T03:03:49Z  2017-02-26T03:03:49Z  Refresh all snaps: no updates
11   Done    2017-02-26T06:14:13Z  2017-02-26T06:14:13Z  Refresh all snaps: no updates
12   Done    2017-02-26T13:01:39Z  2017-02-26T13:01:39Z  Refresh all snaps: no updates
13   Done    2017-02-26T19:58:29Z  2017-02-26T19:58:29Z  Refresh all snaps: no updates
14   Done    2017-02-27T00:53:39Z  2017-02-27T00:53:39Z  Refresh all snaps: no updates
```
Once the service was running, I was able to validate the key using the "canonical-livepatch enable ...." command and everything is working as expected.

It's still a bit of a mystery as to what caused it to start working. Maybe something changed server side on the Ubuntu Livepatch servers? Maybe there was some kind of "cached" OS version value that needed to be cleared?

Either way, will update the bug ticket and this thread can (probably?) be marked as resolved, though the resolution is basically "wait and it'll come right".

---

