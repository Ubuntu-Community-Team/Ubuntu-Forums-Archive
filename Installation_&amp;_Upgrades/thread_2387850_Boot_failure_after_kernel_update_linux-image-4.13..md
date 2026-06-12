---
title: "Boot failure after kernel update linux-image-4.13.0-37-generic"
date: 2018-03-24
forum: Installation &amp; Upgrades
---

### Post by pierotiste on 2018-03-24
Hi, I never report this kind of issues, but to the best of my knowledge, there is no mention anywhere of this issue, that might be specific to my system somehow:

I have recent installation of Ubuntu 17.10, and since the latest kernel upgrade (linux-image-4.13.0-37-generic) the system fails to boot. It happens after Grub, Grub is working fine and the previous kernel version (selected via Grub) boots fine.
The screen (still black) freezes with a single line:
```
/dev/sda5: clean 815861/3055616 files, 9118912/12206848 blocks
```

Let me know if I should report this as a bug, and how to provide more information on this issue.

Thanks!

---

### Post by tinylagarto on 2018-03-24
It looks like a bug to me. I would report it.
The same kernel works here without issues. 

Normally after the mentioned single line you should boot into your session.

---

### Post by pierotiste on 2018-03-26
OK thanks. Any idea on how to get more data on it?

---

### Post by tinylagarto on 2018-03-26
Do you mean how to report a bug to Ubuntu?

I would take a look here:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by pierotiste on 2018-04-07
So I didn't figure out what was the issue, but kernel linux-image-4.13.0-38-generic fixed it.

---

