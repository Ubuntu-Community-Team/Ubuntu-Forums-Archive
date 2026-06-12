---
title: "Acer Aspire E1 doesn't turn power off on shutdown"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by morphus2 on 2013-10-24
Hi there,

after I was able to install Ubuntu 13.10 on my new Acer Aspire E1-422-3444 (took 10 hours) I have now a small but annoying problem:
The system does not turn off on shutdown.

I know there are a lot of threads discussing the problem, I tried everything.
- Forcing ACPI in Grub 2 did not work
- Forcing APM in Grub 2 and modules did not work
- I tried a kernel update to latest version, did not help. Instead I am not able to view the shells (Ctrl+Alt+F1...) anymore, so I cant tell
for sure about the errors while shuttimng down.
What happened before the update:

* System will halt now ....

and nothing. Everything frozen, I assume that the problem is the same after the update (even if I dont see the command line).

- I tried all combinations of sudo shutdown -hP now etc (shutdown, poweroff, halt).

Interesting: I cant even get the system turning off in grub shell with the command halt.

Does anyone have an idea what might be wrong? In the BIOS there are no powersettings...
I had to switch to legacy mode to get ubuntu installed, which means that I"m not able to run the preinstalled Windows 8 (who cares...).

I think I was able to shut the computer down with ubuntu 13.04, but I cant tell for sure (maybe I just did not realize that I was not able to do this).

rebooting works like a charm...

Hope you can help me!
Best regards
Morphus

EDIT: I tried shutdown with Trial Ubuntu 13.04 on USB Stick. The Output is *will now halt and nothing happens.

---

