---
title: "Upgrading to Ubuntu 16.04 Stalled"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by cobalt2 on 2016-06-08
While upgrading to Ubuntu 16.04, the program informed me that it wants to edit the grub configuration file and asked what I want to do with it. I selected review the changes. After reviewing the changes, I went back to the menu and selected launch a new shell to examine the changes. Then debconf was not responding so I killed the process. Now the installation has stalled. What do I do next? How do I get the installation to resume?

---

### Post by cobalt2 on 2016-06-08
I was able to to continue the installation by exiting sudo. I received this error:

```
Could not install 'grub-efi-ia32'

The upgrade will continue but the 'grub-efi-ia32' package may not be in a working state. Please consider submitting a bug report about it.
```

Then the installer asked me again if I want to allow the grub configuration file to be edited. I selected keep the existing grub configuration file.

The installation continues. Then I receive this error at the end of installation:

```
Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).
```

Is it safe for me to restart the computer? Is there anything that needs to be done to fix this upgrade?

---

### Post by cobalt2 on 2016-06-08
I restarted and now everything is working okay.

---

