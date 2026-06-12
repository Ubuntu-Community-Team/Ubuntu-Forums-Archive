---
title: "Ubuntu 12.04 ufw vs iptables?"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by matthys on 2012-07-01
Hello everyone,

After many years of using Gentoo I made the decision to move to Ubuntu Server.

However I have a question what to use as firewall. The documentation said it moved from iptables to the more easier configurable ufw. On my Gentoo machine I used iptables, which automatic load and saves the iptables. I know that with some modifications you can do this in Ubuntu as well. The major question I have is; does ufw do the same, keep iptables as it is? I asked this as I create a customized block chain which I want to keep, **also after reboot etc**.

Also, should I stay stick to iptables or move to ufw? As documentations seems to be focus on ufw...

Thanks,
Matthijs

---

### Post by darkod on 2012-07-01
I would say stick with iptables especially since you are already familiar with it.

I recently needed to do a firewall project, and being total beginner in both iptables and ufw I did it with ufw as it looked (and sounded) easier. Only towards the end I realized the iptables would have been much better and works more efficiently.

You would probably load them using /etc/network/interfaces and something like:
pre-up iptables-restore < /path/iptables-file

PS. One example:
[http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server](http://www.linode.com/wiki/index.php/Configuring_IPtables_on_ubuntu_server)

---

### Post by Blackbird_13 on 2012-07-01
I use, and have not had any problems with, iptables-persistent which is referenced on
[https://help.ubuntu.com/community/IptablesHowTo#Solution_.233_iptables-persistent](https://help.ubuntu.com/community/IptablesHowTo#Solution_.233_iptables-persistent)

---

### Post by darkod on 2012-07-01
> **Blackbird_13 said:**
> I use, and have not had any problems with, iptables-persistent which is referenced on
[https://help.ubuntu.com/community/IptablesHowTo#Solution_.233_iptables-persistent](https://help.ubuntu.com/community/IptablesHowTo#Solution_.233_iptables-persistent)

If I am not mistaken NetworkManager comes included in the desktop version but not the server. That page looks like having the desktop version in mind. Especially since after the iptables-persistent it continues with GUFW and the servers don't have any GUI by default.

EDIT PS: My mistake, juts looked more carefully now. iptables-persistent is mentioned just before the NetworkManager title. I saw the title first. :)

---

### Post by matthys on 2012-07-01
Thanks ... I will stick to iptables, seems to be more flexible as ufw anyway.

I just added these pre-up & down rules to /etc/network/interfaces and works great:

# The external network interface (INTERNET)
auto eth1
iface eth1 inet dhcp
    # The line "post-down iptables-save > /etc/iptables.rules"
    # will save the rules to be used on the next boot.
[B]    pre-up iptables-restore < /etc/iptables.rules
    post-down iptables-save > /etc/iptables.rules[/B]

Of course also enable the net.ip4.ip_forward=1 in /etc/sysctl.conf

Thanks,
Matthijs

---

### Post by darkod on 2012-07-01
You don't even need to do the post-down iptables-save especially if sometimes testing new rules. If you mess up, a reboot will revert to the rules without the change.

And when you want to apply some change you can edit /etc/iptables.rules directly.

---

### Post by matthys on 2012-07-01
I DO need the post-down as on it way some chains are filled, and I want to keep them as they are.

I created a firewall.sh script to fill the iptables the first time (or if I need to empty iptables and fall back to basic one).

---

### Post by nuxnix on 2012-07-06
This is a great method. It means I can document my iptables in a single nicely commented script for a group of servers, modify the script in one place and run it once, per server and it remains persistent after that. Provided any changes are made to the script its very maintainable. Thanks for the ideas.

---

