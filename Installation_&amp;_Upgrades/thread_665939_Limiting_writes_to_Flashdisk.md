---
title: "Limiting writes to Flashdisk"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by martin.demare on 2008-01-12
I installed Ubuntu a year ago on an internal flash disk (using a CF to IDE adapter). I was worried that the flash disk would not be able to handle all the writes, so I of course chose NOT to use a swap-partition. I also did some other more elaborate changes described last in the post.

I would appreciate if someone with more knowledge can tell me what adjustments are necessary in order to save the CF-card. If adjustments are necessary I  think there should be a separate option when installing since laptops with flash disks probably will grow more and more common
/Martin


PS. MY EXPERIMENTAL SOLUTION:
My main objective when installing Ubuntu 6.10 on the internal CF card was to reduce the noise since the computer acted as server and was always on. In order to limit the number of writes to the card I mounted a TmpFS partition over the root using UnionFS, at start up. At shut down I merged back all changes with a snap merge script. Later I changed the system making it optional to merge back system changes.

Unforeseen benefits with the experimental system::
What I discovered was that I started to use the computer differently. On my other computers I am always very careful making changes to the system, wanting to keep the system as "clean" as possible. On this computer however I started experimenting a lot since I knew that I could always discard the changes I had made to the system. 
Later I added another CF-card (without UnionFS overlay) where I could save documents etc. This proved to be at  very robust configuration and I think, for example, it coped quite well with power loss, not giving me a bunch of warnings when rebooting.

---

