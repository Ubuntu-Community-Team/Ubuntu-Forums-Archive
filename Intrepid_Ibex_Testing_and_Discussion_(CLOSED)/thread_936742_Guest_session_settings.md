---
title: "Guest session settings"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MJWitter on 2008-10-03
I really like the idea of the guest session but was wondering if there is any way to make changes to its defaults?

For example, when i open Firefox in the guest session i have to choose my settings for Add-ons. When I log out and open a new Guest session I have to do it all over again.

So it would be great if I could set things like that by default and, say, add specific icons to the desktop.

Does anyone know how this could be done or where to suggest it? Brainstorm?

---

### Post by wilsong on 2008-10-03
Hey, 

I was having some problems that i didnt like with Guest Sessions either, some options that i didnt really like, or thought that should work different, i would appreciate you adding your idea (and if you want reviewing the ones i suggested) to the forum post here 

[http://ubuntuforums.org/showthread.php?t=934972](http://ubuntuforums.org/showthread.php?t=934972)

---

### Post by dinxter on 2008-10-03
i'd guess you could do something in the "/usr/share/gdm/guest-session/guest-session-setup.sh" file after the temporary home directory has been mounted to copy across some user default files you'd like to the temp guest user home directory in a way such as....

cp /dir/or/files/with/custom/setup/ "$HOME"

---

