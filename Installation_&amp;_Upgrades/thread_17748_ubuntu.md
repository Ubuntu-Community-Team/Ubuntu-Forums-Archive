---
title: "ubuntu"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by goose on 2005-03-02
Hi Everybody,

First off, Ubuntu is quite great.  I'm a long time Debian user (7 years, has it been that long? :), and I'm really glad the there is a well supported distro that uses the very intelligent package backing of .debs.  Sweet.  Glad to join up with y'all!

Second, I've always been a KDE person, but Ubuntu uses Gnome.  Catch is, my girlfriend, a gnome lover, want's to keep gnome, yet I want kde.  So, I switched on the universe package list and installed all the KDE stuff... But, funny thing is my sound doesn't work at ALL in KDE, but it works fine in gnome.  Real pisser.  I've been doing a lot of searching around these forums for some sort of help, but can't really find it.  On my previous debian installation, I had both desktops running no problem, so I imagine there is something I've missed, but darned if I can find it.

Everytime I log into kde, I get an error saying that the sound core couldn't start up, so it would use the null device instead.  No matter what I play with in the KDE control gui, nothing makes the sound work.  I always get the same errors, /dev/dsp is permission denied or something similar to the log in error.  I tried something quirky, and chmodded /dev/dsp to 666, then sound worked just fine.  But of course, on a reboot, it was back to no sound.

Hope that's enough to get started on debuggning.
Thanks for all and any help out there!

Andrew Gosline, aka Goose

ps: If I shouldn't be posting here, moderators please move this to the proper location.

---

### Post by JmSchanck on 2005-03-02
I dont know if im completely off here but try:

```
groups username
``` 

check to see if it says audio. also, what are the file permisions set to before you change them?

---

### Post by goose on 2005-03-03
Hey, 
Thanks so much.  I must have forgotten about groups, cause when I added myself to the audio group, the sound works now.  I'm getting loads of sounds, nicely, in KDE.  However, it only works with my analog line out:

I'm using a soundblaster live with a hoontech daughter card that has an optical out on it.  I use this to connect to my MiniDisc recorder, so,  the optical channel won't output sound at the moment.  It used to work just fine with my old debian install.  Actually, it worked right out of the box with the old oss drivers.  Now, however, with ubuntu, I've played around for 2 hours looking for the right checkboxes in the volume control/mixer, both the alsa and oss versions.  Anybody know I can enable ouput on the digital cannel?  Anybody know of any info where I could look?

thanks,
goose

---

