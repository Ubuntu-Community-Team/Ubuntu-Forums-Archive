---
title: "(EE) Screen(s) found, but have a usable configuration after Skype installation"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by padu on 2010-04-27
Hi all,
I just installed 8.10 on my desktop.
Everything was working ok.
After successfully having installed skype and adjusting sound I get this error when starting PC:
The following error was encountered: You may need to update your configuration to solve this.
Ubuntu is running in low-graphics mode
(EE) intel(o): No valid modes.
(EE) Screen(s) found, but have a usable configuration

When I choose to make a new configuration automatically it does not change the situation. Every restart gives me the same message.
I have not much experience in Linux or Ubuntu, so I don't know what to type in Terminal to show u more details of this error. But if you tell me I will do it and post the result.
Thanks in advance for your help.
Padu

---

### Post by dstew on 2010-04-27
These error messages come from the X server software that creates the graphical display. Probably, Skype changed some setting in the file /etc/X11/xorg.conf file, which controls the X server.

Possibly, the Skype installer created a backup xorg.conf file, in the /etc/X11 directory. Look to see if one is there. It might have the name xorg.conf.bak, or possibly it has a number that is the date it was created. If so, you can try to use the old backup xorg.conf file by entering these commands:```
cd /etc/X11
mv xorg.conf xorg.conf.old
mv xorg.conf.bak xorg.conf
```Then reboot.

If there are no backups, or you cannot get the backups to work, you might need to reconfigure the X server. I think the command in 8.10 is **xfix**, entered on a command line from a Recovery Mode boot.

---

