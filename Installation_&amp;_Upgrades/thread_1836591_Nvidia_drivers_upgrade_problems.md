---
title: "Nvidia drivers upgrade problems"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Jooon on 2011-08-31
Hi all.
Today i downloaded the new nvidia driver (280.13) in a .run file.
I have an old driver (173) and i need to upgrade it.

So, i removed the old driver with
apt-get --purge remove nvidia-*
i rebooted the system and executed the .run file.
It prompted an error saying that the Xserver was running and the installation closed.
I rebooted in safe mode (telinit 1) and re-executed the .run file.
Now it says that the installation cannot continue in telinit 1 (it should be at least level 3).
I executed the command
telinit 3
and the installation cannot go on because the Xserver is running.

I also checked if the old driver was removed correctly, but the packages nvidia-173, nvidia-common and nvidia-current still installed.

Any tips?
Jon


Ubuntu 11.04, x86, 32 bit
nvidia GeForce 7600GT


edit:
SOLVED -> ctrl+alt+F1 and stopped gdm. That was easy...

---

