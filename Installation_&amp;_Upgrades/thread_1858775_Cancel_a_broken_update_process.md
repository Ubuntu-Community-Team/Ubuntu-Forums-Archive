---
title: "Cancel a broken update process"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by kalasend on 2011-10-13
Hi,

When i was in the middle of a "sudo apt-get install XXX" process, i needed to Ctrl-C the process and reboot. Now, I decided that I don't need to install the package after all. But apt-get seem to remember the broken process.

How do I revert apt-get to the state before? (if it's possible at all...)


Thanks in advance

---

### Post by WasMeHere on 2011-10-13
Welcome to the Ubuntu Forums!

Try the following commands.
```
sudo apt-get update
sudo apt-get upgrade

[s]sudo apt-get install XXX    # install (is reverted by remove)[/s]
sudo apt-get remove XXX     # remove
sudo apt-get purge XXX      # remove (any configuration files are deleted too)

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

Read also ```
man apt-get
``` to get more details about *apt-get*

Have fun learning about Ubuntu :-)
Olle

---

### Post by raja.genupula on 2011-10-13
> **kalasend said:**
> Hi,

When i was in the middle of a "sudo apt-get install XXX" process, i needed to Ctrl-C the process and reboot. Now, I decided that I don't need to install the package after all. But apt-get seem to remember the broken process.

How do I revert apt-get to the state before? (if it's possible at all...)


Thanks in advance

If you are installing something unless you're touching it again ,apt-get doesn't alert you if you cancel the installation.

The commands given in post 2 also works but for installation cancellation apt-get will not go fo own decision with out your interaction.

Enjoy the Ubuntu.

---

