---
title: "Gutsy alternate install fails: &quot;Kernel panic - not syncing: IO-APIC&quot;"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mattengland on 2007-10-18
On an x86 box ( a Powerspec 7121: [http://www.powerspec.com/systems/system_specs.phtml?selection=7121](http://www.powerspec.com/systems/system_specs.phtml?selection=7121) ) I see the following hang error when booting from gutsy alternate cdrom:

```

[ 45.781270] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 46.024508] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option

```

How might I work around this problem?  I try the alternate cdrom because 7.04 installs on this box fail unless I use the 7.04 alternate cdrom.

More details here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/54621/comments/41](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/54621/comments/41)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/54621/comments/42](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/54621/comments/42)

I see this similar thread:

[http://ubuntuforums.org/showthread.php?t=509499](http://ubuntuforums.org/showthread.php?t=509499)

...but the suggestions there seem to be on the lines of changing boot parameters...which I can't do because the cdrom is burned, unless I go change the filesystem myself and re-burn the cdrom (not a trivial task).

---

### Post by Whiffle on 2007-10-18
There should be an option to change boot parameters when you boot the cdrom.  Just add 'noapic' in there and it should work.  If it doesn't offer that option with the desktop cd try the alternate one.

---

### Post by banewman on 2007-10-18
At the "start or install" screen press F6 - that lets you set boot parameters. Add at the end of the line -  noapic nolapic  -  .  :)

---

