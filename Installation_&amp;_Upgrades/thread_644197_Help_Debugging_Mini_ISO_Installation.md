---
title: "Help Debugging Mini ISO Installation"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Torginator on 2007-12-18
I'm going to try this again with what I hope is a better title.

I'm trying to install Ubuntu from a Mini ISO image onto an old laptop. For various reasons, I don't want DSL or anything else but a command-line (or server) basic Ubuntu installation. I can get the installation to start (alas, using LINLD from FreeDOS), but it crashes immediately with much debug information that scrolls by and is lost.

Is there a boot parameter I can pass so I can capture that output somehow, say via serial port or saved to a file?

Many thanks.

---

### Post by Torginator on 2007-12-31
For anyone else with a similar problem: My system will boot the installer for Dapper or Edgy, but not Feisty or Gutsy. And as for the command line: Add "console=ttyS0,9600" to your kernel parameters to capture the debug output via the serial port. 9600 baud works with nearly all the old computers without flow control.

---

