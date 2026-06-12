---
title: "how small can ubuntu alternative installation"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by roytam1 on 2009-11-28
I tried a barebone install and it used ~630MB, what packages can be removed safely?
Debian 5.03 minimal installation used ~380MB.

---

### Post by phillw on 2009-11-28
You can start with about 13Mb, then choose what you want to add [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Has the Howto on that. For a GUI of 9.10 you'll need about 1.5GB Disk space (Xubuntu - [http://www.xubuntu.org/get](http://www.xubuntu.org/get)) Xubuntu can run on 256Mb RAM (Well, it can manager a bit less, but ti's not recomended) It's the GUI that takes up the room - there are some other GUIs you can look at :

There's a good discussion on the matter over here --> [http://ubuntuforums.org/showthread.php?t=1332606](http://ubuntuforums.org/showthread.php?t=1332606)

Regards,
Phill.

---

### Post by roytam1 on 2009-11-28
> **phillw said:**
> You can start with about 13Mb, then choose what you want to add [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Has the Howto on that. For a GUI of 9.10 you'll need about 1.5GB Disk space (Xubuntu - [http://www.xubuntu.org/get](http://www.xubuntu.org/get)) Xubuntu can run on 256Mb RAM (Well, it can manager a bit less, but ti's not recomended) It's the GUI that takes up the room - there are some other GUIs you can look at :

There's a good discussion on the matter over here --> [http://ubuntuforums.org/showthread.php?t=1332606](http://ubuntuforums.org/showthread.php?t=1332606)

Regards,
Phill.
but at least I need apt-get, g++, lft, w3m.

---

### Post by phillw on 2009-11-28
lol --- yup !!!, the minimal CD DOES have the likes of apt-get. It'll be your choice of GUI that is the killer question - there are several small ones you can look at.

For you, I think the Server edition & then go hunt a small gui for your needs  [http://ubuntuforums.org/showthread.php?t=1197520](http://ubuntuforums.org/showthread.php?t=1197520)

There are alternative Linuxes like dsl that people say work well. Also, do not forget to have a look at the UNR version of ubuntu. But, it's going to be the GUI that is the killer for disk-space. So, I'd advise taking a look round and seeing how people get on with the alternatives to gnome on the server edition. You can slways choose not install the AMP part of LAMP - or, use the alternative CD via the minimalCD route.

Regards,

Phill.

---

### Post by wojox on 2009-11-28
> **roytam1 said:**
> but at least I need apt-get, g++, lft, w3m.

So download the mini.iso like phillw suggested and you'll have just a shell environment with those features.

---

### Post by roytam1 on 2009-11-28
> **wojox said:**
> So download the mini.iso like phillw suggested and you'll have just a shell environment with those features.
but how can I install mini.iso to harddisk?
I boot mini.iso and it goes to network installer.

---

### Post by wojox on 2009-11-28
Right it has to download the packages to install. That's why the cd is so small. When you get to the Taskel screen don't install anything.

---

