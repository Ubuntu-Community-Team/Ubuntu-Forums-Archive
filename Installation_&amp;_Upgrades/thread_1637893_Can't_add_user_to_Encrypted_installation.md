---
title: "Can't add user to Encrypted installation"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by opus1 on 2010-12-05
I just installed Ubuntu 10.04 and decided to encrypt the entire hard drive for the first time.  I followed the tutorial on how to install Ubuntu and encrypt the hard drive during installation, located here: [http://ubuntuforums.org/showthread.php?t=1205372&highlight=cryptsetup](http://ubuntuforums.org/showthread.php?t=1205372&highlight=cryptsetup)

Everything worked as planned, however, I cannot successfully add a user.  Specifically, I can add a user account, but when that user logs in, they receive an error stating: "Could not update ICEauthority file /home/username/.ICEauthority".  Closing this window results in a second error: "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)".  Then I get errors stating that Nautilus could not create the Desktop or .nautilus folders.  After this, the computer hangs indefinitely at the desktop wall paper.

I have googled these errors and found several different solutions, none of which have worked.  I have looked in the user director and there is no .ICEauthority file to change permissions on.

I suspect that this has to do with the encryption I did, but an evening of looking through google has resulted in no joy.

Can anyone help?

Thanks,

---

### Post by opus1 on 2010-12-05
I fixed the problem... it was a permissions problem.  I issued a
```
sudo chown -R user:user *
```
within my home directory. Apparently it was recursive up through the parents and changed the owner of the /home directory from "root" to "user".  That's why other users couldn't access anything within /home.

I learned 2 lessons:
[LIST=1]
[*]Don't change owners recursively from within a directory
[*]Don't do this stuff at one in the morning
[/LIST]

---

