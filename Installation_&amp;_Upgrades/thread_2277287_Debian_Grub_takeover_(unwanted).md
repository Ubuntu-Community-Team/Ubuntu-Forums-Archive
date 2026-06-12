---
title: "Debian Grub takeover (unwanted)"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by psfal on 2015-05-07
Hey all, got an issue with Grub. I've had Debian 7.+ on a partition of one of my laptops and use Ubuntu 14.04 alongside it. I just kept the Debian updated (hoping for a fix to an issue that never happened), it's latest upgrade brought it to 8.0 and took over the Grub that was run from Ubuntu til then.
 How do I get Grub back under control of Ubuntu so I can remove the Debian partition and still boot Ubuntu?
It's the machine my fiance uses so the less headaches from it the less I have to hear about... Any help is appreciated, please keep it relatively simple, I know enough about Linux to be dangerous but that's it

---

### Post by Dennis N on 2015-05-07
Assuming the computer is a BIOS system, boot into Ubuntu 14.04. In the terminal, **sudo grub-install /dev/sda** then **sudo update-grub**. If the drive is not sda change it to the correct designation.

After this, computer should boot to grub of Ubuntu.

---

### Post by Bashing-om on 2015-05-07
psfal; Hi !

It is a fairly simple operation to install ubuntu's grub from a liveDVD(USB). But, you must know what partition ubuntu is installed to.
You can start this process of discovery with terminal commands:
```

sudo fdisk -lu
sudo blkid

```
Differentiating between ubuntu and debian partitions might be a challenge ->
If the partitions are not identified. one can mount the partitions' file system and check for known files in a particular place.

Once identified the install command will be provided.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by psfal on 2015-05-07
Thanks so much, you've saved my butt from much nagging. Worked perfectly :)

---

### Post by psfal on 2015-05-07
Dennis' instructions took care of it, thank you. And thanks Bashing also for the additional info. You guys are great :-)

---

### Post by Dennis N on 2015-05-07
Glad your problem was solved, and thanks for the feedback. You can mark it solved with the thread tools just above post #1.

---

