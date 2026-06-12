---
title: "Installing Ubuntu on Medion Erazer X7820 (MD99085)"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by kaefert66014235 on 2013-01-01
Hi there!

I've got this new machine here, it's name is
```
Medion Erazer X7820 (MD99085)
```

It's processor is an
```
INTEL® CORE&#8482; i7- 3630QM
```

And the graphics card is an
```
NVIDIA® GEFORCE® GTX 670MX
```

For more details look at
[http://aldi.medion.com/md99085/at/]("http://aldi.medion.com/md99085/at/")

It came with Windows 8 on it, and I thought I'll set it up as a dualboot machine with Windows 8 and Ubuntu. However, it doesn't seem to be as easy as I thought.

First with the boot mode in the BIOS set to "EFI" I manage to get Ubuntu to boot from USB sticks up to the point where I see the Grub2 interface, but also when I remove the "quite splash" from the boot config, the device won't show me anything afterwards.

After switching the boot mode to "Legacy" I managed to boot the live version of linux mint 14 in compatibility mode, but the instalation won't finish, it hangs on "configuring hardware" (or something like that, did the installation with the german translations)

Ubuntu 12.10 won't finish to boot, the last two lines that he prints (after removing the "quite splash" part from the boot options) are:

```
mttr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
```

My (unfinished) Linux Mint 14 installation that I repaired by installing grub manually afterwards by following this guide: [http://wiki.ubuntuusers.de/chroot/Live-CD](http://wiki.ubuntuusers.de/chroot/Live-CD) shows the same last lines before it freezes (at least there is no switching ttys, and no reaction to strg+alt+entf = ctrl+alt+remove)

Then I thought the memory is damaged, since I got errors in the memtest, but after googling the error I found that it matches exactly this description: [https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209](https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209)

Please help, I'm already sitting at this machine for more than a day, and normally it takes me an hour or two to get a dual boot setup up and running...

---

### Post by kaefert66014235 on 2013-01-02
Okey so Linux Mint 13 (Ubuntu 12.04) installed fine, but X didn't boot at first, after installing nvidia drivers and running nvidia-xconfig , he managed to start X in some failsafe mode, but no graphic effects.

Today in the morning I returned the notebook back to the shop, so the problem has been circumvented for me ;)

---

### Post by MrColdbird on 2013-01-03
Thats a shame you returned it... cause this device is GOLD on Ubuntu.

[LIST]
[*]LONG BATTERY RUNTIME (6-7 Hours)
[*]EVERYTHING WORKS (Bluetooth, WLAN, Powersaving, etc.)
[*]BLAZING FAST
[/LIST]
The only problem this device has is that installation is troublesome... and tricky... but hey...
I've figured out how its done and post it here so others got a easier time than I did.
):P



[LIST=1]
[*]First thing... don't bother with the normal Ubuntu Install Disc... it won't work!
Instead get Lubuntu 12.10 Alternate Installer Disc (text-based Installer)!
[*]Now just install Lubuntu 12.10 like you would on any other PC!
[*]After Installation you will notice that the thing won't boot... you will get a black screen and that's it. Don't worry. Boot into Recovery Mode instead and pick Root Shell.
[*]Connect to your network of choice (ask Google on how to connect to your Wireless / Wired Network from a terminal)!
[*]Type in the following commands:

mount -o remount,rw /
add-apt-repository ppa:ubuntu-x-swat/x-updates
add-apt-repository ppa:bumblebee/stable
apt-get update
apt-get install linux-headers-generic
apt-get install bumblebee
apt-get upgrade
reboot
[*]Voila! Done! Everything should work now!

Should you wish to run graphically intensive stuff like 3D games on wine use the optirun command like this...

optirun wine blabla.exe
[/LIST]
Should you wish to change the Desktop to the default Ubuntu one, just do a sudo apt-get install ubuntu-desktop command and you should be back to Unity. :p

---

### Post by anaka13 on 2013-02-23
Well, almost getting off-topic, but can you update us on weight, noise, and maximum memory? I expect the motherboard to have 4 slots for up to 32gb ram but you never know. Also the speed of the installed memory? Thanks!

Ps the questions are not entirely academic, if 16GB RAM is maximum then it makes sense to buy that configuration from the Medion shop, otherwise the 8GB on the ALDI offer can be thrown away for the 4x8 I want in an upgrade.

Edit 1: I went out and bought it for the 670MX, so I can answer a few questions on my own. Max memory seems to be 16GB with 2x4GB extremely slow RAM in the machine I bought, as well as a not so fast hard disk. So, out of the box not such a brilliant impression from this great processor and graphics card. Now, it has resisted my efforts to boot most of my USB and DVDs with Linux, never mind install them. Also resists booting Windows without Secure Boot on, looks like windows.efi or whatever it's called is encrypted? When I did get some kind of EFI partition on a second hard disk I installed, everything stopped booting (perhaps a result of my EFI not being signed by Linux the right way?) . I have to say I'm quite shocked by the way the Boot Menu F10 ignores most of my bootable media, they just never show up in the list!

---

### Post by MrColdbird on 2013-03-08
First things first... forget about the preinstalled Windows 8, its crap... boot into the BIOS first and switch booting mode to legacy mode... then launch a linux live disc of choice that actually boots (not Ubuntu) and wipe the HDDs clean.
And by clean I don't mean gparted, but a shredder instead (fully zeroing them).

This has to be done because by default it has a GUID partition  table on it... and partitioning a MBR on top breaks things (or far more  confuses things) as it will detect the HDD as both MBR and GUID... and  depending on OS of choice, one will prefer the MBR and one the GUID  partitions...

The reason your boot devices arent shown is quite simple - its that EFI boot crap... by switching to legacy mode its back to normal.

As for the RAM slots... the one I got had a single 8GB RAM bench in there, from what I could see it only has one (reachable) RAM slot, but I heard (in other forums) that there is a second RAM slot right beneath the keyboard (not reachable without full disassembly) - which I didn't confirm myself yet though.

But yeah, with Legacy Boot turned on in BIOS, every Linux distro should (at least) boot. As for me I had to use the Lubuntu text-based installer as the graphical ones from Ubuntu seem to get stuck at some point.
Once installed Ubuntu runs great, so does Windows 7.

As for operating noises... really not too bad in my opinion. The weight sure is the big no-no on this one, its rather heavy but still comfortable on your lap. You will notice it however when you carry it around, it sure is a biggie.

Overall though I'm extremely happy with this box, it gives me superb performance at a affordable cost.

---

