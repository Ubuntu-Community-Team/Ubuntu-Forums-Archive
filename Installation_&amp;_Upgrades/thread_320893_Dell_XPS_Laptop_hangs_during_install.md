---
title: "Dell XPS Laptop hangs during install"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by grandnagel on 2006-12-18
OK, I have to boot using Safe mode to begin with...  When I get into the installer, it runs through great until "Installing System" "Copying Files" "72%"  ...  Then the installer and the game I'm playing lock up ...  Theres an ATI Mobility Radeon 9600 in the Dell and I  think it may be at fault...  Either that or the CD player is going out on me...  Doing a BOOT_DEBUG=2 on it shows that there are a significant numbers of read failures to at least one spot on the CD.  

I had originally started out burning onto a CD-RW at 4x but finally settled on a CD-R (Memorex, brand spanking new from the store) after the CD-RW immediately proved flawed when trying to boot it...  The CD-R checks out in the disk test though (I'm running it again as I type this on my windows box) 

Since I'm using safe mode to boot the box, and the installer likely isn't using safe mode, maybe someone could clue me in to how to know whats really going on, or even if I should bother with 6.10 any further for this Dell Laptop... ??  I've seen a reference to a text based installer which permits more customized installs, but with 12 years in software development, I've never had to use a linux dist, so, I was hoping to ease into it instead of heading for Alaska and jumping in the the icy head waters brain first.

Anyway, suggestions welcome, even if it's this dist is really not suitable for that box...  

It's a Dell XPS first generation laptop, w/ 2gig ram, 80 gig drive, partitioned with 20 gigs of ext3 formatted partition for ubuntu (broken into 2 parts  15GB(root) and 2GB (swap) ) and 58 gigs for XP.  running a 3.4 ghz dual proc with ATI radeon 9600 mobility video.  

The file check I've been running is more than 1/2 way through and not presenting anything in the way of error...  Going for a smoke ...  Got back from the smoke... Theres a blue txt message about Checking integrity now and we're at about 75%.

Would it be more 'wise' to try and install this into a VM? 99%... done   0 checksums failed.

Thx in advance.

D. ](*,)

---

