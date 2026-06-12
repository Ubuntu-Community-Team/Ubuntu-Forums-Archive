---
title: "Preinstalling Ubuntu"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by redsoxreed on 2008-11-21
Hi.  I want to sell a pc with a clean install of Ubuntu on it.  However, when you install Ubuntu, it makes you set up the users and passwords before the installation.  Is there a way to install the base system and then set up the users and passwords later?

---

### Post by Arseny92 on 2008-11-21
> **redsoxreed said:**
> Hi.  I want to sell a pc with a clean install of Ubuntu on it.  However, when you install Ubuntu, it makes you set up the users and passwords before the installation.  Is there a way to install the base system and then set up the users and passwords later?
Yes, there is a way to do that. Boot from the Ubuntu (Kubuntu, Xubuntu, Edubuntu, Mythubuntu - ubuntu is not important, all variants) LiveCD, open the additional options by pressing F4 and choose OEM install mode. Then the installer will start with OEM support. Follow the instructions. At the stage where you provide username and password you will see inactive username/password fields (with the text "oem (temporary user)"). Continue, install and reboot. You will then be logged in to GNOME (or into the desktop environment of the corresponding variant) with the temporary user **oem** . Configure the system. Then launch the icon on the desktop that says "prepare to oem shipping", or something (I don't know the exact name in English of this icon, since I installed a russian version of the system). A box will appear, saying that the last configuration process will take place after reboot. Do not reboot the computer after launching this message. Instead, shut down the computer and sell it. When the client user buy the computer and turn it on, he will see the last installer questions (his username, password, place and timezone). Done. The user will then be logged in into his freshly created account.

---

### Post by redsoxreed on 2008-12-24
Ah, I see now.  I only had an older Ubuntu live CD and that used to not be an option.

---

