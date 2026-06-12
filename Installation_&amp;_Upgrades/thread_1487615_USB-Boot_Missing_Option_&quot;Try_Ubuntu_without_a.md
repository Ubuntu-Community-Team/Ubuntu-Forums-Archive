---
title: "USB-Boot: Missing Option: &quot;Try Ubuntu without any change to your computer&quot;"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by MartinSt on 2010-05-19
Hello everyone,

I have generated a bootable USB-Stick with the application "Startup Disk Creator" from the file "ubuntu-10.04-desktop-i386.iso".
When I boot from the stick, the option "Install Ubuntu" is shown but I am missing the option "Try Ubuntu without any change to your computer".

According to [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes) this should only happen when a computer has less than 256 MB of RAM, mine has 2 GB.
When I boot from a burned CD (same iso-file) the missing option is shown.

Please help me to run the live version also from a USB-Stick.

---

### Post by darkod on 2010-05-19
In 10.04 they have changed the menus a bit. When it starts booting and the purple image is shown, you can press any key to get a menu displayed. Try that.

---

### Post by MartinSt on 2010-05-19
I can bring up the menu and I can select "Install Ubuntu" or "Check CD..." and so on but there is no option to run a graphical live Ubuntu.

---

### Post by MartinSt on 2010-05-20
Has anyone made a bootable USB stick with Ubuntu 10.04 and is able to use it as a live-OS?
I want to know if it is a problem with my soft- or hardware or a general bug/incapacity.

Thanks for your response
Martin

---

### Post by MartinSt on 2010-05-21
I dont know why but it works now.
I did exactly the same as two times before and with the third time trying suddenly the entry to "Try Ubuntu without installing" is shown. Weird.

---

### Post by wilee-nilee on 2010-05-21
> **MartinSt said:**
> Has anyone made a bootable USB stick with Ubuntu 10.04 and is able to use it as a live-OS?
I want to know if it is a problem with my soft- or hardware or a general bug/incapacity.

Thanks for your response
Martin

I type this from my 16 gig thumb fully installed Lucid. If you decide to do a full install on a thumb make sure you put grub in the MBR of the thumb. Also a fully installed thumb isn't really considered portable, although it runs on the 3 different computers I own which are all very different setups. A ISO loaded thumb with persistence is considered portable, but has it's own limitations. There are 3 main thumb-loaders used that have gui's ask if you need more information.

---

