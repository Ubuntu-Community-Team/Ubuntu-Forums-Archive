---
title: "Ubuntu 20.04 Netinstall - bad default tty (black screen after boot installed system)"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by gchmurka on 2020-04-28
Hi, I found a problem in the new ubuntu 20.04 LTS installer via netinstall.

When  installing and selecting only the SSH server, the distribution installs  correctly, but after booting from the disk the default terminal is tty7  (thus only the black screen is shown).
Switching the ALT + F1 terminal to tty1 solves the problem and shows a normal login prompt.

When installing from a normal ISO image I did not encounter this problem.

It is a bit disturbing because it is not known what happens during startup and whether the server turned on correctly.

The difference I found is in the setting
/etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT

netinstall has:
GRUB_CMDLINE_LINUX_DEFAULT = "splash quiet"

system with normal iso:
GRUB_CMDLINE_LINUX_DEFAULT = "maybe-ubiquity"

After changing and rebuilding the grub config next boot normally loads login prompts.

---

