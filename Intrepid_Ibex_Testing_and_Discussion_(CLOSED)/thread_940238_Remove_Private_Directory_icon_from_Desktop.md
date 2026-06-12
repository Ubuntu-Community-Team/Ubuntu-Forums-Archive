---
title: "Remove Private Directory icon from Desktop"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rouge568 on 2008-10-06
How does one remove the icon for the Private directory from the Desktop? I like mine clean and free of icons. (Intrepid Beta)
Thanks.

---

### Post by Naddiseo on 2008-10-06
Need to turn this off. Will remove all mounted volumes though.
```
gconf-editor /apps/nautilus/desktop/volumes_visible
```

---

### Post by rouge568 on 2008-10-06
This is more of a hack than a real solution, and true fix would be more helpful. Why can this option not be turned off? This seems intuitive, especially for people who a) don't like desktop icons but do want to see mounted directories or b) don't want to declare to the world that they have a Private directory.

---

### Post by mc4100 on 2008-10-06
```
gconftool-2 -s  --type bool  /apps/nautilus/desktop/volumes_visible  false
```

---

### Post by Naddiseo on 2008-10-06
I agree, it is more of a hack, it seems that's how gnome does things though; in order to make things simpler for users they remove/hide the more powerful customizations.

File a bug report, I don't belive that the "real solution" exists.

Sorry I couldn't be of more help.

---

### Post by rouge568 on 2008-10-06
Oh well. Thank you very much for your help, though. I have submitted a bug report here: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/279422](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/279422)

---

### Post by cariboo on 2008-10-06
The icon is only there when your private directory is mounted to unmount and make the icon go away, in a terminal type:

```
umount.ecryptfs_private
```

For more look here:

[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

I had problems early on in testing, but it turned out most of it was my own fault. :)

Jim

---

### Post by Kow on 2008-10-07
> **rouge568 said:**
> This is more of a hack than a real solution, and true fix would be more helpful. Why can this option not be turned off? This seems intuitive, especially for people who a) don't like desktop icons but do want to see mounted directories or b) don't want to declare to the world that they have a Private directory.

Agreed! I have had this very same thought since setting it up. I would also recommend future nautilus integration instead of auto-mounting the drive on login. I understand that this may already be planned...

---

### Post by taavikko on 2008-10-07
Changed the bug to confirmed.

---

