---
title: "rmap.c Kernel Bug, update safe?"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Kurdt on 2007-01-02
Hi guys,

I have an ubuntu based server, I had a crash on one of my daemons (amavisd-new) and I have this at kern.log:

> [B]Dec 30 16:49:07 pc009 kernel: [17460453.680000] ------------[ cut here ]------------
Dec 30 16:49:07 pc009 kernel: [17460453.680000] kernel BUG at mm/rmap.c:486!
Dec 30 16:49:07 pc009 kernel: [17460453.680000] invalid operand: 0000 [#2][/B]
Dec 30 16:49:07 pc009 kernel: [17460453.680000] PREEMPT
Dec 30 16:49:07 pc009 kernel: [17460453.680000] Modules linked in: rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_userspace cpufreq_statDec 30 16:49:07 pc009 kernel: [17460453.680000] CPU:    0
Dec 30 16:49:07 pc009 kernel: [17460453.680000] EIP:    0060:[page_remove_rmap+34/48]    Not tainted VLI
Dec 30 16:49:07 pc009 kernel: [17460453.680000] EFLAGS: 00210286   (2.6.15-26-386)
Dec 30 16:49:07 pc009 kernel: [17460453.680000] EIP is at page_remove_rmap+0x22/0x30
Dec 30 16:49:07 pc009 kernel: [17460453.680000] eax: ffffffff   ebx: d4a4a4e0   ecx: c104ce80   edx: c104ce80
Dec 30 16:49:07 pc009 kernel: [17460453.680000] esi: b7d38000   edi: c104ce80   ebp: 00000020   esp: d4589dcc
Dec 30 16:49:07 pc009 kernel: [17460453.680000] ds: 007b   es: 007b   ss: 0068
Dec 30 16:49:07 pc009 kernel: [17460453.680000] Process amavisd-new (pid: 4239, threadinfo=d4588000 task=d7b22a70)
Dec 30 16:49:07 pc009 kernel: [17460453.680000] Stack: c014ee7f c104ce80 ccb848e0 ffffffff 00000000 cdf33b7c b7d39000 d4589e54
Dec 30 16:49:07 pc009 kernel: [17460453.680000]        cdf33b7c c014f0f2 c03dc944 d4a4be34 cdf33b7c b7d38000 b7d39000 d4589e54
Dec 30 16:49:07 pc009 kernel: [17460453.680000]        00000000 cdf33b7c b7d38fff d4a4be34 b7d38000 b7d39000 d4588000 c014f1fe
Dec 30 16:49:07 pc009 kernel: [17460453.680000] Call Trace:
Dec 30 16:49:07 pc009 kernel: [17460453.680000]  [zap_pte_range+271/672] zap_pte_range+0x10f/0x2a0


This made my amavisd-new process to crash, and I have to completely shut down my ubuntu to make it work again, is this a known bug?
This is not the first time I got this.

I have 2.6.15-26-386 #1 PREEMPT, when I try to upgrade with apt-get upgrade (to get a new kernel and maybe find a solution)

[B]
I have that these packages will be kept back:[/B]
  linux-image-386 linux-restricted-modules-386 proftpd spamassassin totem
**These will be updated**
  evince gdm gnupg libapache2-mod-php5 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 libgsf-1-113
  libgsf-1-common libmysqlclient15off libpango1.0-0 libpango1.0-common libssl-dev libssl0.9.8 libxine-main1 linux-386
  linux-image-2.6.15-26-386 linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common lvm2 mysql-client mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0 openssl php-pear php5-cgi php5-cli php5-common php5-gd php5-ldap php5-mysql php5-mysqli
  php5-snmp phpmyadmin python2.4 python2.4-examples python2.4-gdbm python2.4-minimal python2.4-tk spamc ubuntu-base ubuntu-desktop
  ubuntu-minimal ubuntu-standard xinit xserver-xorg-core

Some questions as this is a very important server:

What exactly means that some packages will be kept? 
I read on some website that I should use apt-get dist-upgrade and not apt-get upgrade, is this correct?
No packages will be removed right?
Updating to new kernel will fix this bug?  (2.6.15-27)

[B]Sorry me for this basic apt doubts, I am almost new at it.
Thanks Guys[/B]

---

### Post by Kurdt on 2007-01-04
Anyone? Please ? :-k

---

