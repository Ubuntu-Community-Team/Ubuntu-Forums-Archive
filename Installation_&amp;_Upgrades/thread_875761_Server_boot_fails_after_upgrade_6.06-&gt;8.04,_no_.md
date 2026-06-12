---
title: "Server boot fails after upgrade 6.06-&gt;8.04, no logs, no access, no clue, please help"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by OscarO on 2008-07-31
After having worked with ubuntu on local pc's for a while I decided to run it on my server as well. It's running great and I didn't anticipate trouble when upgrading 6.06LTS to 8.04LTS.

I updated everything to the last 6.06 packages, rebooted and updated to 8.04. Everything went well and I followed the advice to reboot. Nothing happened.

The server is a Virtual one with recovery access to the files. Through 9 hours of trial and error I've found that only /var/log/wtmp gives a response (see below) when /etc/init.d/rc is made non executable. Other than that there are no logs after the upgrade and I need ssh to acces the machine.

So the server doesn't boot, isn't accessible and doesn't tell me anything on what the problem is. Can you help me tackle this challenge?

Server output below.

 Your VPS is under repair mode now.
 You can access the file system of your VPS under /repair directory.
 To finish repair mode, eihter login into the Customer Service Area
 ([https://config.stratoserver.net](https://config.stratoserver.net)) and select
 'Server Configuration' -> 'RecoveryManager'.
=============== VPS REPAIR MODE ===============
root@h1385896:~# last -f /repair/var/log/wtmp | head
reboot   system boot  2.6.9-023stab044 Thu Jul 31 10:02          (00:09)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 07:33          (00:49)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 07:15          (00:05)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 06:57          (00:04)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 06:40          (00:05)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 06:16          (00:15)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 06:03          (00:04)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 05:52          (00:03)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 05:40          (00:05)
reboot   system boot  2.6.9-023stab044 Thu Jul 31 05:15          (00:05)

---

### Post by dstew on 2008-07-31
What virtualization program are you using to run Ubuntu?

---

### Post by arcane47 on 2008-11-11
I am suffering the same problem, on OpenVZ.

Any resolution on this?

---

### Post by OscarO on 2008-11-11
I didn't manage to resolve it and dumped Ubuntu on the server to replace it with Suse.

After a while the most promessing tip pointed to the boot-loader being replaced during the upgrade.

6.06 uses LILP and 8.04 uses GRUB.

I didn't try the fix because it arrived to late.

---

