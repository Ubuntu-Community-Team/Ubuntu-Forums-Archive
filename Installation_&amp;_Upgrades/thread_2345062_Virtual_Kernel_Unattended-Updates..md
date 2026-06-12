---
title: "Virtual Kernel Unattended-Updates."
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by mcparty2 on 2016-11-30
Hi Folks,

I have a few servers using 12.04 LTS and have noticed one is using a Virtual Kernel which never seems to get any patches pushed its way from Unattended-Upgrades. I only allow security upgrades to my servers unattended however, on other servers I am prompted for a reboot after a new kernel update is provided I have a couple of servers which are on 3.2.0-113 and I want them all to be the same.

```

uname -r 
3.2.0-102-virtual

```

I have checked Unattended-Upgrades logs which show it's working, though the Kernel updates from the 11th November didn't come through.

My questions really are:

1, Is there a procedure to change the virtual kernel back to the standard server kernel?
2, Does the virtual kernel not need security patches - I know they are lightweight does this mean they are immune to a lot of the updates?


Thanks

---

### Post by mcparty2 on 2017-10-17
I never got an answer on this and 12.04LTS is now out of support by Canonical.
As such I shall close as it is no longer relevant for me.

---

### Post by oldos2er on 2017-10-17
Since no solution has been found or posted,  I'm removing the solved tag and closing the thread.

---

