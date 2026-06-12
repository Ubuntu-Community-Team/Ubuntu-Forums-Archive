---
title: "Shorewall fails to start at boot after upgrade to 15.04"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2015-06-16
After upgrading to 15.04, shorewall fails to start at boot with the error

**Job shorewall.service/start deleted to break ordering cycle starting with shorewall.service/start**

I can start shorewall manually without problems

The following shows the systemctl status

>> sudo systemctl status -l shorewall.service 
shorewall.service - LSB: Configure the firewall at boot time
   Loaded: loaded (/etc/init.d/shorewall)
   Active: inactive (dead)
     Docs: man:systemd-sysv-generator(8)

Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found ordering cycle on shorewall.service/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on network-online.target/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on NetworkManager-wait-online.service/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on basic.target/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on paths.target/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on cups.path/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on sysinit.target/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Found dependency on shorewall.service/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Breaking ordering cycle by deleting job shorewall.service/start
Jun 16 10:34:00 LeosGameLaptop systemd[1]: Job shorewall.service/start deleted to break ordering cycle starting with shorewall.service/start

Snippet from syslog is
Jun 16 10:13:21 LeosGameLaptop systemd[1]: Found dependency on shorewall.service/start
Jun 16 10:13:21 LeosGameLaptop systemd[1]: Found dependency on network-online.target/start

---

### Post by lister171254 on 2015-10-26
Have just upgraded to 15.10 and the problem remains. I have a number of servers and they all have the same issue.

Maybe I'm the only person using shorewall, but given that the firewall doesn't start at boot for 2 releases is more than an annoyance as it depends on me to remember to manuall start shorewall.

Appreciate any pointers on what causes this issue.

Thanks

---

### Post by BCSharp on 2015-12-23
I have exactly the same problem. Also in my case, upgrade to 15.10 did not help. Searching the Internet for workarounds did not help either (except that this thread and a [Debian bug report]("http://permalink.gmane.org/gmane.linux.debian.devel.bugs.general/1226303") showed up). So I came up with my own workaround.

Shorewall does not come with a systemd native service unit description. Such description is being generated at boot by /lib/systemd/system-generators/systemd-sysv-generator based on /etc/init.d/shorewall. I have noticed, however, that the LSB header of /etc/init.d/shorewall wants the service to be started from /etc/rcS.d, which is pretty early, and at the same time it has Required-Start: $network $remote_fs, which is a pretty strong requirement. In fact, this is the only script in /etc/rcS.d that requires $network (well, except shorewall6, which exhibits exactly the same problem). Looking into the auto-generated unit in /run/systemd/generator.late/shorewall.service shows:

[FONT=Consolas]DefaultDependencies=no
[/FONT][FONT=Consolas]Before=sysinit.target shutdown.target[/FONT]
  [FONT=Consolas]After=network-online.target remote-fs.target[/FONT]
  [FONT=Consolas]Wants=network-online.target[/FONT]
  [FONT=Consolas]Conflicts=shutdown.target
[/FONT]
This looks problematic: sysinit.target is a very early target, most higher level services are started after it, and on many systems (including mine) various dependencies will make network-online.target available only after sysinit.target. So in the end, I wrote my own shorewall.service definition and put it in /etc/systemd/system to override the auto-generated one:

[FONT=Consolas][Unit]
[/FONT][FONT=Consolas]Documentation=man:shorewall[/FONT]
  [FONT=Consolas]Description=Configure the IPv4 firewall at boot time
[/FONT][FONT=Consolas]DefaultDependencies=no[/FONT]
  [FONT=Consolas]After=local-fs.target systemd-sysctl.service[/FONT]
  [FONT=Consolas]Before=network-pre.target shutdown.target[/FONT]
  [FONT=Consolas]Wants=network-pre.target[/FONT]
  [FONT=Consolas]Conflicts=shutdown.target[/FONT]
  
  [FONT=Consolas][Service][/FONT]
  [FONT=Consolas]Type=oneshot[/FONT]
  [FONT=Consolas]RemainAfterExit=yes[/FONT]
  [FONT=Consolas]TimeoutSec=30
[/FONT][FONT=Consolas]Restart=no[/FONT]
  [FONT=Consolas]IgnoreSIGPIPE=no[/FONT]
  [FONT=Consolas]KillMode=none[/FONT]
  [FONT=Consolas]ExecStart=/etc/init.d/shorewall start[/FONT]
  [FONT=Consolas]ExecStop=/etc/init.d/shorewall stop[/FONT]
  [FONT=Consolas]ExecReload=/etc/init.d/shorewall restart[/FONT]
  
  [FONT=Consolas][Install][/FONT]
  [FONT=Consolas]WantedBy=network.target
[/FONT]
After that, the service is installed by:

[FONT=Consolas]$ sudo systemctl enable shorewall.service
[/FONT]
This works for me, but I had very specific requirement: for security reasons, I wanted my firewall be up before any network interfaces are up. That means that no remote filesystems will be mounted yet when shorewall start runs and all shorewall config files have to be on a local filesystem. Additionally, /etc/default/shorewall does not define any wait_interfaces.

---

### Post by lister171254 on 2015-12-25
Have already logged this as a bug [https://bugs.launchpad.net/ubuntu/+source/shorewall/+bug/1511869](https://bugs.launchpad.net/ubuntu/+source/shorewall/+bug/1511869) , but have so far not had any luck with a resolution.

Suggest you indicate that you are affected by this bug too.

I've added your workaround to the bug too.

Thanks,

Leo

---

