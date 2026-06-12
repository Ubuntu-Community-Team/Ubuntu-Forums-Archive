---
title: "How to remove DOWNLOADED packages?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by OVERPOWER8 on 2009-12-05
Hello.

I have a lot of downloaded packages, that I want to remove.
I have installed much software using Synaptic Package Manager without option "*Delete downloaded packages* *after installation*".

After that I deleted a lot of that installed packages, but they are still downloaded and placed somewhere in my system. 

How can I remove those downloaded packages? (Don't ask why, if u know, just tell how).

Thanks.

---

### Post by Bachstelze on 2009-12-05
```
sudo rm /var/cache/apt/archives/*deb
```

Be careful about typos.

---

### Post by OVERPOWER8 on 2009-12-05
> **Bachstelze said:**
> ```
sudo rm /var/cache/apt/archives/*deb
```Be careful about typos.

Thanks for reply, but that isn't working - 
rm: cannot remove `/var/cache/apt/archives/*deb': No such file or directory

Or that means that packages are already removed?

---

### Post by alienclone on 2009-12-05
> **OVERPOWER8 said:**
> Thanks for reply, but that isn't working - 
rm: cannot remove `/var/cache/apt/archives/*deb': No such file or directory

Or that means that packages are already removed?


i ran the command once, it deleted what it was supposed to, then i ran it again and received the same msg you did, so i guess that means they are already deleted.

did it return to the bash prompt the first time you ran the command without saying it did anything? if so then it worked the first time you just didnt know it.

---

### Post by Bachstelze on 2009-12-05
> **OVERPOWER8 said:**
> Thanks for reply, but that isn't working - 
rm: cannot remove `/var/cache/apt/archives/*deb': No such file or directory

Or that means that packages are already removed?

Yes.

---

### Post by oldos2er on 2009-12-05
** sudo apt-get clean** will also clear the cache directory.

---

### Post by OVERPOWER8 on 2009-12-09
Thanx Everyone for your replies.

Just freed my distro from some garbage.

---

