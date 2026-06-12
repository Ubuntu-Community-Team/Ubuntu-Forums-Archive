---
title: "Is it time for a clean install of Ubuntu 10.10?"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by boroborolama on 2011-01-26
I've been running Ubuntu 10.04 Lucid on my Sony VAIO laptop for about six months.  In that time, I've gone from complete ignorance of Linux to writing shell scripts, ssh tunnelling, and otherwise utilizing the power of the command line.  For what it's worth, I also have a shiny [FONT=Courier New]Gnome[/FONT] desktop that remains perennially empty.  (Icons?!)

Now, I am beginning to understand that I installed Lucid, which boots through [FONT=Courier New]wubi[/FONT] on Windows 7 that came preloaded on this computer.  I have to choose Ubuntu everytime I boot.  It's not the default, either.  Moreover, the hard drive is partitioned to leave the lion's share of the space for Windows, which I never use.

I am now at the point where I'm ready to

[LIST=1]
[*]Download Ubuntu 10.10 Maverick on a USB stick.
[*]Backup my home directory tree on said stick.
[*]Reformat the hard drive.
[*]Install Maverick on the "new" Linux laptop.
[/LIST]
But, I'm a bit apprehensive.
My questions.

[LIST=1]
[*]Should I install 10.10 directly, or instead install 10.04 (because of the LTS)?
[*]Is there a way to automatically remember what software I have from the repositories that isn't standard with the install?
[*]Is there some reason that I shouldn't wipe Windows from the machine (this is irreversible)?
[/LIST]
Thanks in advance for any advice.

---

### Post by IWantFroyo on 2011-01-26
Boot into Windows and make a backup on an external hard drive (you probably could do cd, but I don't trust that). Then try 10.10 Maverick. The only reason to fall back to LTS is if something doesn't work. Like Maverick is known to have acpi issues, but these can be fixed with pci=noacpi. Enjoy whatever Ubuntu you decide! Also, you can upgrade without deleting, but that won't overwrite your windows. If you would rather keep your files there along with windows, alt-f2->settings->show stable releases. Then select 10.10, and go read a book.

---

