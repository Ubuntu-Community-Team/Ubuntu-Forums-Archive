---
title: "Canonical livepatch problem"
date: 2019-04-12
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2019-04-12
I have just bought a new laptop with Ubuntu 18.04 (Dell XPS 13) and got a problem with Livepatch, see attached screenshot.
It looks it is a problem with a particular kernel, so others should have the same problem...
Thanks for any help![ATTACH=CONFIG]283009[/ATTACH]

---

### Post by PaulW2U on 2019-04-12
The error message is drawing your attention to your **oem** kernel variant which is presumably what you get when you buy a Dell laptop with Ubuntu pre-installed.

Take a look at the [Livepatch]("https://wiki.ubuntu.com/Kernel/Livepatch") wiki page. Livepatch is only available for the GA (General availability) and low-latency variants of the kernel.

---

### Post by Gingalone on 2019-04-16
Thank you PaulW2U (and sorry for late reply)
Is it thinkable/convenient the install a kernel supported by Livepatch in my situation?

---

### Post by PaulW2U on 2019-04-16
> **Gingalone said:**
> Is it thinkable/convenient the install a kernel supported by Livepatch in my situation?
I don't know. You have an oem kernel for a reason. May be a question for Dell if no one here knows why they install an oem kernel by default.

Although I have Livepatch activated, and I occasionally see patches applied, I reboot most days as I dual boot with Fedora. Rebooting after a kernel update is not a problem for me.

Do you really **need** Livepatch on your laptop? Not all updates can be applied by Livepatch and reboots to update the kernel will still be necessary from time to time.

---

### Post by Gingalone on 2019-04-17
Thank you PaulW2U and no,  I don't really need Livepatch, my interest was just for a novelty which promises some convenience on updates...
I have been using Ubuntu for 20 years and to restart my PC/laptop after an update was really a small problem!

---

