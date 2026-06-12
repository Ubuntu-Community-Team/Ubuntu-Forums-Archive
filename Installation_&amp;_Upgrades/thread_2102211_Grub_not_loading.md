---
title: "Grub not loading?"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by HeinzVoerbakje on 2013-01-06
Hi everyone,

I bought a new laptop, a HP G7-2201SD-AMD C-A6 4400M with windows 8. I installed Kubuntu on it, but after the installation Grub is not loading. I have to press ESC when the laptop boots and then select F9, boot options, then Kubuntu, then I get Grub, where I select Kubuntu and I can boot into Linux. Is it possible to run Grub by default without going through all these steps? I've installed Grub on sda, so I expected it to handle the boot process, but unfortunately it doesn't by default :-(

Who can help me out?

Thanks!

HeinzVoerbakje

---

### Post by darkod on 2013-01-06
Sounds like you installed in legacy mode. On the new UEFI machines you need to install in uefi mode. If your new machines comes with Secure Boot like most new win8 machines, note that right now only 12.10 64bit is secure boot compatible.
Some basic uefi info:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by HeinzVoerbakje on 2013-01-06
Thanks voor the reply, I've now reinstalled Kubuntu in UEFI mode, but the problem persists, I have to press ESC and press F9 and so on to get to Grub. Also in the Windows 8 advanced settings I cannot select any other operating systems than windows 8 to boot, I really have no clue!

I really like to have this solved, who can help me out?

Thanks, HeinzVoerbakje

---

