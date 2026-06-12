---
title: "Installed Lubuntu 24.04 - lost grub menu"
date: 2024-05-21
forum: Installation &amp; Upgrades
---

### Post by gdenton61 on 2024-05-21
Hello,
I just installed Lubuntu 24.04 over Lubuntu 22.04 on a dual-boot legacy BIOS machine, I no longer have a grub menu on boot, boots straight into Lubuntu, can anyone please look at this boot-repair info before I screw things up?

[https://paste.ubuntu.com/p/TwQKss9N5y/](https://paste.ubuntu.com/p/TwQKss9N5y/)

Thanks for any help.

---

### Post by gdenton61 on 2024-05-21
Please disregard, wxl on the Lubuntu Discourse gave me the fix:

[COLOR=#203243][FONT=Arial]You can edit /etc/default/grub like so:[/FONT][/COLOR]

# GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5

[COLOR=#203243][FONT=Arial]Then run [/FONT][/COLOR]sudo update-grub[COLOR=#203243][FONT=Arial].[/FONT][/COLOR]

---

### Post by guiverc on 2024-05-21
As I added on the the Lubuntu discourse..  I suspect you ran into this issue

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624)

I suggest you see if that fits your type of install, as if it does, you can click *affects me too* and the bug may receive more attention, as currently I'm the only person who has encountered it (*during QA for 24.04 actually*). 

It impacts all 24.04 ISOs using `calmares` and `ubuntu-desktop-installer` so all Desktop *flavors*, but does require the re-use of a specific partition (*first installed GNU/Linux using grub*) on your system, so most installs will not be impacted by it.

This may not be your issue though, as your fix relates to timeout, where the fix for the issue of the bug I'm listing is changing a true/false flag in the same file.

---

