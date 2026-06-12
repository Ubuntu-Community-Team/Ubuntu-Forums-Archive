---
title: "Mythtv - Can't start database. This is getting ridiculous!"
date: 2017-09-22
forum: MINT
---

### Post by kkrofft on 2017-09-22
Trying to build a new Mythtv server. Figured I had issues with .28 so .29 might be better. Chose the Mint 18.2 distro since I like the menus better. Installed Myth using every method I can google, Software managers, PPA's Command line, it doesn't matter every single time I try i get to the point of starting the backend setup and the message is that the database won't start. Searching shows folks who have had this issue and solved it by using the password in /etc/mythtv/config.xml in the setup screen, does not work for me. I can use mysql -u mythtv -p with the password shown in the config.xml and the mysql login works fine. My user account is part of the mythtv group.

I have reinstalled the OS and Myth a good 8 to 10 times to be sure I am not polluting the configuration with all the things I have tried from various forums. i am ready to just chuck it all but just can't seem to stop.
Sorry for the rant but if you have something new I can try, I am willing.

Thank you!

---

### Post by QIII on 2017-09-22
Moved to MINT.

---

### Post by kkrofft on 2017-09-22
I don't think this is Mint related as I probably should have mentioned that I tried Ubuntu 17.04 with the exact same issue before deciding on Mint. Hopefully it will be viewed there/here sufficiently to get some suggestions.

---

### Post by mc4man on 2017-09-23
Why not ask here
[https://forum.mythtv.org/index.php](https://forum.mythtv.org/index.php)

---

### Post by mc4man on 2017-09-23
Also here's another thread, seems same issue
[https://ubuntuforums.org/showthread.php?t=2372019](https://ubuntuforums.org/showthread.php?t=2372019)

---

### Post by kkrofft on 2017-09-27
I gave up getting it to work on a standard distro and loaded Mythbuntu. At least the database errors went away. Another two days of frustration and I finally have it working for the most part.

---

