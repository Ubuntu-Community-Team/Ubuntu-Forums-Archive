---
title: "Change /boot in this BTRFSonLUKS install so passphrase prompt after GRUB?"
date: 2020-09-14
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2020-09-14
[COLOR=#242729][FONT=Arial]I have also posted this on [Ask Ubuntu]("https://askubuntu.com/questions/1274972/change-boot-in-this-btrfs-luks-install-method-to-facilitate-future-chain-loadin"). 

I have installed Ubuntu 20.04.1 on my laptop according to [Ubuntu 20.04 with btrfs-luks full disk encryption including /boot and auto-apt snapshots with Timeshift]("https://mutschler.eu/linux/install-guides/ubuntu-btrfs/") using an encrypted swap file twice the size of my RAM which I have setup for suspend-then-hibernate - I skip the commands referencing the swap partition. I am very happy with the setup and I want to configure it on my desktop but I would like to tweak it to make dual booting a future Windows install easier, something which I do not do on my laptop.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
The crux of this is that on boot my laptop prompts me for my passphrase before displaying the GRUB menu, which I actually prefer, but on my desktop when I make changes in the future so I can chain load a future VeraCrypt Windows install on another drive, it will mean multiple passphrase entries just to start booting.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
On my current desktop setup, LUKS Ubuntu 18.04 is [Using VeraCrypt with a UEFI dual boot]("https://medium.com/@lankycyril/using-veracrypt-with-a-uefi-dual-boot-setup-27d1eacbf36b") for Windows 10, prompting only for one passphrase after an OS is selected from GRUB but it is using the older [ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption") setup method without the advantages of the btrfs-luks with timeshift setup.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I understand that I should use the normal ubiquity installer instead of ubiquity --no-bootloader, and that /boot should be outside of the btrfs-inside-luks partition for the setup I desire but I am unsure exactly how to change the steps in the guide to set this up so it will work and be secure. Before I start my install I would very much appreciate if someone could please clarify the changes I should make to the commands including what size /boot or /boot and /boot/efi should be.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My version of the setup on my laptop starts with:
[/FONT][/COLOR]
```
parted /dev/nvme0n1
mklabel gpt
mkpart primary 1MiB 513MiB
mkpart primary 513MiB 100%

```

Which I could change to:

```
parted /dev/nvme0n1
mklabel gpt
mkpart primary 1MiB 513MiB
mkpart primary 513MiB 2013MiB
mkpart primary 2013MiB 100%

```

---

