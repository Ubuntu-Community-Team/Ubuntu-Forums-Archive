---
title: "Error while upgrading Kubuntu 17.10 to 18.04."
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by chaturbauka on 2018-08-08
[https://paste.ubuntu.com/p/xpqjGh38DX/plain/](https://paste.ubuntu.com/p/xpqjGh38DX/plain/)

Got errors cannot find swap device and missing firmware and dkms.conf. Please help. Thanks in advance.

[COLOR=#000000][FONT=sans-serif]Edit:- [/FONT][/COLOR][https://drive.google.com/open?id=1VDsv-Vd3-Q9ihn6hsLHxV5Jcy_bC9pAM](https://drive.google.com/open?id=1VDsv-Vd3-Q9ihn6hsLHxV5Jcy_bC9pAM)
[COLOR=#000000][FONT=sans-serif]I'm posting this alternate link as I am getting error on paste.ubuntu.com[/FONT][/COLOR]

---

### Post by springshades on 2018-08-08
Hey,

Let me start with a heads up that there are probably people who are better equipped to handle this one than I am. However, I've had experience with those dkms errors. There was an update a while back that caused a dkms error (I think it had something to do with the spectre/meltdown issues) that wiped out every Ubuntu computer I have, and I had to find workarounds for it.

(1) The dkms errors usually relate to a failure to build the driver module for your graphics card. That appears to be the case from your log.

(2) Did the upgrade error cause the upgrade to try to roll itself back or did the upgrade complete and you can't boot afterwards? If the former, I may not be able to help you. I never found a way to just flat out fix in. In my searches of bug reports, Debian/Ubuntu blame this issue on the drivers. They know about the fact that these things can happen in updates (they can even happen in a "apt dist-upgrade") but generally won't fix it. If the latter, you can usually get around the error by simply changing your kernel. It will probably boot if you just choose one of your other installed kernels in grub.

(3) If 2 makes sense and works for you, I've been able to come up with a permanent workaround to the issue most easily by changing my kernel line. If you go from the LTS kernel line to the HWE kernel line (or vice-versa), it usually fixes the problem. Once you delete the kernel with the issue (use autoremove after a few kernel updates) it's as if the issue never happened.

(4) The swap thing seems like it might be different. Any chance you used a swap file instead of a swap drive?

Note: I'm about 99% sure that this issue is not Kubuntu-specific, so you probably don't need to add that tag. The dkms issue that I had wiped out Xubuntu machines too. You might get more help if the Ubuntu users see it as well.

---

