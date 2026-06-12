---
title: "Stuck in login loop after upgrading to 18.04"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by benjamincomley on 2018-05-13
Hi,

Firstly a little about my setup as I believe it may be key to the issue.

I am running a Dell XPS 13 9360. Almost always it is connected to an eGPU via the Firewire port. The eGPU houses an NVIDIA GTX1080.

Initially I was running 17.10 with no problems. I upgraded to 18.04 via the prompt last week (while plugged in to the eGPU) and everything went fine.

But since then I have discovered that when unplugged from the eGPU, I am stuck in a login loop.

I enter my password and press login, it looks as though it's about to load, the screen goes black, then I'm back to the login prompt.

Any thoughts?

---

### Post by dino99 on 2018-05-13
When the eGPU is unplugged, which gpu driver is used ?
With a black screen, swith to a tty console (ctrl+alt+F2) and run 'startx', then check 'journalctl -b' to know about warnings/errors

---

### Post by benjamincomley on 2018-05-13
Thanks for the reply.

When running `startx` I get ```
xauth: file /home/benji/.Xauthority does not exist
```

Following that I entered `journalctl -b` and looked through the log. There were multiple errors, mainly to do with `systemd` and `ACPI`.

---

