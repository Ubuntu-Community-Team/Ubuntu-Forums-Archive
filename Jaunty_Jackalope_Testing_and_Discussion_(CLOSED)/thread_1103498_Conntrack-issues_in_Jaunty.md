---
title: "Conntrack-issues in Jaunty"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kristrev on 2009-03-22
Hello,

I am working on an xtables-extension that uses conntrack to check the state of the connection. After upgrading to Jaunty on one of my testmachines, I noticed that conntrack stopped functioning properly. Even though conntrackd is running and all required config-variables are set, conntrack -L outputs 0 flows and IPMARK tells me that the skb's ct is NULL. My questions is, has anyone noticed similar behaviour and/or knows how to solve this.

Conntrack worked perfectly when running Interprid on the same machine, that is why I suspect Jaunty has broken something. Please let me know if you need any more information.

-Kristian

---

