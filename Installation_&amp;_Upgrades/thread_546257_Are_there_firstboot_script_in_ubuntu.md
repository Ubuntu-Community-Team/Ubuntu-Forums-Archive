---
title: "Are there firstboot script in ubuntu?"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2007-09-08
Hi,
I am always using pxe to deploy the Xubuntu to new computer system.
I am wondering are there firstboot script in ubuntu system?
If yes, where is the script located?

---

### Post by Herman on 2007-09-08
Hello bbmak, I'm not sure I understand perfectly what you mean, sorry if I am guessing wrong. 
I think you might mean like an OEM install, where it lets the new user choose their own username and password the first time they boot their new computer.
That's an option in the 'Alternate CD installer, and I'm not sure if the 'Desktop' (Live/Install CD), can do that too yet or not.
Is this waht you want,
> **Text mode install for manufacturers**. This is for computers that are being set up in a factory or a store with Ubuntu pre-installed.  During the OEM installation, you set an OEM password. You then log in with the username 'oem' and the password that you set. After you shut down, it will be set up to allow the new owner to set up their own new user account on boot-up.  For an Official OEM Installer Overview, [Click Here]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview").
Regards, Herman :)

---

### Post by dfreer on 2007-09-08
As for a "firstboot script", perhaps you are looking to execute a script at startup?

---

### Post by bbmak on 2007-09-08
Herman:
not the username and password.
Because i am deploying the Ubuntu from server, so I already did the username & password with a pre-configurated file.

What i really mean is what "dfreer" said.
I want a script to run as only the first time login of xubuntu.

---

