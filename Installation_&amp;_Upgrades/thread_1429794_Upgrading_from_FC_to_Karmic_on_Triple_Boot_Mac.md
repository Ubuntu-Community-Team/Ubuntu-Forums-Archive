---
title: "Upgrading from FC to Karmic on Triple Boot Mac"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by ampermc on 2010-03-14
I have a Core 2 Duo iMac that I had set up for triple boot using Fedora Core (probably FC8 )and GRUB, Windows XP Pro, and Mac OS X v10.5. Some time ago, I had to blow out and reinstall my Windows installation because it had developed errors, but this also blew out my GRUB, leaving the Fedora install non-bootable. Since I never really used FC on this machine much, I didn't worry.

Lately, I've acquired an hp Mini 110, on which I'm running Linux Mint 8 (Helena), and I'd like to upgrade my FC partition on the iMac to Karmic, but when I run the installer, it won't let me use all of the existing Linux partition, instead wanting to resize it to accommodate both FC and Ubuntu.

How do I make the installer simply replace FC with Karmic, using the entire existing partition? I'm sure earlier versions of Linux that I've used had a simple "erase all Linux partitions and install" option, and the "Manual" option doesn't appear to read the existing partition information (I was too afraid to go any further).

I ended up quitting the installer, which put me into the Live CD environment, where I used the File Browser to "Format..." the Linux partition, but when I went back to the installer, I ran into the same problem, and it didn't seem to matter if I unmounted the existing partitions or not.

---

### Post by ampermc on 2010-03-14
OK, I figured it out. I was afraid to proceed with "Manual" partitioning, because when you select "Manual", it makes the partition table map bar all one color. When you then click "Forward", it reads the existing partition table, and then allows you to make the necessary changes.

Now I just need to figure out how to recover my bootloader, since I screwed it up during the install. When I originally did this a couple of years ago, I figured out how to do this with GRUB instead of rEFIt. This time, I put the bootloader on the Linux partition, and GRUB isn't coming up, just displaying the Windows error "Error Loading Operating System". I'm pretty sure I can figure that part out, but just in case, feel free to offer advice.

---

### Post by ampermc on 2010-03-14
I gave up on trying to re-create my GRUB loader and just threw rEFIt on the machine. I don't feel like spending any more time screwing with this...

---

