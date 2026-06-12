---
title: "Installation of ubuntu-16.04.desktop-amd64.iso hangs On HP 15-N0004 TX laptop"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by shridhar-kapshikar on 2017-06-14
Hi All,

I am trying to install the ubuntu 16.04 from the pre-build image but it won't be going ahead. I have been seeing 2 error messages on screen and

```

[FAILED] Failed to start Light Display Manager
[*****] A start job is running for hold until boot process finishes up. ( time/ no limit)

```

I have tried the installation in both non-efi and efi model. Here is output from my dmesg logs.

```

# dmesg |grep EFI
[    0.000000] ACPI: UEFI 0x0000000092FFD000 000236 (v01 HPQOEM 2164     00000001 HP   00040000)
#


```

Even though I have tried to add "nomodeset" parameter at the installtion stage but that also didn't work.

Can you please advise on this.

---

### Post by 2011spook on 2017-06-14
what kind of computer are you trying to install it on, we should start there

---

### Post by kc1di on 2017-06-15
What graphic card does that machine have?
I believe it Nvidia if so the nomodeset should work to get you in. 
Where did you place nomodeset ?

it should go on the boot line right after "quiet splash"  and look something like this
```
quiet splash nomodeset
```

if that does not work try this one
```
quiet splash nouveau.noaccel=1
```

once in go to Additoinl drivers and install the recommended driver for your card. 
good luck.

---

### Post by shridhar-kapshikar on 2018-03-05
Sorry for very late response. It has the RADEON graphics card on this machine.

---

