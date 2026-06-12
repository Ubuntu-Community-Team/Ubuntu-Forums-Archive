---
title: "LUKS and 24.04 install"
date: 2024-09-07
forum: Installation &amp; Upgrades
---

### Post by makitso on 2024-09-07
I have a pretty busy Ubuntu Budgie 22.04.4 system with / and /home on separate partitions.  The /home partition is encrypted with LUSK.   After backing things up, I did an update to 24.04.1. The resulting system was highly unstable.  So, I started a clean install of 24.04.1.   My tried and true method of reinstalling the 22.04  OS on the / partition was to launch gparted, unlock the LUKS /home partition and complete the install.  With the new installer I did the unlock and proceeded with the install only to be told that my LUKS device was locked due to encryption.  I tried using the terminal and  cryptsetup luksOpen but the same outcome.    So, I had to restore  22.04.4  and look for another option.     Any suggestions?

---

### Post by TheFu on 2024-09-07
I've never looked at Budgie, so don't have specific ideas about that, however, 

I know that the Xubuntu and Lubuntu 24.04 installers don't allow LVM customization. Seems that having support for MSFT encryption in a dual-boot setup was more important than retaining the current LVM capabilities in desktops.  I can see why Canonical made that choice.  "New" users typically come from MSFT and have MS-Windows already installed.  Anyways ... that sorta leaves us screwed.

I had 2 workarounds.
[LIST]
[*]Install the 24.04 Server install. This has the same support for LVM, though it doesn't provide integrations for network setups. Typically, server installs use static IPs and netplan YAML for configurations. There's no GUI, so the GUI you are used to for network management isn't there.  I suppose you can add the budgie-desktop metapackage and get many things back, but IDK if that's true.  I don't use any DE anymore, just a nearly 30 yr old WM for my GUIs.
[*]Install Linux Mint 22 (I used the Cinnamon DE), which will setup LVM + LUKS for you, then just reduce the size of the "root" LV to something reasonable (use the bootable ISO for this), say 35G, and add new LVs for other needs like "home" and "var" and whatever else you like.  I typically add 4.1G for swap and for /tmp/ into an separate LV so I can control mount options and get a little better security, but you do you.  After that's all done, I install my WM with a lite login manager and purged Cinnamon's packages. Feel free to leave them if you like.  Mint 22 is based on 24.04 and doesn't have any snap packages.  I've been running it on a new-to-me laptop about a month now. No issues.  LUKS, LVM, standby, are all working. 
[/LIST]

Anyway, a few ideas for your consideration.  Some people posted they'd had 23.10 installed with their custom LVM+LUKS setups, then upgraded that to 24.04 ok.  You might consider that as well - or at least search for their posts about it.  

There is a launchpad bug on the poor LVM support in 24.04: [https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058511](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2058511)  It has been assigned a low priority, but the bug does have a few other workarounds for more nerdy people.  Not so much help for normal people that just want their computer to work and be upgraded with little hassle.

---

### Post by makitso on 2024-09-08
Thank you TheFU, this is why the forum is so important. So, the bottom line is that with a LUKS home partition,  "if" I can get this laptop upgraded to 24.04, I will never be able to reinstall the OS only, without reinstalling the encrypted  home partition.  :-(

---

### Post by TheFu on 2024-09-08
> **makitso said:**
> Thank you TheFU, this is why the forum is so important. So, the bottom line is that with a LUKS home partition,  "if" I can get this laptop upgraded to 24.04, I will never be able to reinstall the OS only, without reinstalling the encrypted  home partition.  :-(

I believe you've over-simplified what I said.  Only you know your skills.  

On some things, I'm, very practical and when it comes to LUKS and full system encryption, I'm even more practical, since it needs to work without me manually having to edit the crypttab or initramfs.  

But you are probably more stubborn than I am about these things.  I have excellent backups of data, especially data stored on encrypted storage, so wiping everything and restoring it isn't anything complex to me.  The fact that it is encrypted might add 30 seconds extra to the restore effort. It doesn't impact backups at all, at least with the way I do automatic, daily, versioned, backups. YMMV.

I don't know your storage setup.  My laptop has a single 500G SSD inside it and I'm probably using less than 100G of that.  Backing up 100G is nothing to me. Plenty of storage available on my network for this sort of need.  These days, a 4TB USB HDD is about $40, so there's little excuse for not having excellent backups. Here's my main backup HDD for all my systems here:
```
$ df /d/b-D7/
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB--B-lv5_back  3.4T  1.4T  1.9T  43% /d/b-D7
```
Lots of room and it has 90-366 days of versioned backups for about 10 systems - not counting media files. Media file backups are handled separately.

---

