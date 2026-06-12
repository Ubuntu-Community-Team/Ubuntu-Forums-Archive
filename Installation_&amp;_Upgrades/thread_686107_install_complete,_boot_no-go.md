---
title: "install complete, boot no-go"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by notascoolasu on 2008-02-02
ditched xp on my desktop PC, clean install of ubuntu.

tried to install desktop edition 7.10 x86 32-bit.  booted from disk, chose "start or install ubuntu" and get a screen with ubuntu logo and orange status bar.  bar gets to about 80%, stops, hangs indefinitely.

tried to install desktop edition 7.10 ditto except i downloaded the "alternate" desktop CD, which got me through all the installation (text-based.)  after installation, it spit out the disk and said "now it's time to boot your system for the first time..."  boots to same screen, gets to 80%, hangs indefinitely.

what am i missing?  hardware problem?

---

### Post by Partyboi2 on 2008-02-02
try without the spash screen.
when booting press ESC to get to grub menu. highlight the kernel you going to boot into and press "e" then highlight the kernel line again and press "e" then look for the word "splash" and change it to ```
nosplash
``` press enter then press "b" to boot. If this works you will need to add it to grub menu.lst to make it perm.

---

### Post by notascoolasu on 2008-02-03
thanks so far partyboi

alright - without the splash i can see it gets as far as "Starting Common Unix Printing System: cupsd" and then stops.  

found the following older threads, but no resolution to either:

[http://ubuntuforums.org/showthread.php?t=255870](http://ubuntuforums.org/showthread.php?t=255870)
[http://ubuntuforums.org/showthread.php?t=279294](http://ubuntuforums.org/showthread.php?t=279294)

any ideas?

i should say, i do not particularly care if i can print at all from my desktop (though it would be nice).  mainly i use my desktop for word processing, internet and movies/music, and haven't had it connected to a printer for months...printer-sharing is something i can absolutely do without until i find a fix.  is there a way to bypass CUPS loading during startup?  i can always print from my windows laptop which runs openoffice.  not sure how vital CUPS is for anything but print/printer sharing?

also, i didn't configure dhcp during installation...if that is of any relevance?  figured i'd configure it later - my desktop has been 'quarantined' from my network and entirely offline for awhile now, hence the format and decision to play around with linux/abandon xp (plus vista on my laptop has been the bane of my existence for months now...)  i can get it back on the network and reinstall, but that'll be tomorrow, i think i give in for tonight.

if it can't be resolved, is this likely to be a problem i encounter with other distributions?  i'd really like ubuntu, but i'm definitely NOT going back to windows for my PC, so would try other distros if it's likely to get me at least into a workable OS.

---

