---
title: "Upgrade problem"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by BobTheBuilder on 2008-04-17
Hi everyone, I'm new to Ubuntu, although I used Unix years ago. I've installed Feisty on a desktop PC, and want to upgrade to Gutsy, but if I use Update Manager as suggested in the upgrade notes, there is no 'Upgrade to 7.10' button, although my Feisty installation is up to date.

This being the case, I tried using **gksudo "update-manager -c"** which results in update manager appearing, checking my Feisty install, and then sure enough telling me there is an upgrade to 7.10 available. Clicking the 'upgrade' button results in the release notes appearing, but clicking the 'upgrade' button on *that* window appears to do  nothing.

Can anyone help with what's going wrong? I'd be grateful for some help.

---

### Post by Partyboi2 on 2008-04-17
Make sure you have all the updates installed before upgrading, also make sure you have all 3rd party repo's disabled.

---

### Post by BobTheBuilder on 2008-04-18
Thanks Partyboi. I've used update manager to check Feisty is up to date, and I've only had Feisty up for a week or so as a stepping stone to Gutsy, so I haven't installed any 3rd party stuff *as far as I know*. How can I tell if 3rd party stuff is the problem?

---

### Post by Partyboi2 on 2008-04-18
To check 3rd party repo's open up Software Sources (System>Admin>Software Sources) Then click on the 2nd tab <3rd party software>
When you enter
```
update-manager -d
``` in a terminal is there any output in the terminal?
Another option you could try to upgrade is to download the gusty alternate cd and use that to upgrade.
> **Upgrading using the alternate CD/DVD**

  Use this method if the system being upgraded is not connected to the Internet. 
 [LIST=1]
[*]Download and burn the alternate installation CD. 
[*]Insert it into your CD-ROM drive. 
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD. 
[*]Follow the on-screen instructions. 
[/LIST] If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:  
 gksu "sh /cdrom/cdromupgrade"


---

### Post by BobTheBuilder on 2008-04-19
Thanks again, Partyboi. It turns out I did have some 3rd party stuff installed. I'd forgotten that I installed a Ralink wireless card and needed to install drivers etc.

Unfortunately, I've just broken my network connection by disabling/re-enabling the 3rd party software stuff, so it may be a while before I can get back to this. I'll probably download the alternate CD and see how that goes. Thanks again.

---

