---
title: "RHEL 5 server hate Unbuntu 7.04"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Decepticon22 on 2007-04-30
I am trying to setup a RHEL 5 dual boot with Unbuntu 7.04. and it seems neither OS like the idea. When I tried to install and use the RHEL5 grub after I installed Unbuntu, it would not find the proper Unbuntu partition even after I told it where to look in the RHEL 5 pre-install. All I got when I tried to boot to unbuntu was an error saying : Error 23: Error while parsing number. I figured this was a case where I just needed to change the order of the naming schema of grub, so I tried going in the proper order,

/dev/fd0 (fd0)
/dev/hda (hd0)
/dev/hdb2 (hd1,1)
/dev/hda3 (hd0,2)

And so forth, but to not avail. RHEL 5’s grub just didn’t want to allow an Unbuntu boot. I then tried reinstalling Unbuntu and let it's grub take over, however, this time I got a different error: Error 13: Invalid executable or unsupported format. 

I’m start to wonder if there is a conspiracy here; if maybe Unbuntu is too fresh and funky for Ole’ Redhats taste or if Redhat is going the way of the Eeevil empire, either way, any help would be deeply appreciated.

---

