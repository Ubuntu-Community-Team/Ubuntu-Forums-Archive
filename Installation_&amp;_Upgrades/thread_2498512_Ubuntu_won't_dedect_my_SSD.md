---
title: "Ubuntu won't dedect my SSD"
date: 2024-06-17
forum: Installation &amp; Upgrades
---

### Post by mufurkan on 2024-06-17
I have tried installing linux several times and failed becasue no of the distros can dedect my SSD
I tried installing linux mint and it works and dedects my SSD so i install it

But i want to swich to ubuntu now unfortunately it doesnt see my SSD

I did a lot of research and tried lots of things:
[LIST]
[*]Changed raid to ahci
[*]Turn off secure boot
[*]Turn off tpm
[/LIST]
None of that worked

Why ubuntu cant see my ssd adn how can i fix it

Edit: i runned this code in mint to learn what my ssd is
[COLOR=#000000]furkan@furkan-EXCALIBUR-G900:~$ sudo dmidecode -s bios-version[/COLOR]
[COLOR=#000000]CP141[/COLOR]
[COLOR=#000000]furkan@furkan-EXCALIBUR-G900:~$ udisksctl status[/COLOR]
[COLOR=#000000]MODEL REVISION SERIAL DEVICE[/COLOR]
[COLOR=#000000]--------------------------------------------------------------------------[/COLOR]
[COLOR=#000000]CT1000P2SSD8 P2CR048 2223E6392E6A nvme0n1[/COLOR]

---

### Post by oldfred on 2024-06-17
Have you updated UEFI firmware & SSD firmware to latest available?
Even new system may have updates.
sudo dmidecode -s bios-version
udisksctl status

Mint is based on Ubuntu, so at low level detecting drives, I would expect it to be the same?
What version of Ubuntu. If newer system, try live installer from 24.04 to have latest drivers & kernel.

What brand/model system & SSD?

---

### Post by currentshaft on 2024-06-17
> **mufurkan said:**
> I have tried installing linux several times and failed becasue no of the distros can dedect my SSD
I tried installing linux mint and it works and dedects my SSD so i install it

But i want to swich to ubuntu now unfortunately it doesnt see my SSD

I did a lot of research and tried lots of things:
[LIST]
[*]Changed raid to ahci
[*]Turn off secure boot
[*]Turn off tpm
[/LIST]
None of that worked

Why ubuntu cant see my ssd adn how can i fix it

Why would turning off secure boot help detect your SSD? People try the weirdest stuff ...

Anyway, you haven't mentioned what SSD you're trying to use, nor what "not detected" means. What applications have you used or commands have you run to detect it?

---

### Post by mufurkan on 2024-06-17
> **currentshaft said:**
> Why would turning off secure boot help detect your SSD? People try the weirdest stuff ...

Anyway, you haven't mentioned what SSD you're trying to use, nor what "not detected" means. What applications have you used or commands have you run to detect it?

I cant see the ssd in in the installer or gparted or lsblk.
On Ubuntu it only shows my usb
[IMG]https://i.ibb.co/zSCSDsK/Whats-App-Image-2024-06-17-at-22-25-18-1.jpg[/IMG]
[IMG]https://i.ibb.co/wwNwDLF/Whats-App-Image-2024-06-17-at-22-25-18.jpg[/IMG]
[IMG]https://ibb.co/2s7sX61[/IMG]
[IMG]https://ibb.co/64G4LY6[/IMG]

---

### Post by mufurkan on 2024-06-17
When i run code in my curret mint system i get this
furkan@furkan-EXCALIBUR-G900:~$ sudo dmidecode -s bios-version
[sudo] password for furkan:       
CP141
furkan@furkan-EXCALIBUR-G900:~$ udisksctl status
MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
CT1000P2SSD8              P2CR048   2223E6392E6A         nvme0n1

My laptops manufacturer(Casper) doesn't offically support linux and won't provide bios updates or linux drivers
Edit: i did some research and i think i found  my ssd model [https://linux-hardware.org/?id=pci:c0a9-540a-c0a9-540a](https://linux-hardware.org/?id=pci:c0a9-540a-c0a9-540a) it says supported on ubuntu but mine is not working

---

### Post by mufurkan on 2024-06-17
I did some more digging and found this
"
[COLOR=#000000][FONT=&quot]kernel: nvme nvme0: pci function 0000:02:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]kernel: nvme 0000:02:00.0: Unable to change power state from D3cold to D0, device inaccessible[/FONT][/COLOR]
"
It could be a kernel bug same bug appears here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2047728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2047728)

---

### Post by ubfan1 on 2024-06-17
It does look like the same bug, do join the bug (the "Does this affect me?" yellow circle in upper left corner).

---

