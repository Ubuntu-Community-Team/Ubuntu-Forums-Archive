---
title: "Can't install new OS"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by ray9 on 2016-10-03
This is the same old same old about installing a new OS thru Grub.  I bought a NEW PC and put my old hard drive with Ubuntu 14.04 in it along with a drive with WIN10 and another drive with Ubuntu 14.04.  My old drive was pretty full that's why I went with a fresh drive with 14.04 on it.  So, there are some very interesting new Linux OS's out there I'd like to try but I can't run any of my dvd's thru grub.  I put them in the machine but the grub menu that tied all my drives together doesn't want to see a new dvd.  How can I break thru grub to add another OS to one of my drives???  The one I'm most interested in is Linux Lite.

Thanks in advance.

---

### Post by TheFu on 2016-10-03
Linux really isn't a different OS with each distro. They really just change the default programs and the GUI.
If you know what programs you already want, switching distros just isn't necessary.  You can swap in any GUI that you like. Just use a different userid when testing it so any conflicting config/settings are stored in a different location.  Lots of GUIs are based on gnome, gnome2, and other GUI toolkits - those are the ones most likely to have incompatible settings that may cause issues.

In short, no need to waste 6G on a new distro when 500MB will load a new GUI.

---

### Post by oldfred on 2016-10-03
You normally do not install systems from grub.
Just like when you installed Ubuntu, you have to go into UEFI and choose to boot flash drive.
And how you boot installer UEFI or BIOS is then how it installs. You need to be consistent with all installs. All UEFI or all BIOS.

If another flavor of Ubuntu, that install will overwrite the /EFI/ubuntu folder in the ESP - efi system partition and become the default boot. Back up the ESP first, just in case.

---

### Post by ray9 on 2016-10-04
The thing is I can't get into bios or uefi.  F10, F2, F9 none will bring up bios at boot.  Goes right into grub.

---

### Post by oldfred on 2016-10-04
Did you leave fast boot on in UEFI. That assumes no system changes and immediately jumps to booting leaving no time for to press any keys.
Cold boot should work, or the last entry in grub menu is a direct to UEFI/BIOS entry.

---

### Post by RobGoss on 2016-10-04
You might get better help if you told us what kinda of machine you're trying to install Linux on this way if we need to do a bit of research at least we know what were working with

---

### Post by TheFu on 2016-10-04
> **ray9 said:**
> The thing is I can't get into bios or uefi.  F10, F2, F9 none will bring up bios at boot.  Goes right into grub.

I have a box like that - 1 in 50 attempts hitting the correct key works.  I looked up in the MB manual (home built system) which key would get into the BIOS.  The only sure-fire way I found was to use a PS2 keyboard connector.  I hate graphical BIOS systems that work with mice!

---

### Post by RobGoss on 2016-10-04
I think it's safe to say most machines will allow you to access the BIOS hitting the** F12**, key sometimes** F2** depending on what machines you're using. I have a mini netbook that only allow me to access the BIO's by pressing the F10 so it really what computer is used. I'm sure there's some info on the machine in question on how to access the BIOS's but with out knowing what kind of computer were all guessing  here

---

### Post by ray9 on 2016-10-04
What I have is a  Cybertron-AMD FX-4130 Quad Core Processor 3.80 Ghz, RAM 12 GB, Win 10 on a 931 G drive and two versions of Ubuntu on 2 other 500G drives.  The set-up screen goes by so fast you can barely see it.  Holding the keys down before hand  doesn't work.  So on edit you press "delete" to get into the BIOS.  I set it to boot from the cdrom but it still runs right into the grub boot screen w/o running the cd.

---

