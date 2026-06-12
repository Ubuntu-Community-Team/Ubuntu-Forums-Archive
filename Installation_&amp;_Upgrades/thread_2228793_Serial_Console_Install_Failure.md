---
title: "Serial Console Install Failure"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by tnteverett on 2014-06-09
I have been working on this for a few days now and can't seem to get past final kernel installation.  My current error message is "Unable to install busybox-initramfs An error was returned while trying to install the busybox-initramfs package onto the target system."
I have retried a number of times reformatting the drive in-between.  I have zero'd out the disk.  I still can't get past this last step.

Additional Log Info:
Jun  9 17:45:06 base-installer: info: Found kernels 'linux-signed-generic,linux-signed-generic-lts-quantal,linux-signed-generic-lts-quantal-eol-upgrade,linux-signed-generic-lts-raring,linux-signed-generic-lts-raring-eol-upgrade,linux-signed-generic-lts-saucy,linux-signed-generic-lts-saucy-eol-upgrade,linux-signed-generic-lts-trusty,linux-generic,linux-generic-lts-quantal,linux-generic-lts-quantal-eol-upgrade,linux-generic-lts-raring,linux-generic-lts-raring-eol-upgrade,linux-generic-lts-saucy,linux-gen
Jun  9 17:45:06 base-installer: info: preseeded/current kernel: linux-generic
Jun  9 17:45:37 base-installer: info: Using kernel 'linux-generic'
Jun  9 17:45:37 base-installer: warning: Failed to get debconf answer 'base-installer/kernel/linux/initrd'.
Jun  9 17:45:37 base-installer: info: Setting do_initrd='yes'.
Jun  9 17:45:37 base-installer: info: Setting link_in_boot='no'.
Jun  9 17:45:37 base-installer: apt-install or in-target is already running, so you cannot run either of
Jun  9 17:45:37 base-installer: them again until the other instance finishes. You may be able to use
Jun  9 17:45:37 base-installer: 'chroot /target ...' instead.
Jun  9 17:45:37 in-target: Unexpected error; command not executed: 'sh -c debconf-apt-progress --no-progress --logstderr --     apt-get -q -y --no-remove install busybox-initramfs'
Jun  9 17:45:37 base-installer: error: exiting on error base-installer/kernel/failed-package-install
Jun  9 17:45:42 main-menu[305]: WARNING **: Configuring 'bootstrap-base' failed with error code 30
Jun  9 17:45:42 main-menu[305]: WARNING **: Menu item 'bootstrap-base' failed.
Jun  9 17:45:43 main-menu[305]: INFO: Modifying debconf priority limit from 'medium' to 'low'
Jun  9 17:45:43 debconf: Setting debconf/priority to low
Jun  9 17:45:52 main-menu[305]: INFO: Menu item 'di-utils-shell' selected
/var/log # sh -c debconf-apt-progress --no-progress --logstderr --     apt-get -
q -y --no-remove install busybox-initramfs
--no-progress: line 1: debconf-apt-progress: not found

When I drop to a shell I can see this file.  When I try to test it in the shell I get errors that the file does not exist or that I library can't be found.  I assume these are due to the lack of a proper environment.  I also assume that the install would set this environment for me.

Another method:
Error Message:
"Unable to install the selected kernel An error was returned while trying to install the kernel into the target system. Kernel package: 'linux-generic'."

Log Info:
Jun  9 19:02:59 in-target: Building dependency tree...
Jun  9 19:02:59 in-target: 
Jun  9 19:02:59 in-target: The following extra packages will be installed:
Jun  9 19:02:59 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun  9 19:02:59 in-target: The following NEW packages will be installed:
Jun  9 19:02:59 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun  9 19:02:59 in-target:   linux-headers-generic
Jun  9 19:02:59 in-target: 0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Jun  9 19:02:59 in-target: Need to get 9,581 kB of archives.
Jun  9 19:02:59 in-target: After this operation, 76.5 MB of additional disk space will be used.
Jun  9 19:02:59 in-target: WARNING: The following packages cannot be authenticated!
Jun  9 19:02:59 in-target:   linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
Jun  9 19:02:59 in-target:   linux-headers-generic
Jun  9 19:02:59 in-target: E: There are problems and -y was used without --force-yes
Jun  9 19:02:59 base-installer: error: exiting on error base-installer/kernel/failed-install
Jun  9 19:11:19 main-menu[308]: WARNING **: Configuring 'bootstrap-base' failed with error code 1
Jun  9 19:11:19 main-menu[308]: WARNING **: Menu item 'bootstrap-base' failed.
Jun  9 19:11:20 main-menu[308]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Jun  9 19:11:20 debconf: Setting debconf/priority to medium
Jun  9 19:11:26 main-menu[308]: INFO: Menu item 'di-utils-shell' selected

 How do I get this resolved???

---

### Post by tnteverett on 2014-06-10
What other information can I post here in order for anyone to understand what the issue is?
Some background.
Target Hardware Platform:
Dual Quad Core Xeon
24GB Memory
Dual 300GB Hard Disk
ATCA Blade (no keyboard, no mouse, no monitor)
Network Connection
Serial Console Connection
USB
PXE Boots to Bare Bones Custom Linux (need to upgrade to Ubuntu Server Linux)

---

### Post by steeldriver on 2014-06-10
> **tnteverett said:**
> What other information can I post here in order for anyone to understand what the issue is?

I think that there just aren't too many people on here who are familiar  with serial console - you will need to be patient and hope the right  people see your thread

---

### Post by tnteverett on 2014-06-11
I'm still looking for help on this issue if anyone has any ideas.

---

### Post by tnteverett on 2014-06-16
OK, so this is not a serial console failure.  I found some hardware that was compatible with my SAS disk that had a monitor and keyboard.  I get the exact same failure when the kernel is being installed.  I think I might try other versions of Ubuntu before I quit and pick some other Linux OS.

---

### Post by coffeecat on 2014-06-16
Closed. OP has started new thread here:

[http://ubuntuforums.org/showthread.php?t=2229953](http://ubuntuforums.org/showthread.php?t=2229953)

---

