---
title: "compatibilty of /Home between 20.04LTS and 22.04 LTS"
date: 2022-05-12
forum: Installation &amp; Upgrades
---

### Post by Nosphky on 2022-05-12
When I did a clean installation of 20.04, I kept my /home on a separate drive, sda1, as recommended on the forum at the time. Now, I'm thinking about a clean install of 22.04 (probably 22.04.1 when it arrives) and in the meantime, UbuntuStudio has moved from Xfce to KDE Plasma.

 Will there be any config files in my present /home that are incompatible with the KDE Plasma setup? Are there any recommendations for actions prior to the clean install of 22.04 with KDE Plasma?

---

### Post by #&amp;thj^% on 2022-05-12
Xfce to KDE Plasma
It will have a effect on themeing for just **one** heads-up.
I solved it by:
removing a directory:

```

rm ~/.gtkrc-X.0
```
What ever version is there, gtkrc-2.0 or gtkrc-3.0
create different users for each window manager. This can prevent these sorts of problems in the future for you.

---

### Post by ajgreeny on 2022-05-12
One alternative, may be to install the normal ***Xubuntu 22.04*** and simply add the extra packages that are included by default in **Ubuntu-Studio**.

Unfortunately, I do not know exactly what extras are in the Ubuntu-Studio-20.04 system which you currently have compared with Xubuntu-20.04 itself, but I believe they are all available in the standard Ubuntu repos.

Just for your information, I currently have a dual boot system with both Xubuntu 20.04 and 22.04, sharing the same /home partition and so far, there have been no problems.

---

### Post by Nosphky on 2022-05-12
Thank you 1fallen and ajgreeny. I did realise that I could stay with Xfce by going to Xubuntu and the UbuntuStudio group does already has a pre-packaged set to bring same functionality to Xubuntu. I read the reasoning given by UbuntuStudio devs for changing to KDE PLasma so I thought I would go with it although I have had no problems over the years with Xfce.

---

### Post by #&amp;thj^% on 2022-05-12
New can be both fun and, now what?
you seem to be up for the change.
Enjoy

---

