---
title: "Ubuntu-Kubuntu-Ubuntu"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by Jonathan45 on 2008-09-05
Hi im new to ubuntu and to linux.
i had ubuntu for about a month now and i saw the Kubuntu desktop. can i change From ubuntu to kubuntu? will i be able to change back from kubuntu?
will i get a worthless hybrid or a kubuntu?!

---

### Post by tuxxy on 2008-09-05
Kubuntu uses KDE rather than GNOME, yes you can install KDE in Ubuntu then select either GNOME or KDE at login.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by snowpine on 2008-09-05
> **Jonathan45 said:**
> Hi im new to ubuntu and to linux.
i had ubuntu for about a month now and i saw the Kubuntu desktop can i change From ubuntu to kubuntu? will i be able to change back from kubuntu?
will i get a worthless hybrid or a kubuntu?!

Hi Jonathan, at the Terminal, you can type:

```
sudo aptitude install kubuntu-desktop
```

Then, each time you log in, you can click the Sessions button and choose between Gnome (Ubuntu) and KDE (Kubuntu) sessions. They will exist nicely in parallel, the only real disadvantage is that your Applications menus will be a bit more crowded.

If you change your mind, you can uninstall Kubuntu:

```
sudo aptitude remove kubuntu-desktop
```

Good luck!

---

### Post by Jonathan45 on 2008-09-05
Thanks for the help:)

---

### Post by Jonathan45 on 2008-09-05
By the way can i uninstall gnome?!:confused:

---

### Post by snowpine on 2008-09-05
> **Jonathan45 said:**
> By the way can i uninstall gnome?!:confused:

Yes of course: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

No reason not to try both for a while before making the decision. :)

---

### Post by Jonathan45 on 2008-09-05
Thank everyone for the help!
One last question:will i get the new KDE4 or the stable KDE3?:):guitar:

---

### Post by Jonathan45 on 2008-09-05
hi i have now tried it but the kde session wont show up!!

---

