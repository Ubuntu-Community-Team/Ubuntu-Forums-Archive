---
title: "Ideas please? Debugging 'upstart' on a headless box"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by mflint on 2010-03-25
Hey,

Here's the scenario:
[LIST]
[*]currently running Ubuntu 9.04 on a headless PPC box (the Kurobox)
[*]when I say "headless", I really mean it! (So cannot just plug in a keyboard/monitor)
[*]Ubuntu 9.04 running fine with a custom 2.6.27.5 kernel
[*]trying to create a fresh installation of Ubuntu 10.04
[*]when I boot the machine, I can only see boot-time messages via netconsole
[/LIST]

So I debootstrapped Ubuntu 10.04 into a new partition, installed "sshd" and "ubuntu-base" and all its dependencies and compiled a new kernel. This is exactly the same kernel as the one I have working with 9.04, with exactly the same config file. (And the same installation process I used when installing 9.10 and 8.04 previously)

When I reboot, using "netconsole" kernel parameter, I can see the kernel booting and mounting the root filesystem read-only... but then everything stops.

Usually, I'd then "ssh" into the box to continue installing stuff, but "sshd" isn't running. (nmap says that all ports are closed too). But I can ping the box, so it's not completely dead.

Questions:
[LIST]
[*]"netconsole" kernel parameter only broadcasts kernel logging messages - but I'd like to see "upstart" output too. Is this possible?
[*]failing that, can I force "upstart" to log somewhere local? (I know I'd need to force the root fs to be mounted RW by the kernel)
[*]any other bright ideas? ;-)
[/LIST]

One other thing: I did try changing the "init" process (by passing "init=/path/to/script" to the kernel - where the script only performs "dhcpclient eth0" and "sshd") but that doesn't seem to make any difference.

In fact, passing "init=/sbin/donkeys" doesn't make any difference either... I was at least expecting a kernel panic, but there is none visible, and eth0 comes up (is pingable) just like usual.

Questions
[LIST]
[*]why does the kernel apparently ignoring the "init=" parameter?
[*]how can I determine whether the problem lies with the kernel (not finding and executing /sbin/init correctly) or with upstart (which may just be failing somehow)?
[/LIST]

So that's where I am. Any insightful / inventive ideas welcome! :)  I'm quite used to hacking this box, but this has got me stumpted.

Matthew



(Reminder: I cannot simply add a monitor because it's a headless box with no video hardware)

---

### Post by mflint on 2010-03-25
After a bit of googling, I wonder whether it's related to this issue: [https://bugs.launchpad.net/ubuntu/karmic/+source/ifupdown/+bug/497299](https://bugs.launchpad.net/ubuntu/karmic/+source/ifupdown/+bug/497299)

Would still like to see messages from Upstart though!

My ideal solution would be to be specify these kernel arguments: "netconsole=.... console=netconsole"

---

