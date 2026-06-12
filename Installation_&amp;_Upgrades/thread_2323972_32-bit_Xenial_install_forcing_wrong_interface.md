---
title: "32-bit Xenial install forcing wrong interface"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by swajime on 2016-05-09
The install is defaulting to "enp10s0", instead of the first interface device which is "enp3s0".  I can enter the following settings, but nowhere does it allow me to correct the interface name.  Choosing <No> to start over does not give me the opportunity to correct the interface name.

```

                  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; [?] Configuring d-i &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                  &#9474;                                          &#9474;
                  &#9474; Currently configured network parameters: &#9474;
                  &#9474;                                          &#9474;
                  &#9474;  interface     = enp10s0                 &#9474;
                  &#9474;  ipaddress     = 192.168.1.10            &#9474;
                  &#9474;  netmask       = 255.255.255.0           &#9474;
                  &#9474;  gateway       = 192.168.1.20            &#9474;
                  &#9474;  pointopoint   = <none>                  &#9474;
                  &#9474;  nameservers   = 192.168.1.20            &#9474;
                  &#9474;                                          &#9474;
                  &#9474; Is this information correct?             &#9474;
                  &#9474;                                          &#9474;
                  &#9474;     <Yes>                       <No>     &#9474;
                  &#9474;                                          &#9474;
                  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

This is in /var/log/syslog:
```
Jan  1 03:28:47 kernel: [   10.157931] igb 0000:0a:00.0 enp10s0: renamed from eth4
Jan  1 03:28:47 kernel: [   10.739409] igb 0000:04:00.0 enp4s0: renamed from eth1
Jan  1 03:28:47 kernel: [   10.791779] igb 0000:05:00.0 enp5s0: renamed from eth2
Jan  1 03:28:47 kernel: [   10.834681] igb 0000:09:00.0 enp9s0: renamed from eth3
Jan  1 03:28:47 kernel: [   10.871730] igb 0000:03:00.0 enp3s0: renamed from eth0

Jan  1 03:28:50 net/hw-detect.hotplug: Detected hotpluggable network interface enp4s0
Jan  1 03:28:50 net/hw-detect.hotplug: Detected hotpluggable network interface enp5s0
Jan  1 03:28:50 net/hw-detect.hotplug: Detected hotpluggable network interface enp10s0
Jan  1 03:28:50 net/hw-detect.hotplug: Detected hotpluggable network interface enp9s0
Jan  1 03:28:50 net/hw-detect.hotplug: Detected hotpluggable network interface enp3s0
...
Jan  1 03:38:59 frontend: Adding [ifchoices] -> [enp10s0: Intel Corporation I210 Gigabit Network Connection, enp3s0: Intel Corporation I210 Gigabit Network Connection, enp4s0: Intel Corporation I210 Gigabit Network Connection, enp5s0: Intel Corporation I210 Gigabit Network Connection, enp9s0: Intel Corporation I210 Gigabit Network Connection]
```

I've currently removed preseed.cfg and emptied kickstart.cfg as I'm trying to troubleshoot what is turning into a very difficult automatic installation.

In txt.cfg I have this:
```
label automatic
        menu label ^Automatic
        menu default
        kernel ubuntu-installer/i386/linux
        append tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=788 initrd=ubuntu-installer/i386/initrd.gz --- console=tty0 console=ttyS0,57600n8 ks=http://192.168.1.20/kickstart.cfg DEBCONF_DEBUG=5
```
How can I get past this?

Any help will be much appreciated,

Thanks,


John

---

