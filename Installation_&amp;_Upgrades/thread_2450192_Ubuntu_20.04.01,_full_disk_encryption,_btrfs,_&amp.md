---
title: "Ubuntu 20.04.01, full disk encryption, btrfs, &amp; hibernation?"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2020-09-09
I am trying to install *20.04.01 on my desktop with full (or almost full as Tj puts it) disk encryption including encrypted swap partition that allows hibernation, and btrfs.

The last few years I am using [ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption") but even being careful to make sure I do not turn my system off after an update before the grub fix script automatically runs, these updates or *Windows updates if dual booting, have broken grub and I have often had to boot to a live USB and run [fix-grub.sh]("https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b").

Yesterday I followed Tj's [Full_Disk_Encryption_Howto_2019]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019") but when I got to the point of formatting [COLOR=#333333][FONT=monospace]/dev/mapper/ubuntu--vg-root I searched to see if I needed to do anything extra to use btrfs and ext3. I have since learned that using btrfs is not as simple as just selecting another filesystem from the dropdown.

[/FONT][/COLOR]This next brought me to Willi Mutschler's [Ubuntu 20.04 with btrfs-luks full disk encryption including /boot and auto-apt snapshots with Timeshift]("https://mutschler.eu/linux/install-guides/ubuntu-btrfs/") which is very similar to Tj's, although it includes many extra steps for optimising btrfs and SSD. This is almost perfect for my intention, the only issue is that Willi sets it up so that swap is encrypted with a random password as he does not use hibernation:

```
[COLOR=#0086B3][FONT=&amp]export[/FONT][/COLOR][COLOR=#333333][FONT=&amp] SWAPUUID=$(blkid -s UUID -o value /dev/vda2)[/FONT][/COLOR][COLOR=#0086B3]echo[/COLOR] [COLOR=#DD1144]"cryptswap UUID=[COLOR=#008080]${SWAPUUID}[/COLOR] /dev/urandom swap,offset=1024,cipher=aes-xts-plain64,size=512"[/COLOR] >> /etc/crypttab
cat /etc/crypttab
[COLOR=#999988]*# cryptdata UUID=8e893c0f-4060-49e3-9d96-db6dce7466dc none luks*[/COLOR]
[COLOR=#999988]*# cryptswap UUID=9cae34c0-3755-43b1-ac05-2173924fd433 /dev/urandom swap,offset=1024,cipher=aes-xts-plain64,size=512*[/COLOR]

```
He references Archlinux's [dm-crypt/Swap encryption]("https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption") which I have looked through, and it would seem I need to set up some kind of hook for swap, but I have not been able to make much more sense of it than that.

Last night I found Félix Saparelli's [Full-disk encryption with Btrfs, swap, and hibernation]("https://blog.passcod.name/2020/jun/16/full-disk-encryption-with-btrfs-swap-and-hibernation"). It gives commands for setting up encrypted swap but not the rest of the install, so I had planned today to try and use it in conjunction with Willi's guide to achieve my desired install.

I wanted to post and ask if this is the best approach, or if there is better way to do this or a more complete guide?

*I would prefer to install Ubuntu Server edition on my desktop and then manually install my desktop environment as I have read this is an even more stripped down version of Ubuntu than the minimal install. Unfortunately when following Tj's guide, which is not intended for Server, after selecting the partitions the installer errored. Willi's guide references files for optimising btrfs in /usr/lib/partman which is not contained in the server installer and the same files do not exist anywhere else and it does not seem I can just install a package for partman.

*I was running a setup with Windows 10 on the same drive encrypted with VeraCrypt. This time I am not dual booting.[COLOR=#0366D6][FONT=SFMono-Regular]
[/FONT][/COLOR]

---

