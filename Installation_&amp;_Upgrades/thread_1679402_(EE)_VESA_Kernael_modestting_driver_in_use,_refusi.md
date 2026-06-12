---
title: "(EE) VESA: Kernael modestting driver in use, refusing to load"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by tptmrk on 2011-01-31
I just updated to 10.04 (forgot about the many hours I spent on this problem due to the last upgrade).

On boot I get these errors:
(EE) VESA: Kernael modestting driver in use, refusing to load
(EE) No devices detected.

I think the problem is (this started with 9.10)
lspci | grep VGA
**00:02.0** VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I followed at least a dozen blogs and threads last time and tried lots of stuff eventually disabling Compiz (checked and it's still off according to preferences menu), did something with a grub booting setting to change quiet splash to nomodeset, and finally it worked without the screen freezing when I did post #3 here:
[http://ubuntuforums.org/showthread.php?t=1307413&highlight=82845G%2FGL]("http://ubuntuforums.org/showthread.php?t=1307413&highlight=82845G%2FGL")

I forgot all about this when upgrading and it asked me about xconf.org and I didn't what it did so I told it to upgrade. I've changed it back like the post above, but it still freezes up randomly. I can't figure out how to do the nomodeset thing because the grub file doesn't seem to be in the same place as the post I saved from last time (#50 here)
[http://ubuntuforums.org/showthread.php?t=1347430&highlight=9.10+freeze&page=5](http://ubuntuforums.org/showthread.php?t=1347430&highlight=9.10+freeze&page=5)

I've been poking around for hours and rebooting and messing around, but I'm just really lost. I had also saved this link and the last post seems to say the problem may go away by upgrading to 10.10 - worth a try? 
[http://janvandevoort.wordpress.com/2010/03/27/ubuntu-9-10-with-vga-intel-82845gglbrookdale-gge/](http://janvandevoort.wordpress.com/2010/03/27/ubuntu-9-10-with-vga-intel-82845gglbrookdale-gge/)
If so, it doesn't show up as an option on Update Manager but other websites say it's a "stable release" so how would I upgrade.

Any help here? Thanks!!!

---

### Post by tptmrk on 2011-02-01
[B](EE) VESA: Kernel modesetting driver in use, refusing to load (correct spelling!)
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]Oh yeah, there's a file names ***xorg.conf~*** that was there after the upgrade. It doesn't show up when I run "sudo nautilus", though.

***Anybody know how to at least try changing "quiet splash" to "nomodeset" in 10.04?*** I found something that said how to do it temporarily at startup, but ctrl-X wouldn't restart so it didn't work for me. This is the only other thing I know to try right now unless someone has another idea.[/SIZE][/FONT]
[/B]

---

