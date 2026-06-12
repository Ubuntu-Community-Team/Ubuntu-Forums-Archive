---
title: "Ubuntu upgrade from 13.04 to 13.10 - service problems - unknown job"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by Ikka3990 on 2013-10-17
I updated  my laptop from Ubuntu 13.04 to Ubuntu 13.10. Everything seems to work well, but I am having trouble with some services. The service command would not identify services like lightdm and network-manager. (The latter is important to me because I like to restart my networking from command line.)

```

root@Dibbiya:~# service network-manager restart
stop: Unknown job: network-manager
start: Unknown job: network-manager

root@Dibbiya:~# service networking restart
stop: Unknown job: networking
start: Unknown job: networking

root@Dibbiya:~# service lightdm stop
stop: Unknown job: lightdm

root@Dibbiya:~# service --status-all 
 [ + ]  acpid
 [ + ]  anacron
 [ + ]  apparmor
 [ ? ]  apport
 [ + ]  avahi-daemon
 [ ? ]  binfmt-support
 [ + ]  bluetooth
 [ - ]  brltty
 [ + ]  console-font
 [ + ]  console-setup
 [ + ]  cron
 [ + ]  cups
 [ + ]  cups-browsed
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ + ]  kmod
 [ ? ]  lightdm
 [ ? ]  networking
 [ ? ]  ondemand
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ - ]  procps
 [ - ]  pulseaudio
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ + ]  rfkill-restore
 [ + ]  rfkill-store
 [ - ]  rsync
 [ + ]  rsyslog
 [ + ]  saned
 [ ? ]  sendsigs
 [ + ]  setvtrgb
 [ - ]  smartmontools
 [ ? ]  speech-dispatcher
 [ - ]  sudo
 [ ? ]  tlp
 [ + ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  vboxautostart-service
 [ + ]  vboxballoonctrl-service
 [ + ]  vboxdrv
 [ + ]  vboxweb-service
 [ - ]  virtualbox
 [ + ]  winbind
 [ - ]  x11-common


```

I would really appreciate any ideas as to what might have gone wrong!

---

### Post by Enrico_Schenone on 2013-10-18
I have the same problem.
It seems to be a general bug of 13.10.
It occurs with many services, not only with sshd (eg. cron).

First occurred when I have made the dist-upgrade from Kubuntu 13.04.
Then, suspecting something failed during dist-upgrade, I have made a fresh installation.

Unfortunately it have the same behaviour.
I hope someone can give us a solution or developers will release a fix asap (hours not days), because at this point all people which have installed the 13.10 are frozen.

Sincerely.

---

### Post by Ikka3990 on 2013-10-18
Have you filed a bug report?

> **Enrico_Schenone said:**
> I have the same problem.
It seems to be a general bug of 13.10.
It occurs with many services, not only with sshd (eg. cron).

First occurred when I have made the dist-upgrade from Kubuntu 13.04.
Then, suspecting something failed during dist-upgrade, I have made a fresh installation.

Unfortunately it have the same behaviour.
I hope someone can give us a solution or developers will release a fix asap (hours not days), because at this point all people which have installed the 13.10 are frozen.

Sincerely.

---

### Post by kib0rg1337 on 2013-10-18
Confirmed.

I faced this bug since beta-1, and in release it is still here.

The problem is that "service" and "initctl" commands requires sudo-access even if you root, so if you use "sudo service ..." everything is working.


Example:
```

root@test-virtual-machine:~# whoami
root

root@test-virtual-machine:~# service network-manager stop
stop: Unknown job: network-manager

root@test-virtual-machine:~# sudo service network-manager stop
network-manager stop/waiting

root@test-virtual-machine:~# initctl start network-manager
initctl: Unknown job: network-manager

root@test-virtual-machine:~# sudo initctl start network-manager
network-manager start/running, process 2469

```


Also I have just found an interesting thing,
if you logging in terminal with (CTRL+ALT+F1), then service/initctl does not requie sudo prefix:

[IMG]http://i.imgur.com/Bncc0li.png[/IMG]


Temporarily it can be fixed like this:

```

root@test-virtual-machine:~# alias service="sudo service"
root@test-virtual-machine:~# alias initctl="sudo initctl"

```

---

### Post by Ikka3990 on 2013-10-18
Thanks, that works!

---

### Post by Enrico_Schenone on 2013-10-21
Thanks for your work-around.
It works.
I created a .bash_aliases file into my home directory with the two suggested lines.
At the moment no fix has been released.

---

### Post by brunonova on 2013-11-05
I think I've found out the real "problem".
And I think it's not a problem. Look here [http://ifdeflinux.blogspot.pt/2013/04/upstart-user-sessions-in-ubuntu-raring.html](http://ifdeflinux.blogspot.pt/2013/04/upstart-user-sessions-in-ubuntu-raring.html).
It seems Upstart now has "user sessions".

If you execute "status lightdm", it returns "unknown task". But if you execute "status --system lightdm" it works fine.
Additionally, execute "initctl list" and "initctl --system list". The second one lists a lot more services.
Then try to run "stop hud" without using sudo (you should have this service listed in "initctl list"). It will work! Try opening the HUD and serching something. It won't return anything (but the service will be restarted when you search).
So, as a user, you can manage the services listed by "initctl list". And to manage upstart system services, you need the "--system" argument.

Now, "service" is not Upstart ("--system" won't work here). That's the older system of managing services (still used).
So, if the "service <SERVICE> start|stop|status" command fails, try "initctl --system start|stop|status <SERVICE>" or just "start|stop|status --system <SERVICE>" (that's Upstart).

---

