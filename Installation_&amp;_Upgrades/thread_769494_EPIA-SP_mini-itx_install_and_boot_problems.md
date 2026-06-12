---
title: "EPIA-SP mini-itx install and boot problems"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by kazzle101 on 2008-04-26
Hello,

I have a via mini-itx EPIA-SP 13000. Previously I have had this working fine with ubuntu 7.10. 

Yesterday I did a fresh install with xubuntu 8.04, which failed. I can get it working with v6.04 and I then did the upgrade. But upon rebooting it crashed. I pressed caps-lock and the LED didn't light up on the keyboard.

Putting pci=noacpi into grub didn't work either.

Booting from the network install CD also caused the same failure. It appears to be when its says "* Starting Hardware Abstraction Layer (HALD)" but I'm not sure if that's the actual point of failure.

I can get access to the computer in Recovery Mode, but that's a bit useless.

Can anyone help?

K.

---

### Post by dan_hurst on 2008-05-09
I tried the same thing on my EPIA SP.  Couldn't get it to boot with 8.04 unless I removed the NovaT500 PCI tuner card.

I went back to Gutsy but couldn't get the hw decoders to work, no myth tv for me :-(

Let me know if you get it working, I'll keep you posted but as its good weather here at the moment I think I'll be putting this project off a bit until the weather gets bad again :)

---

