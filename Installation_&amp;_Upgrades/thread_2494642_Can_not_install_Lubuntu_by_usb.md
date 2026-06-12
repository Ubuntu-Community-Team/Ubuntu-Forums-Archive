---
title: "Can not install Lubuntu by usb"
date: 2024-01-22
forum: Installation &amp; Upgrades
---

### Post by wtomekw25 on 2024-01-22
Hey, I had a problem with installing Lubuntu (new version) by usb drive. I did a research on the internet to understand what I do wrong but still can not install Lubuntu.

These are my steps, correct me if I am wrong.

1) I have another laptop HP Probook 5310m. I have checked that there is BIOS/Old Version.
2) Using rufus I check MBR (BIOS or UEFI)
3. Using BIOS I move usb disk to highest priority.
4. I choose UEFI Boot mode - disabled

It looks that usb drive is not visible and I can not start instalation.

Any help?

---

### Post by guiverc on 2024-01-22
> **wtomekw25 said:**
> Hey, I had a problem with installing Lubuntu (new version) by usb drive. I did a research on the internet to understand what I do wrong but still can not install Lubuntu.

These are my steps, correct me if I am wrong.

1) I have another laptop HP Probook 5310m. I have checked that there is BIOS/Old Version.
2) Using rufus I check MBR (BIOS or UEFI)
3. Using BIOS I move usb disk to highest priority.
4. I choose UEFI Boot mode - disabled

It looks that usb drive is not visible and I can not start instalation.

Any help?

You mention the "*new version*", so I assume that's Lubuntu 23.10 or the 2023-October release (*it's our newest*).

The installation section of the manual can be found here - [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)

Point 1 & BIOS/Old version?   I don't know what you mean here.

Lubuntu 23.10 will install on all of

- BIOS or legacy hardware
- uEFI hardware
- *modern* Secure-uEFI hardware

providing the ISO is written correctly to install media; ie. it's not reformatted; ie. it's simply written to the USB, and not reformatted via options selected.

I don't use rufus, but I believe to achieve a simple CLONE of ISO to media, you need to use what it calls `dd-mode`, ie a simple data-dump as files were written back to magnetic tape in the 1970s or early 80s (ie. no conversion/formatting).

If written correctly, you can leave your device in whatever mode you want it in, ie. boot & install in *legacy/CSM/BIOS/MBR*, use uEFI, even install with Secure-Boot or Secure-uEFI in. 

Your step 2 makes me think you're trying to reformat the ISO with options, rather than just writing/cloning it (unchanged) to the USB; as if you do you need to perfectly match the settings with your hardware & settings; leaving it default is usually best (it's what QA or *Quality Assurance* test for).

If the ISO isn't visible; that sounds like its either corrupt (did you verify it as per the manual says?) OR the write of ISO to media was incorrect (*either a bad write; and I get many of these each year OR you used inappropriate options for that ISO; just clone it or write without conversion** is my suggestion*).

---

