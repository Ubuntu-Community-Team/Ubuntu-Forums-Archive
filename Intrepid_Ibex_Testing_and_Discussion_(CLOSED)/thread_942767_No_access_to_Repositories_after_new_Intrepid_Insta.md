---
title: "No access to Repositories after new Intrepid Install"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sipickles on 2008-10-09
Hi,

I've just installed Intrepid Server Beta.

Installation was smooth apart from one problem:

I cannot install any packages. If I do 'sudo apt-get install gnome-core' for instance (or any other package) I get an error:

"Couldn't find package"

My entries in /etc/apt/sources.list look fine. I can ping ubuntu.com. I have set a static IP address, and restarted networking.

Any ideas?

Thanks

Simon

---

### Post by cariboo on 2008-10-09
Can you run:

```
sudo apt-get update
```

Jim

---

### Post by sipickles on 2008-10-10
How embarrassing....

Thanks Jim for unblocking my mental block.

---

