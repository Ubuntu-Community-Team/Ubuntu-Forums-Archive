---
title: "approx (apt-proxy replacement) in karmic"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lexxonnet on 2009-10-25
Hi There,

I've been upgrading my systems one by one to karmic and today got to a machine which acts as a repository proxy server for all the other machines.

I use approx as my repository proxy and it had been working really well in Jaunty. Since the upgrade however, I haven't been able to start approx as a service using either the upstart commands (sudo start approx) or the standard /etc/init.d/approx restart command. Turns out that approx just doesn't have an entry in /etc/init.d anymore.

Is this intentional, a bug or just something that's specific to my computer? Has anyone else encountered something similar?

---

