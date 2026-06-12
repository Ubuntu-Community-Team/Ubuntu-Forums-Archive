---
title: "[one solution] Xubuntu doesn't access desktop after login - for iptables user"
date: 2022-10-02
forum: Installation &amp; Upgrades
---

### Post by just24me on 2022-10-02
Hi community,

after using X/Ubuntu for many years right now and regularly checking up these forums for any help, I have come to the point where I want to add some information myself.


[B]Initial problem:
Access to desktop blocked for a long time after login credentials - regarding Upgrade to 22.04.[/B]

Story behind:
After upgrading from 20.04 to 22.04 I couldn't reach the desktop environment after typing in the login password.
Sometimes I could reach the desktop by waiting for a long time (round about 3 to 5 minutes or longer), but the screen resolution was completely wrong and my second monitor wasn't activated.
Because I haven't found a good solution for the problem I did a fresh install.

Today the same problem appeared after [B]I have set up iptables rules. More exactly ip6tables rules.

[/B]In Xubuntu 20.04 I have had all my ipv**6**-traffic blocked via ip**6**tables (INPUT DROP, FORWARD DROP, OUTPUT DROP, no rule else - worked like a charm), which I was about to set up today as well. After saving the ip6tables rules permanently and rebooting the system, exactly the same problem reappeared.
After then setting all the ip6tables rules to ALLOW again, the problem was gone.
So I tried to find out....



[B]Solution in this case:
ip6tables rules must allow ipv6 localhost traffic[/B]

Story behind:
It seems that ipv6 localhost communication has to be accepted. I have set up a new pair of rules with DROP policies to input, forward and output and added the acceptance of localhost traffic with localhost
```
INPUT -i lo -j ACCEPT
``` and ```
OUTPUT -o lo -j ACCEPT
```. 
The problem is gone.
[SIZE=1]Note: this is not a manual for setting up a correct firewall.[/SIZE]


When I upgraded Xubuntu 20.04 to 22.04 in those days, I have had my ip6tables rules from 20.04 (everything on DROP, nothing else) going. Apparently the problem has been the same, but it hasn't been obvious.
I haven't found out why 22.04 needs ipv6 localhost traffic to enter the desktop environment and 20.04 doesn't.


Just for those of you using iptables, try to check out, if this solves your problem.


I hope, I could be of help for some of you.

Have a nice weekend.

---

### Post by The Cog on 2022-10-02
I'm guessing it's DNS resolution - 22.04 uses a systemd-operated DNS server. Look at /etc/resolv.conf and see it it's pointing to an address on the loopback interface. It's only a guess though.

It really does help if you let the applications in the box talk to each other. If you leave this command running, you may see what is using IPv6 locally (leave it running, Ctrl-C to finish).  Or you could add a log directive to the firewall rules.
```
sudo tcpdump -nntl -i lo ip6
```

Well done tracking it down this far, and for warning others. I suspect that others will have also blithely blocked all IPv6 and not understood what's wrong.

---

