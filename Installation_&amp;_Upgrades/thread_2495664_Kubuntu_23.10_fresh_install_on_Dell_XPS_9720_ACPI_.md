---
title: "Kubuntu 23.10 fresh install on Dell XPS 9720 ACPI Error on boot"
date: 2024-02-26
forum: Installation &amp; Upgrades
---

### Post by ValentynPrumers on 2024-02-26
The laptop boots and operates fine. But every time I do a reboot, just before the login window i receive 2 error messages:

```
ucsi_acpi usbc000:00: unknown error 0
```

followed by:

```
ucsi_acpi USBC000:00 UCSI_GET_PDOS failed (-5)
```

Any help how to resolve this?

ps. If i remove all usbc devices (including the usbc charger) I do not receive this error message. But if i start the laptop with a usbc-hdmi connector or usbc mouse i do get the error message.

---

### Post by Rubi1200 on 2024-02-29
Could be a number of reasons why you see those error messages.

If it was me, as long as you can boot normally (including removing the devices before boot) I would not be so concerned.

However, you could try adding some parameter to GRUB config if you like.

I would start with either ```
acpi=off
``` or perhaps ```
pci=noacpi
```

See if that works to remove the error messages with devices attached.

---

### Post by ValentynPrumers on 2024-03-13
Its a laptop. So i dont think its a good idea to disable acpi. Thanks though :)

---

