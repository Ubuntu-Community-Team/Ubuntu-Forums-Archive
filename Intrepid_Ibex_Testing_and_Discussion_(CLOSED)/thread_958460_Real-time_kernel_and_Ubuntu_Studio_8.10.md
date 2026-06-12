---
title: "Real-time kernel and Ubuntu Studio 8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by demios on 2008-10-25
According to the 8.10 release notes,

> No real-time kernel variant is available for the Linux 2.6.27 kernel included with Ubuntu 8.10. Users of UbuntuStudio 8.04 who need real-time kernel support are advised not to upgrade to UbuntuStudio 8.10.

Will this be remedied? Can I use an earlier rt kernel?

---

### Post by BwackNinja on 2008-10-25
I'm using the realtime kernel. uname -r returns "2.6.27-3-rt" which is not as updated as the regular kernel, but it boots and I have JACK running.

---

### Post by demios on 2008-10-25
> **BwackNinja said:**
> I'm using the realtime kernel. uname -r returns "2.6.27-3-rt" which is not as updated as the regular kernel, but it boots and I have JACK running.

how did you get it, did you have to compile it yourself?

---

### Post by BwackNinja on 2008-10-25
just a "sudo apt-get install linux-rt"

---

