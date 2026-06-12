---
title: "Remaster for ubuntu 9.10 help"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by vsk_ram21 on 2009-12-09
I have dual booted Ubuntu 9.10 and Fedora 12 and using Grub 2..
i have stablised and ready for remaster my system suppose if i remaster Ubuntu will the grub settings be reflected there or it will be modified...

i basically doing remastering in order to encorage my friends to use Ubuntu and they already have windows installed so if they install remastered version of ubuntu 9.10 will that show their windows partition or will that be configured manually after installation..?

---

### Post by tommcd on 2009-12-09
> **vsk_ram21 said:**
> 
i basically doing remastering in order to encorage my friends to use Ubuntu and they already have windows installed so if they install remastered version of ubuntu 9.10 will that show their windows partition or will that be configured manually after installation..?
I don't think you could count on a remastered version of Ubuntu detecting Windows any better than a standard Ubuntu 9.10 install.
The only advantage I can see to using a remastered version of Ubuntu (as far as detecting Windows is concerned anyway) is that it would incorporate the latest grub2 updates that have been added since 9.10 was released. With a standard Ubuntu install, once your friends get the updates, they will have the latest grub2 as well. They just need to run:
```
sudo update-grub
```
to update the grub.cfg. The update-grub command is run automatically whenever an update for grub is done anyway, so it is not even necessary to run that command when grub is updated.
Also, when the next grub2 update comes along (there have been several already) your remastered version will be out of date. So just have your friends do a regular Ubuntu 9.10 install.

---

