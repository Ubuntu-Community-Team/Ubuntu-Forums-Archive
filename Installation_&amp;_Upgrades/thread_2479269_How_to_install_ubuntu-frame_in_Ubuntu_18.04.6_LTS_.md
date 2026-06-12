---
title: "How to install ubuntu-frame in Ubuntu 18.04.6 LTS (GNU/Linux 4.9.253-tegra aarch64)"
date: 2022-09-20
forum: Installation &amp; Upgrades
---

### Post by eldho1416 on 2022-09-20
Hi Everyone,

I have been trying to install ubuntu-frame in Jetson nano and I'm getting the below errors

```
$ sudo snap install ubuntu-frameerror: cannot perform the following tasks:
- Mount snap "ubuntu-frame" (3901) (systemctl command [start snap-ubuntu\x2dframe-3901.mount] failed with exit status 1: Job for snap-ubuntu\x2dframe-3901.mount failed.
See "systemctl status "snap-ubuntu\\x2dframe-3901.mount"" and "journalctl -xe" for details.
)



```

```
$ systemctl status snap-ubuntu\\x2dframe-3901.mount&#9679; snap-ubuntu\x2dframe-3901.mount
   Loaded: not-found (Reason: No such file or directory)
   Active: failed (Result: exit-code) since Tue 2022-09-20 10:42:29 IST; 59s ago


Sep 20 10:42:29 ubuntu systemd[1]: Mounting Mount unit for ubuntu-frame, revision 3901...
Sep 20 10:42:29 ubuntu mount[15511]: mount: /snap/ubuntu-frame/3901: wrong fs type, bad option, bad superb
Sep 20 10:42:29 ubuntu systemd[1]: snap-ubuntu\x2dframe-3901.mount: Mount process exited, code=exited stat
Sep 20 10:42:29 ubuntu systemd[1]: snap-ubuntu\x2dframe-3901.mount: Failed with result 'exit-code'.
Sep 20 10:42:29 ubuntu systemd[1]: Failed to mount Mount unit for ubuntu-frame, revision 3901.
lines 1-9/9 (END)



```

How do I solve this issue?

PS: I have asked this in Nvidia forums and didn't get a useful response so I'm posting it here.

Thank you

---

### Post by ian-weisser on 2022-09-20
Are you able to install ANY snaps on that system?

Is it stock Ubuntu Server 18.04? Or some version custom-rolled for the hardware? Or something else?

---

### Post by eldho1416 on 2022-09-21
Hi Ian,

Thanks for the reply.

Yes I'm able to install other snaps also yes it the ubuntu 18.04 LTS is customised for Jetson boards I believe.

Here is the example where other snaps are getting installed.
```

~$ sudo snap install hello-world
hello-world 6.4 from Canonical** installed

```

And i also think the issue is in installing mesa-core20 in Jetson nano and i'm not sure about the cause here.

---

### Post by eldho1416 on 2022-09-21
Wait ubuntu-frame with mesa-core20 cannot be installed in ubuntu 18.04 LTS? Is there anything called mesa-core 18?

---

