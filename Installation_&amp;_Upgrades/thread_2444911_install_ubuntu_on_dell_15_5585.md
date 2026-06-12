---
title: "install ubuntu on dell 15 5585"
date: 2020-06-06
forum: Installation &amp; Upgrades
---

### Post by dbowen2 on 2020-06-06
I can not get Ubuntu 20.04 to install on this Dell 15 5585.

It has 256 GB SSD and a 500GB mechanical HD.

boot off the flash drive , do the install.... and it fails to install the "boot loader?"

I've been installing ubuntu for years and on every machine i've owned.... 
Now SSDs come along a wreck it.

help please.  I used to be a tech, but that was years ago.  I feel like i'm starting over.

- StratTuner

---

### Post by dbowen2 on 2020-06-06
well lets see if it improves by wiping out the SSD and installing.  That will make me lose the copy of windows there... but i'm out of things to try.

---

### Post by dbowen2 on 2020-06-06
nope it boots..gives me the GRUB menu and then a screen fll of gibberish.
last message is  "end Kernel panic - not syncing: Attempted to kill init! exit code=0x00000009 ]---

Is Ubuntu dead on all new computers?

---

### Post by oldfred on 2020-06-06
Dell normally works well, but requires some settings.

Have you updated UEFI?
Did you update SSD firmware?

What gpu are you using?
Most Dell that I have seen have been Intel, but yours looks like AMD?

Dell 5500 
[https://ubuntuforums.org/showthread.php?t=2436198](https://ubuntuforums.org/showthread.php?t=2436198)
 Dell Inspiron 5491
[https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes](https://askubuntu.com/questions/1191031/installation-on-new-laptop-dell-inspiron-5491-freezes)
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

### Post by crip720 on 2020-06-06
My Dell also had to change bios to ACHI from RAID.  Ubuntu installs well on SSDs, but a few computers do to need a few changes to bios and/or Windows for a dual boot or single install to be successful.

---

