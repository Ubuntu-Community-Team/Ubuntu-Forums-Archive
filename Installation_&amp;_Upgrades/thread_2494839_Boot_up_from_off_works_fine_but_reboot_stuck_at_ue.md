---
title: "Boot up from off works fine but reboot stuck at uefi menu"
date: 2024-01-28
forum: Installation &amp; Upgrades
---

### Post by wvotta on 2024-01-28
I can power off just fine and boot up just fine but choosing restart gives me this unusable boot menu of uefi choices, presently only the one ubuntu entry, and it doesn't work like it doesn't even try. When I hold F12 to boot to a menu and manually choose ubuntu it works fine.
Should I run boot repair? Here's my pastebin: [https://paste.ubuntu.com/p/MyH8yJp5v4/](https://paste.ubuntu.com/p/MyH8yJp5v4/)

---

### Post by MAFoElffen on 2024-01-28
What is the hardware?

Please go here and join in as "I am also affected" link in Upper top-left: [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.2/+bug/2032136)

I have the same problem. I cannot reboot. I can only shutdown cold. And boot from cold.

If I try to reboot, it goes to the UEFI Boot Menu...

If you join in that bug, then the status will change to confirmed, and they might start looking for an answer to this (hopefully)!

---

### Post by wvotta on 2024-01-28
It's an old Lenovo 81VS with an AMD A6 processor. This isn't a unique problem to Ubuntu, this first happened to me with the Brunch framework when I was trying to get Chrome OS with Android app support working. It too couldn't reboot tho the originally installed Chrome OS Flex worked fine with reboots!

---

### Post by MAFoElffen on 2024-01-29
Hmmm. Mine is an old Lenovo T520 with Intel i7... Mine was fine until an update about a years ago. I can say, it is just with Windows.

Everything looks fine on mine in journal and the syslogs... So I don;t think there will be any clues on yours there.

I hear that some who have this problem, that a BIOS update might fix it. That won't happen for mine, becaseu it came out in 22011 and already has the most recent update...

But your cam out after 2019 right? Is the BIOS up to date?

---

### Post by wvotta on 2024-03-02
I do already have the latest bios update :(
It's gotta be something with UFEI

---

### Post by oldfred on 2024-03-02
Not sure if this still applies?
[https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot](https://askubuntu.com/questions/1178883/ubuntu-18-04-requires-multiple-attempts-to-boot)

Lenovo laptops containing Optimus graphics W520/T520/T530 nox2apic boot parameter
[https://gist.github.com/wbond/3800562](https://gist.github.com/wbond/3800562)

---

### Post by MAFoElffen on 2024-03-05
Mine is one of those (T520) and mine has Optimus graphics... I have 'nox2apic' as a boot parameter as a boot parameter, and it does not help with mine.

Maybe it might help with others though.

---

