---
title: "midway though 10.4 upgrade then lost power!"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by dkruitz on 2010-05-15
Help!  I was midway through my 10.4 upgrade from 9.1 via package manager and we lost power when a storm rolled in.    Of course now it won't boot to the HD.  I tried the 10.4 live cd and it says there's already a 10.4 installation on there, I can't seem to get the boot:rescue option while booting, might try a different monitor.  Is there a utility I can try while on the live cd desktop by chance?

Stuck and hating it.  Oh, I'm making another copy of my files to a windows box, I did a simple backup before the upgrade, but I don't trust restoring all my stuff from that just yet as it seems a little klunky.  If worse comes to worse, I can just wipe and reload the whole thing I suppose but I really don't want to.

---

### Post by bumanie on 2010-05-15
As far as I know, power failure part way through an upgrade = reinstall from scratch - sorry for the bad news. Hope someone knows a trick that I don't know to help you out.

---

### Post by dkruitz on 2010-05-15
I was afraid of that.

I *was *able to get to the boot options screen, now conveniently hidden from view....
I tried the rescue option and it seems to indicate that there may be bad sectors on the disk, I'm now running SeaTools from Seagate to see if that's the case.

I've been able to copy all data off to a windows pc, *except *for the .Thunderbird folder is it has an "x" on it indicating I don't have permissions via the live cd - how do I get around that?

Thanks!
Dan

---

### Post by dkruitz on 2010-05-16
Success!
sudo chown ubuntu .Thunderbird 
is the command I needed to open up any of the folders I could not access via the live cd.

I copied off all my content to my other pc and have it reloaded with 10.4 now.  Sound was working prior to me applying 104 updates, but that's for another day....

---

