---
title: "Suggestion for improved upgrade experience"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by gwm on 2009-11-16
I wanted to share my upgrade experience.

Karmic is awesome! Ubuntu is coming of age and in my eyes, looks very smart.

The upgrade experience is a bit daunting though. I think some work on the upgrade mechanism can save a huge amount of time and effort for the user.

I am busy upgrading two 32 bit machines from Hardy to Karmic.
I downloaded and burned the alternate cd (md5sum checked out etc.).
I inserted the cd and asked for an upgrade.
At one point I had to answer yes or no with a long, long explanation about which to choose. First I selected yes and the next time, I selected no.

It seemed to make no difference, either way, so why ask the question? I had to download a further 600 MiB of data in both cases!!! That means another 6 hours. Downloading the alternate cd is pointless since that takes about 7 hours. 6 + 7 = 13 whereas upgrading directly with Package Manager requires only 800 MiB and takes only 8 hours.

I only have a handful of packages that I have added from the repositories. How does that require 600 MiB? I can only guess that the upgrade process downloads all the dependencies over and over again.

Why not do a phased process.
1. Upgrade the release basics from the alternate cd.
2. Update the rest, one at a time, using a Package Manager type approach. As upgrade checks for dependencies, it may well find those files were installed by an earlier upgrade.
3. Intelligently work around asking the user questions that he can't answer. Asking the user whether upgrade should keep or replace a config file is not user friendly. Since he doesn't know the answer anyway, he has to guess.

Consider what this means, taking into account the many hours that an upgrade involves. Typically, one gets it going and then goes to bed. Tomorrow morning, when one checks to see how it went, we find it has stalled, asking "do you want to replace or keep file xxx,config?" How would I know? Since I didn't ever change the file I suppose I must say "replace". A few minutes later, it asks me the same thing for the next package. Man! I have to go to work! I can't now baby sit the upgrade through each package that I have installed (I'm stressing). So off I go to work and I only get to complete the upgrade when I get home tonight, which about 24 hours after starting the process.

Couldn't the upgrade determine how to handle the config files for itself? That really involves some good, intelligent coding and somehow making space on the alternate cd, for the various releases of the original config files from past releases of all the trillions of packages (perhaps one could get away with lists of checksums or include the actual files in dedicated folders in the repositories).

The most serious problem is when it comes to upgrading Grub. Usually an upgrade of the kernel reads the settings in menu.lst adds the new kernel to the top of the list and removes the oldest one below. I selected "keep" while upgrading and that meant that I couldn't boot. Oh well, fetch out alternate cd, boot into maintenance mode and find the correct names for the kernel images. Then oh dear! Gedit isn't available and I haven't used a line editor for over 20 years (about the time that Unix was still being invented), so I can't even remember what they are called on this system, let alone how to use them.

Couldn't this also be overcome by some carefully thought out programming.
I know! Cooking up nice pretty make files is a pain for a technical programmer but it is the package's first interface with it's users and is therefore very important.

---

