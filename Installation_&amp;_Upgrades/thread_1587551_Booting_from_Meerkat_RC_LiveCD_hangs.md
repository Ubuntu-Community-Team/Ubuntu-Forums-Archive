---
title: "Booting from Meerkat RC LiveCD hangs"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by PapaNerd on 2010-10-03
Process and problem description:
 1. downloaded ubuntu-10.10-rc-desktop-amd64.iso and burned to CD.
 2. re-booted.
 3. "ubuntu" is displayed center screen with five dots below text (sequencing white and red).
 4. screen jumps to alternating horizontal bars (green & purple plus green & pink sections) about 1/4 inch high.
 5. cd activity light stops blinking.
 6. no standard desktop ever appears.

System:
 - Asus A8N-VM CSM with integrated nVidia C51PV [GeForce 6150] display
 - AMD Athlon(tm) 64 3200+ CPU
 - 2.5GB DDR 333 MHz memory

Has anyone else run across this?  Obviously, trying to convince a friend to switch to ubuntu using this CD would not be good.

---

### Post by coffee412 on 2010-10-03
> **PapaNerd said:**
> Process and problem description:
 1. downloaded ubuntu-10.10-rc-desktop-amd64.iso and burned to CD.
 2. re-booted.
 3. "ubuntu" is displayed center screen with five dots below text (sequencing white and red).
 4. screen jumps to alternating horizontal bars (green & purple plus green & pink sections) about 1/4 inch high.
 5. cd activity light stops blinking.
 6. no standard desktop ever appears.

System:
 - Asus A8N-VM CSM with integrated nVidia C51PV [GeForce 6150] display
 - AMD Athlon(tm) 64 3200+ CPU
 - 2.5GB DDR 333 MHz memory

Has anyone else run across this?  Obviously, trying to convince a friend to switch to ubuntu using this CD would not be good.

Try hitting the shift key before ubuntu loads and this should bring up some boot options. Try the boot safe mode to see if it will work.

---

### Post by PapaNerd on 2010-10-03
Thanks for the quick reply coffee412.  I tried several different boot options without success, but feel a bit acronym challenged when looking at the help page.

---

### Post by coffee412 on 2010-10-03
> **PapaNerd said:**
> Thanks for the quick reply coffee412.  I tried several different boot options without success, but feel a bit acronym challenged when looking at the help page.

So, Im assuming that you tried the safe mode boot? That means it was using the basic (vesa?) video driver and you had the same problem.

Could be incorrect video card default settings. Im curious. Did you try 9.04 (karmic) and have a problem also?

---

### Post by PapaNerd on 2010-10-04
I was unable to find anything called "safe boot mode", but did try some boot parameter changes (the F6 help key).

This system has been running v9.04 and has not be upgraded.

I tried some older CDs/DVDs:
ubuntu-9.04-dvd-amd64.iso (Jaunty Jackalope) comes up okay.
ubuntu-9.10-dvd-amd64.iso (Karmic Koala) comes up okay.
ubuntu-10.04-dvd-amd64.iso (Lucid Lynx) displays the horizontal bars.
ubuntu-10.04.1-desktop-amd64.iso (Lucid Lynx) displays the horizontal bars.

---

### Post by wilee-nilee on 2010-10-04
Looks like a video card problem, you tried nomodeset in f6 correct?

If you boot into 9.04 and run this command it will identify the graphics setup you might post it.
```
lspci | grep VGA
```

---

### Post by PapaNerd on 2010-10-04
I tried "nomodeset" and was able to toggle between CLI screens, but not into the GUI.  The "lspci" command gave the same output as the "lshw" command included in my initial posting (nVidia C51PV [GeForce 6150]).  Video is integrated on the motherboard, and the only difference between success and failure of the LiveCD seems to depend on the version of ubuntu.  

Did something in the installation process change between 9.10 and 10.04 to account for this?  For example, if the default assumes a 16:9 aspect ratio as opposed to a 4:3 aspect ratio, this would not be as robust as users would expect.

---

