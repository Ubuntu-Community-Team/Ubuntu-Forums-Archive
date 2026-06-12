---
title: "Laptop loops &quot;Reset system&quot; after trying to install ubuntu-22.04-desktop-amd64."
date: 2022-06-25
forum: Installation &amp; Upgrades
---

### Post by peps123 on 2022-06-25
Hello, hope someone can help. 

After I installed ubuntu-22.04-desktop-amd64. my laptop (Thinkpad T1440p) get stuck in "Reset system" loop and power cycles. 

How I installed ubuntu:

[LIST]
[*]Check the ISO after I downloaded it In Powershell using: certutil -hashfile ubuntu-22.04-desktop-amd64.iso SHA256
[*]And both match: b85286d9855f549ed9895763519f6a295a7698fb9c5c5345811b3eefadfb6f07 *ubuntu-22.04-desktop-amd64.iso
[/LIST]

[LIST]
[*]Downloaded from the official site, and the version is ubuntu-22.04-desktop-amd64.
[*]And so far have tried making the USB with Etcher, Rufus and Pi imager. All with the same results.
[/LIST]

My laptop is set up for UEFI only, secure boot off and checked drives by installing Windows 10 on them without an issue, pre installation I have also gone into gparted wiped the disks and made a new GPT  partition table. 

I have also booted into the live USB and run:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-repair 
```

And running Boot Repair from within the ubuntu menu, without this solving the problem. 

I'm new to Linux so sorry if I have missed something really important, or omitted useful information. 

Regards the hardware its an i5 with 8gb and 2 SSD's (both SSDs are compatible as I have another T440p with the same make and model drives running a multi boot Windows, Kubuntu and POP-OS). 

But now I am stumped!

---

