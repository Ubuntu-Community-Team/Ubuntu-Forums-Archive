---
title: "error at first restart after install"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by drswingingblades on 2010-12-25
Just reinstalled 10.10 to go down to the 32 bit version and I get this message at the first restart after ubuntu prompts to download necessary drivers 


Don't remember if I got it last time

This normal?

I/O error, dev sr0, sector 537XXX

xxx - as in there were A LOT of them

---

### Post by Rubi1200 on 2010-12-25
Can you boot into Ubuntu normally though?

See here for the error:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)

> 
[LIST]
[*]**I/O error after CD is ejected at end of install.**  In some cases, ejecting the CD at the end of installation will leave errors on the screen such as: 
[/LIST]

end_request: I/O error, dev sr0, sector 437628these  error messages indicate that the system is still trying to access some  files on the CD, and are harmless except that they obscure the message  asking the user to press Enter to reboot.  You can safely remove the CD  from the tray and press Enter at this point to reboot to your new Ubuntu  system.


---

