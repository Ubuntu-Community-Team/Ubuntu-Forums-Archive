---
title: "[SOLVED] backup of / parition"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-03-02
hi

my root (/) partition is on /dev/sdb2 (30GB)

/dev/sdb1 is a blank ext3 formatted partition for backups (50GB).

/home is mounted on /dev/sda1.

now, i would like to backup my root partition (excluding /home) from time to time however I am unsure as to the best and fastest way to do this.

options I'm thinking of are:
dd
rsync

can someone please suggest the best and fastest most efficient way to do this, when I should do it, and also please include how I would restore from the backup.

thanks.

---

### Post by housam on 2008-03-02
use this guide [[COLOR="Red"]_https://help.ubuntu.com/community/BackupYourSystem_[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by keratos on 2008-03-02
ah!

just visited the link (thank you very much) and this is what I seek.

I tried searching the forums for "backup AND root" and "backup AND partition" but your link did not come up.

Anyway, good to go now.

Cheers

---

### Post by housam on 2008-03-02
You can find useful things here [[COLOR="red"]_https://help.ubuntu.com/community/TitleIndex#M_[/COLOR]]("https://help.ubuntu.com/community/TitleIndex#M")

---

### Post by keratos on 2008-03-02
> **housam said:**
> You can find useful things here [[COLOR="red"]_https://help.ubuntu.com/community/TitleIndex#M_[/COLOR]]("https://help.ubuntu.com/community/TitleIndex#M")

cheers!

---

### Post by zvacet on 2008-03-02
I´m just curious why do you want to back up root,bacause I suppose that you have CD.Only thing on root you want to save is var/cache/apt/archives and you can do that with [AptonCD.](http://aptoncd.sourceforge.net/)No need to download it from site,you have it in synaptic.But this is just sugesstion,you will do it your way.

---

### Post by keratos on 2008-03-03
> **zvacet said:**
> I´m just curious why do you want to back up root,bacause I suppose that you have CD.Only thing on root you want to save is var/cache/apt/archives and you can do that with [AptonCD.](http://aptoncd.sourceforge.net/)No need to download it from site,you have it in synaptic.But this is just sugesstion,you will do it your way.

Incorrect!

What about my patch updates to Glib and C++ toolchain &  libraries,
What about my tailored kernel rebuild and  module updates,
What about my system config under /etc/...
What about my optional (non-distro included) non repos stuff, like /opt/...
so on and so on...

I have all these system tailoring plus more.

So, the "only thing on root to save is.." much more than you think !!

:-)

---

