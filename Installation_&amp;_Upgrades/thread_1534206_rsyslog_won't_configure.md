---
title: "rsyslog won't configure"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by burtybob on 2010-07-19
Hi all,

I have upgraded to 10.04 or tried to at least. I have a server at OVH and it was running 8.04 desktop and I decided to upgrade it to 10.04 little relizing that OVHs kernels didn't work with 10.04 so after the reboot phase it ended up going into a netboot rescue mode.

I have got the latest kernel from the kernal.ubuntu area and installed it. Run grub-update, reboot... Nothing. So I decided to run apt-get install just to make sure there was nothing that needed to be installed.
The following is what I have got
```
Setting up rsyslog (4.2.0-2ubuntu8) ...
runlevel:/var/run/utmp: No such file or directory
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rsyslog
 ubuntu-minimal

```
Now from my research this means that I don't have a bootable system.

The following is the response I got from OVHs team
```
The server blocks during the system loading on the
following message:
init plymouth main process (2078) killed by SEGV signal
init plymouth - splash main process (1294) terminated with
status 2
```

I need/hope to find a way to resolve this without having to reinstall as there is nearly 400GB of stuff on the hard drives.

All help will be greatly appreciated.

---

### Post by dino99 on 2010-07-19
boot without "splash" as its a plymouth issue

---

### Post by burtybob on 2010-07-19
Thanks, I tried that and it didn't seem to work :'(. The server still didn't boot up. It boots up in their "rescue mode". I think the problem is that the ubuntu upgrade didn't complete properly as the first bit in code tags shows. I think that is now my problem.

---

### Post by burtybob on 2010-07-19
Ok so I have now got syslog thingy installed and configured and with it the ubuntu-minimal did as well.

Still no luck with booting though.

Summary of what I did:

I changed the CMD_DEFUALT line from ="quiet splash" to = "splash" didn't work.
Changed it to ="" didn't work.
Changed it to ="nomodeset" didn't work.

ARGH Please can anyone give anymore suggestions. And I am probably thinking that your idea is right though. I just can't seem to configure it right. (PS Yes I did update-grub in between each change and rebooted)

---

