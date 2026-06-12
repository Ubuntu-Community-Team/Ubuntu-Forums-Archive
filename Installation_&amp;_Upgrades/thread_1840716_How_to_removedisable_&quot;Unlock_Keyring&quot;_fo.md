---
title: "How to remove/disable &quot;Unlock Keyring&quot; for internet connections"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by davidq25 on 2011-09-08
Hi. How can you disable the "Unlock Keyring" that's required to connect to the internet if you enable it. There's an option to "Automatically unlock this keyring whenever I'm logged in" when the "Unlock Keyring" popup appears, but the popup keeps reappearing when I log off and log back into the computer.

Thanks for the help

---

### Post by Clancy_s on 2011-09-08
My solution was to set it so the keyring didn't lock, following the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=1003471](http://ubuntuforums.org/showthread.php?t=1003471)

I've been upgrading since 9.10 so I haven't tested it in a new install of 11.04 - you could try it and see how it goes, (no guarantee of safety or effectiveness though).

---

### Post by doogiekd on 2011-10-01
this worked for me:

1. in the panel, right click the internet (wireless or wired) icon.

2. select "edit connections." enter superuser (administrator) password.

3. select the type of connection (wired or wireless)

4. if wireless, select the name of your network. if wired, select eth0.

5. Select "available to all users" box at the bottom of the box.

6. click "save."

7. logout, then log back in.

8. the annoying keyring issue should be gone.

---

