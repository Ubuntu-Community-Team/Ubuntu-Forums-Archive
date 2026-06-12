---
title: "Issue whenever restarting laptop for installation"
date: 2017-06-28
forum: Installation &amp; Upgrades
---

### Post by gabolein on 2017-06-28
Hi,
I've been trying to install Ubuntu 17.04 on my new laptop. I created a 150 GB partition on my hard disk and then installed Ubuntu through USB. Everything went fine until I was asked to restart. Upon restarting the screen was black and it read

```
platformMSFT0101:00: failed to claim resource 1
acpi MST0101:00: platform device creation failed: -16
```

ecc., it goes on quite a bit but it seems like the error is already known. The problem is people advice with ignoring it. If I ignore it nothing happens, it lets me do nothing, I can just type or shut down the laptop by brute force. 
So I shut it down. I tried turning it on again and reinstalling Ubuntu. This time another error showed up, which I can't even recall, that ended up blocking the laptop so I restarted and the same screen appeared.
I'm completely helpless, there's no help to be found online and I have no idea how to solve it as I'm not even able to boot Ubuntu since it's not correctly installed.
I would really appreciate if anyone had an idea on how to solve this.

---

### Post by QIII on 2017-06-28
Hello!

That may be due to the motherboard's manufacturer implementing Microsoft's Trusted Platform Module on the board.

What version of Windows are you using?  If your machine came with Win 10, is will be installed in UEFI mode.  Linux will have to be installed likewise.  That might help.

---

### Post by gabolein on 2017-06-28
Thanks for the reply. I indeed have Windows 10. Should I reformat my hard disk before trying again as Ubuntu is technically already installed on the partition?

---

### Post by gabolein on 2017-06-29
So I followed this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Unfortunately it still didnt work

---

