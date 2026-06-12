---
title: "Broken Kubuntu Interpid installation from USB stick"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MoridinBG on 2008-07-13
As I am on CDless laptop I did the same thing I am doing since 7.04 - made a installer USB with the script from isotostick.sh from the Community wiki.
I am using the alternate x86 installer image.

The stick has to be manually mounted on /cdrom before the installer searches for CD-ROM device, otherwise the install fails.
At some point in the begining the installer complains of not being able to find /cdrom/dists/stable, which is easely solved by mv-ing /cdrom/dists/interpid to /cdrom/dists/stable.

Then it goes without glitches up to the point where it should install the Base system. There it crashes because "Release name was not found", or something like that for which I hadn't found a solution yet.

---

