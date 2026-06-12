---
title: "Install Ubuntu from different partition on same HDD"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by anonymous666 on 2008-02-09
The situation:

A laptop with a broken optical drive
BIOS does not support USB booting
A USB floppy drive (fortunately the BIOS supports booting from this)
An external USB HDD for file transferring)

I already made 3 partitions on the HDD (let's call them X, Y, Z)

I transferred ubuntu 7.10 alternate ISO to Y, xcopied extracted ubuntu 7.10 ISO to Z ( both using a dos-based floppy with USB HDD driver).

Now I have X (empty), Y (ISO) and Z (extracted ISO)

I want to install ubuntu into X, but dont know how to proceed. I found that I can mount the ISO from Y [using TomsRtBt]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") and install from there, but the instruction is for Breezy and I dont know whether it will work with current release. I also read somewhere that Loadlin/LinLd can be used to run linux from DOS environment but I'm not sure on how to use that to install ubuntu. Which way is the easiest to proceed from this situation? Thanks in advance

---

### Post by Pumalite on 2008-02-09
Have you thought about:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
I hope you have Internet.

---

### Post by anonymous666 on 2008-02-09
> **Pumalite said:**
> Have you thought about:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
I hope you have Internet.

I havent come accross the WindowsServerNetboot yet until you pointed that out. However can the Dapper Netboot image work with Gutsy ISO? Thanks

---

### Post by Pumalite on 2008-02-09
I think you can get up to Feisty.

---

### Post by anonymous666 on 2008-02-09
Ignore my post above. I was replying without fully understanding how the Netboot+Internet works. I thought I have to host the ISO somewhere on the network. Now I understand that it needs internet. I'll be back with an update in a few hours. Thanks again.

UPDATE:

Installing Gutsy now via Netboot now :)

However I'll leave this thread open for discussion on my original problem (for those without internet access)

---

