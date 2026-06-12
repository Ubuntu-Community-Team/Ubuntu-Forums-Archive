---
title: "irw kills lircd on Feisty (w/MythTV)"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by stevenbparks on 2007-06-05
Hi all,
I'm trying to setup a homebrew serial IR receiver to work with a MythTV installation on Ubuntu 7.04. I've been following the instructions on [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty), but when I get to the part that has me start lircd and run irw, I run into problems that I'm too naive to fix.

So when I run "sudo /usr/sbin/lircd -n --driver=default -d /dev/lirc0", I get the following response:

lircd-0.8.2-CVS[8678]: repeat_gap will be ignored if CONST_LENGTH flag is set
lircd-0.8.2-CVS[8678]: lircd(userspace) ready

Then in another terminal (tab), I run "irw", which kills the lircd command immediately and generates the following lines in the first tab:

lircd-0.8.2-CVS[8678]: accepted new client on /dev/lircd
lircd-0.8.2-CVS[8678]: could not open /dev/lirc0
lircd-0.8.2-CVS[8678]: default_init(): Device or resource busy
lircd-0.8.2-CVS[8678]: caught signal
Terminated

"lsmod | grep lirc" shows the following:

lirc_serial 14080 0
lirc_dev 15988 1 lirc_serial

"dmesg" shows the following new lines:

[92062.233994] IRQ handler type mismatch for IRQ 3
[92062.234011] current handler: acpi
[92062.234064] [<c015410e>] setup_irq+0x12e/0x1e0
[92062.234094] [<c0109646>] read_tsc+0x6/0x10
[92062.234130] [<e05274a0>] irq_handler+0x0/0x5d0 [lirc_serial]
[92062.234147] [<c0154263>] request_irq+0xa3/0xc0
[92062.234165] [<e0528200>] set_use_inc+0xb0/0x1f4 [lirc_serial]
[92062.234181] [<e0405a43>] irctl_open+0xe3/0x240 [lirc_dev]
[92062.234196] [<c017eff5>] may_open+0x65/0x260
[92062.234222] [<c01ed6af>] kobject_get+0xf/0x20
[92062.234233] [<e0405960>] irctl_open+0x0/0x240 [lirc_dev]
[92062.234245] [<c0179458>] chrdev_open+0xa8/0x170
[92062.234262] [<c01793b0>] chrdev_open+0x0/0x170
[92062.234269] [<c0174caa>] __dentry_open+0xba/0x1c0
[92062.234302] [<c0174e65>] nameidata_to_filp+0x35/0x40
[92062.234316] [<c0174ec0>] do_filp_open+0x50/0x60
[92062.234367] [<c0174f1e>] do_sys_open+0x4e/0xf0
[92062.234387] [<c0174ffc>] sys_open+0x1c/0x20
[92062.234397] [<c01031f0>] sysenter_past_esp+0x69/0xa9
[92062.234437] =======================
[92062.234600] lirc_serial: IRQ 3 busy

I don't know enough about serial ports and IRQs to know why IRQ 3 is busy.

Any help would be appreciated!
Thanks!
SBP

---

### Post by dogas on 2007-12-06
I know this topic is old, but I figured my solution would help people in the future.

I ran into the same issue, different circumstances.  In fact, any time you get a "connection refused" error running irw (and then it kills lircd), it always seems to be the same issue.

Lirc is sort of a "middle man" between the raw input from the transmitter and something that irw can actually use.  So the issue is that irw is most likely attempting to read this raw input (not fed to by lircd), and thus is freaking out and bringing down lircd with it.

I noticed this by doing a ```
cat /dev/lirc0
``` and seeing character output when pressing buttons on my remote, but lircd was not running.  This was the eureka moment.

Run lircd manually like so:

```

lircd --device=/dev/lirc0 --output=/dev/lircd -n my_irrecord_conf

```

The difference is that we are specifying the output device (so now lircd is effectlively the middleman between the raw input from the remote at /dev/lirc0 and the marshaled output to /dev/lircd which irw is expecting.

NOW you can run irw and you should see "client connected" in the lircd output.  Walla.

---

