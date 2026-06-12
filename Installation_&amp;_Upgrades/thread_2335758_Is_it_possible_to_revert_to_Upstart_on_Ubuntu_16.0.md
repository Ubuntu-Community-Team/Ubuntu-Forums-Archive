---
title: "Is it possible to revert to Upstart on Ubuntu 16.04?"
date: 2016-09-01
forum: Installation &amp; Upgrades
---

### Post by y-tech on 2016-09-01
For reasons I'll not detail here (unless asked) I want to revert back to upstart instead of systemd. I've done:
```

$ apt-get install upstart-sysv
$ update-initramfs -u
$ reboot
```
Per advice I've found on various posts for 15.10. It sort-of works for 16.04, but I have no login screen. In `dmesg` I get:
```

[  144.803298] systemd-logind[8281]: New seat seat0.
[  144.817793] systemd-logind[8281]: Watching system buttons on /dev/input/event3 (Power Button)
[  144.817980] systemd-logind[8281]: Watching system buttons on /dev/input/event5 (Video Bus)
[  144.818150] systemd-logind[8281]: Watching system buttons on /dev/input/event1 (Power Button)
[  144.818303] systemd-logind[8281]: Watching system buttons on /dev/input/event0 (Lid Switch)
[  144.818461] systemd-logind[8281]: Watching system buttons on /dev/input/event2 (Sleep Button)
[  144.818613] systemd-logind[8281]: Watching system buttons on /dev/input/event15 (Dell WMI hotkeys)
[  144.823088] systemd-logind[8281]: Failed to start user service, ignoring: Unknown unit: user@1001.service

```
which may or may not be relavant. Suggestions?

---

### Post by howefield on 2016-09-01
This may or may not help.

[http://askubuntu.com/questions/779640/how-to-remove-systemd-from-ubuntu-16-04-and-prevent-its-usage](http://askubuntu.com/questions/779640/how-to-remove-systemd-from-ubuntu-16-04-and-prevent-its-usage)

```
apt-get install upstart-sysv sysvinit-utils -y
cp /usr/share/sysvinit/inittab /etc/inittab
update-initramfs -u
reboot
```

---

### Post by y-tech on 2016-09-01
howefield - thanks for the reply. That's basically the link I used to do what I did. You'll notice that the code you posted from that link is basically identical to mine. In fact I did install the sysvinit-utils, though neglected to show that in my post. The poster of that link apparently copied his/her instructions from a similar Debian link ([http://without-systemd.org/wiki/index.php/How_to_remove_systemd_from_a_Debian_jessie/sid_installation](http://without-systemd.org/wiki/index.php/How_to_remove_systemd_from_a_Debian_jessie/sid_installation)), which also shows the `cp /usr/share/sysvinit/inittab /etc/inittab` line. However, there is no /usr/share/sysvinit/inittab in Ubuntu 16.04, nor did Ubuntu have such a file at least as far back as 14.04. However, the Unbuntu man page says Upstart does not use inittab, "and instead reads its configuration from files in /etc/init."

I absolutely need to do something at shutdown that systemd apparently cannot do, so I either need to revert to Upstart, or abandon Ubuntu and find another distro -- which I'd rather not do.

Other ideas?

MORE INFO

Actually, after posting the above, I looked in /etc/init and looked at /etc/init/lightdm.conf. For the heck of it, I started lightdm at the command line and I got the login screen.

So, can anyone tell me why it is not starting automatically and how to make it do so?

---

### Post by mc4man on 2016-09-01
i may try tonight to do this on a disposable install as i'd like to see if systemd is behind some bad behaviors
What also has bothered me is grub presents an upstart option that obviously fails to work. A bug about that has been ignored for some time - 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1535096](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1535096)

---

### Post by y-tech on 2016-09-01
If you are interested in why systemd is not working for me, see [http://www.linuxquestions.org/questi...ml#post5599000]("http://www.linuxquestions.org/questions/linux-server-73/how-to-run-systemd-service-first-4175588181/page2.html#post5599000"). Basically, I need to execute a virtual machine shutdown before any users are logged out. Apparently systemd cannot do this, or at least neither I nor a half-dozen unbuntu 'experts' can figure out how to do it. Upstart has no problem with this. 

At the moment, I'm mostly interested in how to get lightdm to start at boot now that Upstart is supposedly back. Perhaps I'll try removing systemd altogether and see what happens.

---

### Post by y-tech on 2016-09-01
MORE INFO: When I now run Cinnamon, it comes up, but I get the message, " Running in software rendering mode. Cinnamon is currently running without video hardware acceleration and as a results, you may observe much higher than normal CPU usage."

Also, I cannot run virtualBox -- it appears to want systemd:
```

# /sbin/vboxconfig
Synchronizing state of vboxdrv.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable vboxdrv
Synchronizing state of vboxballoonctrl-service.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable vboxballoonctrl-service
Synchronizing state of vboxautostart-service.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable vboxautostart-service
Synchronizing state of vboxweb-service.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable vboxweb-service
vboxdrv.sh: Starting VirtualBox services.
Failed to start vboxdrv.service: Unknown unit: vboxdrv.service
See system logs and 'systemctl status vboxdrv.service' for details.
Failed to start vboxballoonctrl-service.service: Unknown unit: vboxballoonctrl-service.service
See system logs and 'systemctl status vboxballoonctrl-service.service' for details.
Failed to start vboxautostart-service.service: Unknown unit: vboxautostart-service.service
See system logs and 'systemctl status vboxautostart-service.service' for details.
Failed to start vboxweb-service.service: Unknown unit: vboxweb-service.service
See system logs and 'systemctl status vboxweb-service.service' for details.

```

Any ideas at all?

---

