---
title: "vt596_smbus error SMB not enabled in BIOS force=1"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2010-09-19
Hello all.

I have searched for an explicit solution to this problem on Google and on this forum, but so far I haven't hit pay dirt.  'Had a problem like this myself before, but decided to ignore it with little effect.  'Problem is that now that Ubuntu has made booting normally so fast, any hang up like this is a drag.

Here's the line from dmesg that shows up on a flitzerzy green screen briefly before the Ubuntu startup boot splash takes its place.

```
vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
```

Now I know from past experience and from the information I've found on Googling that updating the BIOS has no effect, so I'd like to try the second option, but I'm not sure how.

I thought I'd be smart and I edited the etc/modules file adding the following line.
```
vt596_smbus force=1
```

However, that did absolutely nothing.

Hmm.

lspci -v showed this:
```
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
    Subsystem: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
    Flags: medium devsel, IRQ 10
    Capabilities: [68] Power Management version 2
    Kernel driver in use: vt596_smbus
    Kernel modules: via686a, i2c-viapro
```

I also found this information, which seems to suggests that force=1 could do more harm than good.

[http://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-piix4]("http://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-piix4")

However, that's for Pentiums and I'm running with an AMD Duron processor.  Perhaps I just need to ask the kernel not to bother loading the module?

Please help me to solve this problem so that I can wow the new user with how fast the system boots.

---

