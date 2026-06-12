---
title: "Express card hotplug broken in 12.04"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by sunbird on 2012-05-12
I just did a clean install of 12.04x64 on my machine, which had previously been running 10.04x64. After a few days of tinkering, most everything works, _except_ I can't get the expresscard 34 reader to work.

On 10.04, I simply added acpiphp to /etc/modules and it worked fine, including hotplug.

But on 12.04, I get this:

```

$ sudo modprobe acpiphp
FATAL: Error inserting acpiphp (/lib/modules/3.2.0-24-generic/kernel/drivers/pci/hotplug/acpiphp.ko): No such device

```

**Update**

I fixed this by rebooting the machine. Not sure why I couldn't load it into the active kernel, but works fine now. :)

---

### Post by sunbird on 2012-05-14
This is still buggy compared to 10.04.

In 10.04, after ensuring that the acpiphp module was loaded at boot, I could hotplug devices. I have both a Lexar Compact Flash cardreader and a Rosewill RC-605 eSata card. Both were hotpluggable on my machine on 10.04. Neither will hotplug now unless I have one of them plugged in at boot.

I'll see if there is a bug reported on this issue.

**Edit:** There [is now.]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/999462")

---

