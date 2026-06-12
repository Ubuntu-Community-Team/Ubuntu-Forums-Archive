---
title: "Kubuntu multiple users not working?"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eks on 2010-04-25
Hello,

Posted this on General Help because I was not finding the Lucid Lynx forum... maybe I should have searched more first...

Anyway, I had Ubuntu 9.10 running ok, but I've decided to try Lucid Lynx with Kubuntu from scratch (apart reusing /home without configs "/."). I was quite impressed with the quality of KDE. Everything worked out of the box also. 

Until I tried to login with the two other accounts this computer had...

With one of the users I get both errors seen on the snapshot. One regarding the network manager (which I think it was given just because it was already started by another user), and the ibus error, which completely locks the user from accessing any other drive or usb disk.

For the third user, even if creating it from scratch (not re-using his /home), I get an error:

```

kstartupconfig4 does not exist or fails. The error code is 3. Check your installation.

```

/home is in another partition that's been used since 7.10 I think. I did cancel all /. from all users and the remaining .files from each one homes before installing Kubuntu 10.04 though.

Any ideas?

---

### Post by eks on 2010-04-26
bump

The permissions for both .kde and .dbus are right for all users. And for the third, new, one, well, it's from scratch... I don't get it.

---

