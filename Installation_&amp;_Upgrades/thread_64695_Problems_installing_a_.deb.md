---
title: "Problems installing a .deb"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by SevenForever on 2005-09-11
I hope this is the right forum.

I've searched for another being with the same error as I do, but I couldn't find any information. So I hope someone will be able to help me. Alright, I have a few .deb packages and I want to install them.

This is what happens :```
root@XplioUbuntu:/home/sevenforever # cd Desktop
root@XplioUbuntu:/home/sevenforever/Desktop # dir
opera.deb
root@XplioUbuntu:/home/sevenforever/Desktop # sudo dpkg -i opera.deb
(Reading database ... 76788 files and directories currently installed.)
Preparing to replace opera-static 8.02-20050727.1 (using opera.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (8.02-20050727.1) ...

root@XplioUbuntu:/home/sevenforever/Desktop 
``` 

It just goes to "Setting up opera-static (xxxxxxxxxxxxxxxxx) ... then seems to do nothing. Is that what's supposed to happen? If so, how do I then launch the application? Thanks.

---

### Post by Plank117 on 2005-09-11
A blind man cannot lead another blind man, but it doesn't look like anything went wrong with the install. To verify this, just try to run the app from the terminal:
bob@bobs-Ubuntumachine: opera (or the package name of whatever you installed).
Also, you can check by doing this:
 ```
ls  //usr/bin
``` 
(the extra slash at the beginning is not a mistake, it's the top level of your directory structure.) This is untested, but I think it should work.

---

### Post by SevenForever on 2005-09-11
I love you man. Thanks a million, I love my Opera, everything works 100% now!

---

