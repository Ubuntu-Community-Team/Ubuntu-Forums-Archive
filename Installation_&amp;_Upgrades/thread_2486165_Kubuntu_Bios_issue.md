---
title: "Kubuntu Bios issue"
date: 2023-04-21
forum: Installation &amp; Upgrades
---

### Post by spaarks on 2023-04-21
I am trying to run Kubuntu 23.04 on a Linux Mint MATE installation.
Bios 2.17.1246.
In Bios I disable UEFI, then select USB under Legacy option (before hard drive)..
Save and exit.
Computer boots installed Linux Mint.
I have tried with Kubuntu ISO on two USB sticks.

---

### Post by oldfred on 2023-04-21
What brand/model system?
Is UEFI firmware latest version?

Why disable UEFI? It has been the standard since 2012.

Also UEFI setting is for installed system. It may or may not then be setting for USB flash drive depending on your vendors's UEFI. Most have two boot entries in UEFI one clearly UEFI as [noparse]UEFI:XXXX[/noparse]  and other as BIOS as xxx where xxx is name or label of flash drive.
Then how you boot live installer flash drive, must match UEFI setting, so system will boot without error.

---

