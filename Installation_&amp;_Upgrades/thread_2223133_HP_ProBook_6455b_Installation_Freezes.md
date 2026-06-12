---
title: "HP ProBook 6455b Installation Freezes"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by bruce-hyatt on 2014-05-09
I just want to relate my difficulty installing 12.04 on an HP ProBook 6455b laptop, in case it might help someone in the future. I had a hard time finding any relevant information on the internet. I should have done this sooner when the details were fresher in my mind, but....

When I tried to install Ubuntu 12.04 on this laptop it would freeze at, I believe, the preparing-to-install stage. The circular icon just sat there rotating indefinitely. After much Googling, it appeared it was related to the UEFI setting in the BIOS. This laptop was apparently a corporate-owned device and had a password-protected BIOS. As I recall, changing the UEFI setting helped - I think I had to confirm that I wanted to delete the administrative password - but that didn't completely solve it and I may have switched the UEFI setting back to its original state after deleting the password.

The other setting that helped solve it was to uncheck the box for installing 3rd-party software.

---

