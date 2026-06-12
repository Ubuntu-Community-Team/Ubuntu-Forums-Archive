---
title: "Could the final iso be released on jigdo for early seeding?"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by martalli on 2008-04-22
I have read that jigdo could be used to update ISOs, such as installation ISO on debian testing and unstable.  Is it possible to do this with the release candidate ISO?  For instance, when the final release is out, could I download the jigdo file and use the release candidate ISO as the basis, would it fix the ISO, or would some similar strategy work?  

I actually do not need the ISO's so quickly as much as I would just like to have a copy ready quickly so that I could start seeding sooner.  There must be a way to utilize jigdo for this purpose.

Thanks for any thoughts.

Bryan

---

### Post by martalli on 2008-04-23
As I started doing this, I have made three observations.  The first is that there is no "desktop" jigsaw download.  The second is that the jigdo template for the alternate CD is 5.1 MB.  The final observation is that the jigdo template file for the DVD is 1.5 GB.  I am guessing that the livecd portion of the desktop cd is essentially a binary blob that is incompatible with jigdo is some basic fashion, and that the DVD template essentially contains a template + binary blob in its massive 1.5 GB.

Thus, my plan for a quick update of my ISOs to the finaly hardy release is really only going to work well with the alternate (and server) CDs...I wonder if I could do this all fro the same directory, and thus avoid downloading the entire ubuntu base for both server, ubuntu, xubuntu, and kubuntu, but run jigdo once at a time in the same directory and only download the extra bits, reassembling the ISOs one at a time from the constituent packages.

---

