---
title: "HELP: Cant connect to the INTERNET/LAN in Ubuntu"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by lordnikotine on 2005-10-09
i am on the internet using a router, when i installed Ubuntu, it doesnt connect to the internet although my windows PC is still connected. Im on DSL (Router). The network could be detected either... (ethernet [eth0] connection is active.)

could someone give me a step-by-step instructions... im a super newbie:( .... please help. thanks in advance!:cool:

---

### Post by tehwa on 2005-10-09
Hi lordnikotine,

Post the output of this commands:

```
ifconfig
sudo ifdown eth0
sudo ifup eth0

```

This output is gold.

---

