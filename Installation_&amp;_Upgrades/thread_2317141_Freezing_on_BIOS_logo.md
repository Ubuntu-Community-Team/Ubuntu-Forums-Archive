---
title: "Freezing on BIOS logo"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by BIGREDUNIT on 2016-03-13
I have recently installed the latest version of Ubuntu onto a fresh computer with nothing else installed.

I was getting an issue with it freezing on a black screen after the BIOS full screen logo.

Now I have changed the BIOS setting CSM Support to "never" and I cant get the system past the full screen BIOS logo with using grub.

I have to hold/press the right shift key to get it to the grub screen then select the first option "*Ubuntu" which will then boot to the operating system albeit slowly.

My question is - is there a way to avoid having to get to the grub screen? or is that just what I have to do every time now?

---

### Post by grahammechanical on 2016-03-13
Here is a question.

Is Ubuntu is installed in EFI mode? If it is then setting CSM/Legacy mode won't bring up the Grub boot menu. If the UEFI boot system is set to EFI mode then Ubuntu must be installed in EFI mode.

When Ubuntu is the only OS the Grub boot menu will not appear.

Regards

---

### Post by BIGREDUNIT on 2016-03-13
Yes Ubuntu is installed in EFI mode.

So if there is no other OS installed then I have no option but to manually trigger grub boot menu?

---

