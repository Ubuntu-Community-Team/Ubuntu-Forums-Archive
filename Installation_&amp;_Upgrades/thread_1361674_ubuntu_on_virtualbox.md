---
title: "ubuntu on virtualbox"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by gallaharsha on 2009-12-22
Hi, 

I have set up ubuntu on virtualbox at my office.
Can somebody help with the network configurations required.
I'm using NAT in virtual box settings. I'm not able to update anything.
But when I put proxy for firefox it works.

thanks in advance

---

### Post by starcraft.man on 2009-12-22
> **gallaharsha said:**
> Hi, 

I have set up ubuntu on virtualbox at my office.
Can somebody help with the network configurations required.
I'm using NAT in virtual box settings. I'm not able to update anything.
But when I put proxy for firefox it works.

thanks in advance

k, well clearly one solution would be to configure the proxy for your network connection. System > Preferences > Network Proxy.

Alternatively, vbox supports different modes for networking. NAT will interface your VM bypassing the host right to your network. Bridged mode will let it piggy back on whatever network your host uses. Host-only will only let you share files with it, limited use. Bridged likely would be another solution.

---

### Post by gallaharsha on 2009-12-23
I'm not able to ping any website even. How do I go about solving this.

---

### Post by gallaharsha on 2009-12-23
I'm able to browse internet from firefox by setting proxy settings but they do not work for updates etc.when I set them as network  proxy for system

---

