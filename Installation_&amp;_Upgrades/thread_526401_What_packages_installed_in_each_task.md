---
title: "What packages installed in each task?"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by dongthao on 2007-08-15
I want to change the default installed packages list in a installation mode of Ubuntu, such as "server". 
I found in Ubuntu, each "installation mode" such as "server", "ubuntu-desktop", ... is a *task* in *tasksel*. But I can't find where is the specification for each task, the installed packages, I mean.
For example, I found in the pxecfg file that indicate:[INDENT]LABEL server
kernel ubuntu-installer/i386/linux
append base-installer/kernel/linux/extra-packages-2.6= **[COLOR=Red]tasks=standard [/COLOR]**pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=normal initrd=ubuntu-installer/i386/initrd.gz --
[/INDENT]It means when we type "server" in the very first screen, the task is "standard". And according to the README file of tasksel source code package, I read the file "/usr/share/tasksel/ubuntu-tasks.desc" and saw this:
[INDENT]Task: standard
Section: user
Relevance: 8
Description: Standard system
 This task installs a reasonably small character-mode system.
Packages: **task-fields**
Test-new-install: install skip
[/INDENT]Task-fields, as in the README says:
[INDENT]In Debian, we mostly use the "task-fields" method, which is built into
tasksel, and l*ooks for Task fields* in the control data of available
packages, that list the name of the task. Another available method is
"standard", which just installs all standard priority packages, and another is "manual", which, as a special case, runs aptitude interactively to select what to install.
[/INDENT]I'm not really understand about this method, so I can't find which packages will be installed in this task. May anyone who know about this show me the way:(?

---

