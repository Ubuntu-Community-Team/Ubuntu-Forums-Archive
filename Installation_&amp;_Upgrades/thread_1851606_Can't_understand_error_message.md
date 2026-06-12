---
title: "Can't understand error message"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2011-09-28
I use Ubuntu 10.04.

I tried to install libssl-dev, but got the error message attached.

Can someone please tell me what to do so that I can install libssl-dev? I'm not very knowledgeable about these things and don't know what to try next.

Thanks,

Leslie

---

### Post by oldos2er on 2011-09-28
Do you have any Debian repositories enabled? If so, disable them then try installing libssl-dev again.

---

### Post by dino99 on 2011-09-28
both release dont match, you need a newer package 0.9.8o to be able to install. Is your system updated ? is 0.9.8k installed ? (see into synaptic)

---

### Post by lesliek on 2011-09-28
@oldos2er: I did have Debian 6.0 Squeeze selected under Other Software in Software Sources so that I could install an updated version of Grisbi, a personal finance application. However, after installing Grisbi, I unselected Debian. Did I install the Debian version of libssl as part of installing Grisbi perhaps? If so, can I reverse the situation? I'd much rather have my printer working wirelessly than have Grisbi.

@dino99: I think I've answered your question in my answer to oldos2er. I seem to have the Debian version of libssl installed and that seems to be the cause of my problem.

---

### Post by lesliek on 2011-09-29
I've solved my problem, thanks to oldos2er's alerting me to the fact that the version of libssl I had installed was a Debian one.

I forced the reinstallation of the Ubuntu version of libssl using Synaptic, after which libssl-dev installed as requested. That in turn allowed my printer to begin to work wirelessly.

Thanks again to oldos2er and to dino99.

---

### Post by oldos2er on 2011-09-29
Glad you got it sorted out. Could you please mark the thread as 'Solved' (under Thread Tools). Thanks!

---

