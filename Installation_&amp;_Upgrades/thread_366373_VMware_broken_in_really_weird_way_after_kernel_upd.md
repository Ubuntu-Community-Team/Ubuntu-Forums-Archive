---
title: "VMware broken in really weird way after kernel update (not the same as other message)"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by johnqsmith on 2007-02-20
note; at first I thought this was the same thing as 
[http://ubuntuforums.org/showthread.php?t=358275](http://ubuntuforums.org/showthread.php?t=358275)
but it definitely isn't. I tried all the stuff there but it's not fixing things. I am running 6.06

This started after an update to 2.8.15-28 but I rolled back and still haven't been able to fix it. The primary symptom is that the vmnet interfaces don't show up. When I look with ps I see:
root      6907  0.0  0.0   1416   164 pts/1    S    19:55   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      6919  0.0  0.0   1664   416 ?        Ss   19:55   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf

as opposed to 
root     26247  0.0  0.0   1412   164 pts/1    S    19:56   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root     26259  0.0  0.0   1664   436 ?        Ss   19:56   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root     26266  0.0  0.0   1412   164 pts/1    S    19:56   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8.pid /dev/vmnet8 vmnet8
root     26277  0.0  0.0   1412   164 pts/1    S    19:56   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1.pid /dev/vmnet1 vmnet1
root     26291  0.0  0.0   1724   300 ?        Ss   19:56   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
root     26292  0.0  0.0   1724   300 ?        Ss   19:56   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1

which I see on my healthy machine which hasn't updated/rebooted yet. On the healthy machine it shows vmnet1 and 8 when I do a normal ifconfig but on this broken machine it does not.

I have done /etc/init.d/vmware restart and I still only see the 2 out of 6 things running

I have done vmware-uninstall.pl as root and then went and reinstalled it

I have downgraded to 2.6.15-27 and 26 (what I'm currently on) and uninstalled it and reinstalled it but it didn't help.

I have checked that /dev/vmnet1 and 8 exist

I have tried re-running vmware-config.pl

I have run the missing commands as root and then if I do an ifconfig it doesn't show them but if I do an ifconfig -a it does, but they are not properly bound to their respective IPs.

I have tail -f'ed /var/log/messages /var/log/ but the only things I see are things like

(from /var/log/messages)
Feb 20 19:55:55 localhost kernel: [17181222.876000] bridge-eth0: already up

(from /var/log/debug when I do a /etc/init.d/vmware restart)
Feb 20 20:05:10 localhost kernel: [17181778.128000] /dev/vmmon[7197]: Module vmmon: unloaded
Feb 20 20:05:11 localhost kernel: [17181778.636000] bridge-eth0: down
Feb 20 20:05:11 localhost kernel: [17181778.636000] bridge-eth0: detached
Feb 20 20:05:13 localhost kernel: [17181781.464000] /dev/vmmon[7274]: Module vmmon: registered with major=10 minor=165
Feb 20 20:05:13 localhost kernel: [17181781.464000] /dev/vmmon[7274]: Module vmmon: initialized
Feb 20 20:05:14 localhost kernel: [17181781.932000] /dev/vmnet: open called by PID 7297 (vmnet-bridge)
Feb 20 20:05:14 localhost kernel: [17181781.932000] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 20 20:05:14 localhost kernel: [17181781.932000] /dev/vmnet: port on hub 0 successfully opened
Feb 20 20:05:14 localhost kernel: [17181781.932000] bridge-eth0: enabling the bridge
Feb 20 20:05:14 localhost kernel: [17181781.932000] bridge-eth0: up
Feb 20 20:05:14 localhost kernel: [17181781.932000] bridge-eth0: attached
Feb 20 20:05:14 localhost kernel: [17181781.948000] /dev/vmnet: open called by PID 7309 (vmnet-natd)
Feb 20 20:05:14 localhost kernel: [17181781.948000] /dev/vmnet: hub 8 does not exist, allocating memory.
Feb 20 20:05:14 localhost kernel: [17181781.948000] /dev/vmnet: port on hub 8 successfully opened


I don't really understand why uninstalling, reinstalling (with the proper 2.6.15-26 headers in /usr/src which I point to during vmware-config.pl) and then doing an /etc/init.d/vmware restart doesn't solve this problem.

Has anyone seen anything similar to this before? Because I'm completely stumped. Oh, also I have 2 identical machines which are broken in exactly this way, and the 3rd one is identical but hasn't been rebooted in a long time (but the broken ones have recently)

Thanks

John

---

### Post by athensy on 2007-02-21
VMware server will be broken every time after kernel update, since the new kernel without the modules need to run the VMware server. So, it needs to reinstall the VMware server every time after kernel update. You may follow the link below and it may help you to recover your machines.

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Good luck,
Athens Yan

---

### Post by johnqsmith on 2007-02-23
I'm sorry, I thought I posted it, but I am using VMware workstation. I can not install server(free) as it's limited snapshot capabilities is a hinderance for my users.

John

---

