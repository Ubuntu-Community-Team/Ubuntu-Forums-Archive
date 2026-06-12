---
title: "DNS problems since 12.04 upgrade"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by John Franklin on 2012-05-14
After upgrading to 12.04 DNS did not work and there were no nameserver entries in /etc/resolv.conf. I followed a post to use the resolvconf package to add nameservers and this now permits Internet access through Firefox. However, the Synaptic Package Manager still can't find its install files on the Internet. I've tried changing its Proxy Server settings but to no avail.

Are there other changes I need to make to allow DNS to work from any package?

---

### Post by darkod on 2012-05-14
I think some changes were done in 12.04. Don't use /etc/resolv.conf directly, I think it gets overwritten anyway.

Click the Network Manager icon and select Edit Connections. Select you wired or wireless connection.

Click Edit, then the IPv4 tab, and change the option from Automatic to Automatic (address only). Below, in the DNS field enter your nameservers that you want to use.

Check if that sorts it out. It's not beautiful, but it should work. :)

---

### Post by John Franklin on 2012-05-14
I've used the resolvconf utility, not edited the files directly (because I understand they are overwritten). That fixed Internet access for Firefox only.

There seem to be some odd things happening since the upgrade. If I go to Network Connections, as darkod suggests, there are no connections shown, even though I have a wired connection working quite happily through which I can reach other computers and the Internet (with Firefox). If I add a connection and then the nameservers as suggested, that still doesn't help the Package Manager to find the Internet.

If I go to System Settings -> Network, that recognises the wired connection but the Options button is disabled. (As an aside, why are there multiple ways to get to different network settings instead of having them all in one place?)

---

