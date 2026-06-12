---
title: "No Unity, no errors, after upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by acambre on 2011-04-29
I just upgraded from 10.10 64-bit to 11.04. The desktop looks the same as it did in 10.10, and I get no errors about anything.

Because everything looks and works the same, I assume Unity is not active. How do I turn it on?

---

### Post by KegHead on 2011-04-29
Hi!

system..admin..login..chose default.

Restart.

KegHead

---

### Post by acambre on 2011-04-29
> **KegHead said:**
> Hi!

system..admin..login..chose default.

Restart.Thanks, but there's no selection for Unity. Here's what I see in **Select ... as default session**:
[LIST]
[*]User Defined Session
[*]Ubuntu (Safe Mode)
[*]Ubuntu Classic (No effects)
[*]Recovery Console
[*]Ubuntu Classic
[*]Ubuntu **[this one was selected already]**
[/LIST]

---

### Post by 2uRcJQ34G1 on 2011-04-29
There might also be a possibility that your graphics card is not supported and it defaulted to the gnome version of Ubuntu 11.04.

---

### Post by acambre on 2011-04-29
> **gore_grinder said:**
> There might also be a possibility that your graphics card is not supported and it defaulted to the gnome version of Ubuntu 11.04.Thanks. So to confirm, I should see an entry for Unity in there if Unity is supported?

---

### Post by TBABill on 2011-04-29
Nope. It just says Ubuntu so if your card is not supported or driver not installed, it defaults to classic.

---

### Post by acambre on 2011-04-29
> **TBABill said:**
> Nope. It just says Ubuntu so if your card is not supported or driver not installed, it defaults to classic.Looks like it was hardware. This is a VM guest in Oracle VirtualBox. Checking the boxes in VirtualBox to enable 3D hardware acceleration fixed it.

I definitely see Unity now after rebooting!

---

### Post by KegHead on 2011-04-29
Hi!

It looks like it's not supported.

KegHead

---

