---
title: "Best way to install minimal server with full-drive encryption?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by quinthar on 2008-05-23
What's the best way to install a completely bare-bones server with full-drive encryption (aka, "encrypted LVM")?

In the past I've used the alternate install CD for a desktop system with full-drive encryption; is there some way to use the same CD to install a stripped-down (non-GUI) server?

Ideally I'd like the resulting system to be as clean as a "debootstrap" image -- essentially nothing installed except for the minimum required to install everything else.

Any ideas?  Thanks!

-david

PS: I'm not sure why this thread is labeled [kubuntu]; I meant [ubuntu]

---

### Post by Steve413z on 2008-05-23
the problem with using full disk encryption on a server, is that if the server ever reboots, you are going to need to re-enter the passphrase, or leave some kind of key (like a USB stick, or a smartcard) in the computer.  

If you want a minimalist server with a passphrase, the easiest way to do that is to use debian with the text installer (same text installer as ubuntu) but keep in mind you will always have to enter a passphrase on the computer (not over SSH, but at the physical terminal) to start it

if this server is going to be used for backing up other computers and that is why you want it encrypted, you should try to find a backup utility that will encrypt your backups, I like "duplicity" [http://duplicity.nongnu.org/](http://duplicity.nongnu.org/) (which is in the ubuntu repositories)

---

### Post by quinthar on 2008-05-23
Thanks for the quick reply!  Yes, I'm aware it'll need the password to be entered at the console at each boot (a necessary evil).  That's fine in my case as I have a bunch of servers and none will re-enter service after a crash without manual inspection anyway.

Good idea on just installing with the Debian text installer; I've never used that before but I'll give it a shot.  However, how different will the resulting system be from my Ubuntu 8.04 desktop machine?  (Obviously, it'll lack the desktop components, but I mean system libraries and such.)

Basically, I'm looking to minimize the differences between my development and deployment environments; given all development happens on Ubuntu 8.04, I'd like to deploy on Ubuntu 8.04 as well.

Thus is there any way to use the alternate install CD, set up encrypted LVM, and somehow "unselect" all but the bare essentials?  Thanks!

-david

---

### Post by zvacet on 2008-05-23
On the alternate CD you have option to install server,bot I don´t know if you can set up encrypted LVM.You can explore that option.

---

### Post by quinthar on 2008-05-23
zvacet -- Do you mean by pressing F4 and choosing "Install a command-line system" from the first boot menu?  If so, thanks for the tip!  I hadn't noticed that there before.  I'm installing it right now and the "encrypted LVM" option *is* present, so it's looking good.  Thanks!

---

