---
title: "Cannot install 16.04 from live CD or USB stick"
date: 2016-06-06
forum: MINT
---

### Post by Responsive on 2016-06-06
is there anyway to boot to bios?

struggling with this.

---

### Post by oldfred on 2016-06-06
It should be a choice in UEFI.
Since BIOS is not Secure Boot, you must have the Secure Boot UEFI setting off.
But may still have a setting for UEFI or BIOS/CSM/Legacy.
Some computers call the Secure boot setting "Windows" or "Other".

---

### Post by Responsive on 2016-06-07
is there anyway so check secure boot in LinuxMint?

it is obvious when I google the issue, that we are not the first people to ask this question.

---

### Post by howefield on 2016-06-07
Posts moved to own thread.

---

### Post by sudodus on 2016-06-07
Ubuntu provides kernels (and the whole mechanism) for [UEFI] secure boot.

I don't know if it is the case with Linux Mint, but I know that it can boot 64-bit systems in UEFI mode (without secure boot). Correct information about secure boot should be available at the Linux Mint web site or the Linux Mint user forum.

-o-

You can check for secure boot or similar in the BIOS/UEFI menu system, which can be very different in different computers, and also contain very different items.

---

