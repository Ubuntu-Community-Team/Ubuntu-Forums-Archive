---
title: "Recover OEM account"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by t_anjan on 2007-03-13
I made an 'alternate' CD install of Edgy. At the end of the installation, the installer told me that a default 'oem' user account would be created and that I had to run 'sudo oem-config-prepare' to setup a user account of my choice.

When I ran that command from the terminal and rebooted, I found that the 'oem' account hadn't been converted into my user account, but it was deleted. I had some important files in the home folder of the oem account. Is there any way I can retrieve these files?

The installer should be clearer

---

### Post by taurus on 2007-03-13
You are not supposed to use oem account as your personal account.  It says on the screen during the installing that you need to run that command as soon you first log in to create an actual account for you to use.  Once /home/oem is deleted, all your files are gone too.

---

### Post by t_anjan on 2007-03-13
> **taurus said:**
>  you need to run that command as soon you first log in 

I'm pretty sure that is not how it is worded in the installer. It was more on the lines of "once the system is configured as necessary".

Anyway, Thanks for the info. What's gone is gone.:(

---

