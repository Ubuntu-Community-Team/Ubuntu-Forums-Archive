---
title: "sshd init script says OK but sshd not loading"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by ardya on 2007-04-21
Hi...after an apparently successful dist-upgrade of xubuntu edgy to feisty, all seems well, except for sshd not actually starting at boot. Watching the boot process I see OK from the init script that starts sshd, links exist for the runlevel I'm using (N 2 according to runlevel command), but lsof nor ps ax show sshd running.

I can manually start/stop sshd via /etc/init.d/ssh script just fine.
Is it possible this new Network Manager thing I see during boot could be delaying eth0 init so no iface exists for sshd to bind to? If so, why would ssh init script report OK?


How could I debug this?

---

### Post by ardya on 2007-04-21
Help?

---

### Post by ardya on 2007-04-21
Ok, this looks like a bug. In sshd_config I have ListenAddress 192.168.1.3
If I comment that out, sshd will then bind to any interface successfully.
Why this sucks is because I use IPv6 and don't want sshd listening on IPv6 iface, hence using the ListenAddress
directive. A workaround for ME is to use -4 in /etc/default/ssh, but it won't resolve the issue if multiple IPv4 ifaces exist and the user wants to listen on one only.

Looking at the system logs, the errors I saw mention not being able to use assigned address (iface not up yet???):

Apr 21 19:33:07 daw1 sshd[2788]: error: Bind to port 22 on 192.168.1.3 failed: Cannot assign requested address.

The network init has changed in Feisty such that sshd is started before the iface is up?

In any case, I found all this by wiping my xubuntu feisty dist-upgrade, downloading the ubuntu feisty iso, installing fresh, and when I restored sshd_config from the working edgy (pre-dist-upgrade to feisty), found sshd stopped loading at boot even though the init script for it says OK....ITS OBVIOUSLY NOT OK.

heh

---

### Post by Swab on 2007-04-21
Submit a bug report?

---

### Post by ardya on 2007-04-22
Seems the smbd component of samba also fails to load at boot:

[2007/04/22 02:17:36, 0] lib/interface.c:load_interfaces(225)
  WARNING: no network interfaces found

---

### Post by jetpeach on 2007-04-22
where did you find that samba is also not loaded? i am having problems with samba, unable to use it at all on my system when it worked fine before the upgrade. in the past, i've blacklisted/aliases out ipv6 to try to stop it from working, but it's re-enabled now. but on the thread talking about it people are saying not to just disable ipv6 anymore, since in the future it is important and bugs with it should be tackled rather than avoided... 
anyway, ssh is working for me though, just not samba.

---

### Post by ardya on 2007-04-22
/var/log/samba/log.smbd

lsof -i doesnt show it listening, but nmbd is, a simple restart (/etc/init.d/samba restart) brings smbd up.

---

