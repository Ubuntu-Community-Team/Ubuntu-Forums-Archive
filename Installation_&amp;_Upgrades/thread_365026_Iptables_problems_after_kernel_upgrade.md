---
title: "Iptables problems after kernel upgrade"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by disk11 on 2007-02-19
Just so everyone knows, I have Ubuntu 6.06.

I upgraded to the 2.6.19.1 kernel following the **[Master Kernel Thread]("http://ubuntuforums.org/showpost.php?p=1835811&postcount=1")** in the Tips and Tutorials section and now packages that use/modify iptables do not work.  I tried compliing a newer version of iptables than the repos provide (1.3.7) but that didn't seem to work.  Firestarter gives me  the error "Your kernel doesn't support iptables.  Running via the console doesn't give any useful output.

  
fireflierd gives me:
```
matt@ubuntu:/$ sudo fireflierd
I/O warning : failed to load external entity "/var/lib/fireflier/usrules.xml"
Error loading userspace rules xml file(/var/lib/fireflier/usrules.xml)
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
Client IP: 16777343
Internal ip_queue error: Maybe you forgot to load ip_queue module ? (cf README)
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
FATAL: Module ip_tables not found.
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
abort: Failed to send netlink message: Connection refused
matt@ubuntu:/$ insmod
Usage: insmod filename [args]

```

I figure I'll have to recompile the kernel, what do I need to do different this time around to get iptables working properly?

---

### Post by BrowneR on 2007-02-21
when you configure you kernel (most likely using 'make xconfig') you need to make sure the relevant 'netfilter' modules are selected otherwise they wont be included in your kernel for iptables to use.

i have just compiled 2.6.20 and had to select options from:

networking--->networking options--->network packet filtering framework (netfilter)-->IP: netfilter configuration

when configuring using the 'make xconfig' tool. (see screenshot attached)

these options may be slightly different for the 2.6.19 kernel. you will most likely need to select options relating to 'iptables' and 'packet filtering' depending on what functionality you require. you can build these as modules (shown by a little dot in the checkbox next to the item) or indeed you can build them into the kernel directly (shown by a tick).

that is probably all you require for packet filtering (eg a firewall). i have other options selected as well as i sometimes use my pc as a router and so require nat facilities.

unfortunately i just deleted the kernel config file i used for 2.6.19 so i cant really provide any more details.

best of luck

---

### Post by disk11 on 2007-02-22
It looks like xconfig never showed up for me, so I'm probably missing several things.  I'll give this another shot sometime soon.

---

### Post by disk11 on 2007-02-25
I checked all the boxes in the netfilter section, and that was the only change I made in Xconfig, was able to compile the kernel, reinstalled the Nvidia drivers, but am still having networking issues.  Firestarter now works, I can get an IP address, ping 127.0.0.1, but pings fail to reach my router and anything beyond that.  Adding the router's IP address to the "Allow connections" box didn't help things either.  Did I mess something up again or do I need to change some iptables settings?

---

### Post by BrowneR on 2007-02-26
sorry i'm not really sure what to suggest, i'm not expert on the kernel.

seems strange that you can get an ip (by dhcp i presume?) but you cannot talk to the router :s

does stopping firestarter altogether make the problem go away? are there any entries in firestarters event log?

---

### Post by disk11 on 2007-02-26
It seems firestarter is at fault.  I turned the box back on after wasting an hour or so changing settings and using another NIC, and GAIM connected while I messed with the Firestarter needs admin access message.  I guess I'll try a newer Firestater version to see if I can avoid command line IPtables entries.  Thanks for your help.

---

