---
title: "distribution upgrade failure"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by Evil Wayz on 2007-12-28
i have one update available, that i never saw before, but it tells me i have to do a partial upgrade, however this upgrade fails and gives me the following message:

"could not calculate upgrade there was an unresolvable problem, please send bug report and append /var/log/disr-upgrade"

This is the contents of THAT file:
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5099 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5099 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5099 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5099 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on libc6
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

---

### Post by Partyboi2 on 2007-12-29
What happens if you try and fix the broken packages?

---

### Post by Evil Wayz on 2007-12-29
how do i do that?

---

### Post by Partyboi2 on 2007-12-29
Open up "Synaptic Package Manager" (System>Admin>Synaptic Package Manager) On the "edit" menu, click on "fix broken packages"

---

