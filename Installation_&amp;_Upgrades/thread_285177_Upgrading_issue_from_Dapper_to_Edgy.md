---
title: "Upgrading issue from Dapper to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by quixentric on 2006-10-26
Hello, community!
This is the first time I have upgraded Ubuntu, so I'm a little confused. First off, when I ran gksu "update-manager -c", it did not indicate that there was a new version available in the GUI window (in fact, there were no upgrades at all). So, I went for the text-based method. I installed ubuntu-desktop and edited my sources.list then ran the apt-get updates (including dist-update, the exact line of code from the EdgyUpdate wiki page). After I thought it had finished, I ran sudo apt-get -f install to make sure it worked correctly, and it gave me this:

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 962 not upgraded.

I'm assuming that this means it did not work correctly, and I was wondering if anyone could help me out?
Thanks!
-quixentric

---

### Post by JackandJohn on 2006-10-26
what you want at this point is:

```
sudo apt-get dist-upgrade
```

---

### Post by h00RU on 2006-10-26
Hey there,
You do not mention if you ran an "apt-get dist-upgrade". If not try that.

H

---

### Post by quixentric on 2006-10-26
Ah, I already did. Sorry, that was poorly worded in my first post.
I've gone back to having dapper in for edgy in all places in my sources.list and seeing what happens when I run apt-get updates then. I think the problem may be with one of my repositories.

---

### Post by boz on 2006-10-26
I would open sources.list with gedit:

sudo gedit /etc/apt/sources.list

and do Search->Replace:

search for:  Dapper

replace with:  Edgy

That way you're sure not to make any mistakes.  Alternatively, you can go to the Unofficial Ubuntu Starter Guide and copy their whole file and paste it in and follow the rest of their instructions.  I believe they recommend using aptitude for upgrading to Edgy.

---

### Post by quixentric on 2006-10-26
That's exactly what I did when editing my sources, so I know that's not the problem.
It's running smoothly using aptitude right now, though. Let's hope it continues that way!
-quixentric

---

