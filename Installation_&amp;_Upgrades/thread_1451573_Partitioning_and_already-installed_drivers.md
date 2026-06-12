---
title: "Partitioning and already-installed drivers"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Tacozmeister on 2010-04-10
Hello all, I was just thinking about partitioning my harddrive for Ubuntu. I already installed Ubuntu on my other computer, and I saw it gives you that option automatically, but I wanted to know a few things before I install it on this computer.

1) Can I use my drivers from my Windows Vista drive to be for Ubuntu? (Specifically here, my wireless). 

2) How do you select which hard-drive/operating system you are on? Does that show up automatically?

My computer information: (Just in case that makes any difference) x86 64-bit currently,
Windows Vista currently,
Wireless adapter - D-Link WUA-1340
All requirements are met for Ubuntu, if not surpassed greatly. 

Thank you!

---

### Post by emanuel.b on 2010-04-10
Hi!

As far as I know, the only way you could get Windows drivers working on Ubuntu, is through Ndiswrapper. It allows you to install windows drivers for your wireless card.

As for the startup option, the GRUB bootloader does give you a choice between OSs at startup, but Ubuntu will be default.

Hope that helped!

---

### Post by Tacozmeister on 2010-04-10
Sorry to ask, but what's a Grub Bootloader? Is that something automatic on my drive or something that I have to download?

---

### Post by emanuel.b on 2010-04-11
The GRUB bootloader is the software that handles the most of the pre OS tasks when you start up the computer. It is included with Ubuntu. Mostly what it does is when you install more than one operating system, like Windows and Ubuntu, it lets you choose between them, runs a bunch of processes, then hands it off to whichever os you chose. When you install Ubuntu, you have the choice of not installing the GRUB bootloader. Although I haven't had time to experiment with this, I'm pretty sure that if you choose not to, it let's the Windows bootloader take over (as of Vista, it was the Longhorn bootloader.)

---

### Post by Tacozmeister on 2010-04-11
Ohhh, that's why when I googled it it had the picture of a goat (Knockoff of a bull's horn is a goat..), but okay, thank you. I guess I should be good if I install Ubuntu on this machine then. Thank you!

---

### Post by emanuel.b on 2010-04-11
You're welcome! Always happy to help! (even if it's just to convey information.)

---

