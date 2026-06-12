---
title: "upgrade to 11.10 lost email in Evolution"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by accodata on 2012-01-17
Hi Folks,
I upgraded through the terminal from 11.04 to 11.10 yesterday. I have opened email to find all my emails are no longer there.
I only back my system up with Du Juva, (I think the spelling is)

is there anyway to find my emails.

and as I am pretty thick, and will need simple easy intructions.

Tracey

---

### Post by saneearth on 2012-01-17
At some point in time .evolution was moved to .config in the Evolution folder in the newer release. I am not positive that it occured in this release, but it may have. If this is the case your emails are in the .evolution folder which would still be in your hidden folders in /home/user if you did not format the drive, which you didn't apparently. I would copy both folders elsewhere first, but then delete the contents of the Evolution folder in .config and copy the contents of the .evolution folder into the folder in .config. I caution this may not be the "right" way necessarily to do this, but it is the way I do things. Works for me "most" of the time, thus the back up of the folders.

---

