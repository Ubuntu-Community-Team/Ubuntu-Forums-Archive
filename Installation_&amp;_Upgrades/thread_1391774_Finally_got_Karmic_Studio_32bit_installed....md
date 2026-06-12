---
title: "Finally got Karmic Studio 32bit installed..."
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by mango42 on 2010-01-27
...on an old thinkpad T43...and it's gorgeous! **Thank you so much all you hardworking vocational people** ;-)

But (there's always a caveat with any software, isn't there?) at present I have to manually boot from Grub command line because when I ran the installation (ubuntustudio-9.10-alternate-i386.iso using usb-creator, no recognised net connection) it loaded all the software (which appears to work as intended - even JACK worked first time!) but ended with two error messages:- 'software installation failed' and 'Grub installation failed'.

Consequently, there's no GRUB entry for this partition. I have tried replicating the manual commands in grub.cfg and in my (9.04 vanilla) other partition's menu.lst but really I'm fumbling in the dark, not being a programmer.

Dare I just issue ```
sudo update-grub
``` from my lovely new anechoic Koala, or is there far more to repairing this error than I can cope with unaided? (Reading all the confusion surrounding docs on Grub v Grub 2 just can't compete with musical composition - sorry, but they just make me crossed-eyed and cross-brained!)

Once again, a very BIG thank you for all the hard work put into this most gorgeous Ubuntu offering yet seen.

---

