---
title: "installing graphics driver in 9.10"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by MilanT on 2010-07-08
I was trying to install drivers for my ati radeon 9550 and when i typed in the terminal this:
sudo apt-get update
sudo apt-get install libgl
i got:
 W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
a posle ove druge: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgl
how do i add this repo to sources list and how do i install the public key?
please correct my question if it is wrongly asked, i am a begginer with ubuntu:)

---

### Post by Mark Phelps on 2010-07-08
> **MilanT said:**
> I was trying to install drivers for my ati radeon 9550

There are no ATI drivers that will work with your card and Ubuntu 9.10. You will have to use the open-source drivers -- and those are automatically installed by default when you install the OS.

So, don't try to force a driver install.  It will only trash your display and you'll have to end up booting into a console to remove them.

---

