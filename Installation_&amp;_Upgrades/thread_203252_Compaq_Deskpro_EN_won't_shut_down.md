---
title: "Compaq Deskpro EN won't shut down"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by _Petya_ on 2006-06-24
Hi!

I have a Compaq Deskpro EN SFF box, and if i issue shutdown command, it goes down perfectly, "Power down.", or "Rebooting..." appears on the screen, but then nothing happens. Have you got any ideas? Maybe something with ACPI or APM? I've tried to adjust BIOS settings, unsuccessfully.

Peter

---

### Post by rcarring on 2006-06-24
ACPI would cause the machine to hang when shutting down. Make sure in the bios your APM is set to use "Other" and not "Win95".

Presume you issued

```

sudo shutdown now

```

I have found that some machines that should power off don't automatically so I just turn them off instead.

---

### Post by _Petya_ on 2006-06-25
[QUOTE=rcarring]ACPI would cause the machine to hang when shutting down. Make sure in the bios your APM is set to use "Other" and not "Win95".

Presume you issued

```

sudo shutdown now

```

I have found that some machines that should power off don't automatically so I just turn them off instead.[/QUOTE]

I've issued shutdown -r now and shutdown -r now. There is no BIOS setting in connection with APM or ACPI.

Petya

---

