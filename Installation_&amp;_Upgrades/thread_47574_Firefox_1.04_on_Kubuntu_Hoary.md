---
title: "Firefox 1.04 on Kubuntu Hoary"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by mhbengal on 2005-07-09
I am trying to upgrade my Firefox browser to 1.04 using the new repos available on the Ubuntu site. I have run apt-get update and trying to ugrade using "aptitude", apt-get upgrade and Kynaptic.

However it keeps giving a message that "libcairol 0.3.0-1" is not authenticated.

How do i upgrade the firefox?

---

### Post by emmet on 2005-07-09
This just means that you haven't put in the pgp keys of the original packager of the package you are trying to install (in this case some cairo library).

It happens to me a lot, but if you are confident of your source, they you can just allow Synaptic or whatever you are using, to install the package. The rest will then continue.

Hope this helps,

Emmet

---

