---
title: "Minimal Grub, hidden EFI, Surface Pro 3"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by MobiusOne on 2014-09-05
Hi Guys,

I have a really BIG problem. I have hidden (and set as read-only) the EFI partition from my Surface Pro 3. After the installation of Ubuntu on a USB Stick, the device crashed. I had no oppertunity to unhide the EFI partition. When the device starts, I only see the Grub minimal Bash-Like ...

How can I fix this? I can`t boot a USB stick! With the command LS, I only see this: (hd0) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1). Their is no Ubuntu installation on the hd0.

Please help :(

PS. sorry for my English

---

### Post by MobiusOne on 2014-09-05
I fixed the Problem with this command:
chainloader /efi/Microsoft/Boot/bootmgfw.efi
boot

I could boot to the Windows Bitlocker Recovery and after that to the Windows Recovery Environment. Here I could reset the Windows Installation.

:)

---

