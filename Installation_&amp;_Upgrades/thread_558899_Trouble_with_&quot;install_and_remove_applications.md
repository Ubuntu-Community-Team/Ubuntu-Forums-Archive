---
title: "Trouble with &quot;install and remove applications&quot;"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by frostwyrm333 on 2007-09-24
When i try to install anything it will give me:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a to correct the problem.
E: _cache->open() failed,please report.

Sorry i am new, i dont have slightest idea what to with this. I tried to do smt from terminal but i would only mess it up more.

Thanks for help.

---

### Post by forestpixie on 2007-09-24
open a terminal and do as it says :)

```
sudo dpkg --configure -a
```

if you haven't used terminal yet (Apps > Accessories > Terminal) it will want your pasword, but when you type it won't show - just keep going and then enter.

And welcome

---

### Post by frostwyrm333 on 2007-09-25
im such fool, ok thank you, it happend when one insteller freezed.

---

### Post by frostwyrm333 on 2007-09-25
Well, more problems,
When i was installing the package of restricted codecs, java and that stuff, the installation of java frozen in the "agree the license" screen. I restarted, and then everything messes up. I tried to download new updates. The installer told me that some packages are wrong(java), update says 
"Error: BrokenCount > 0" and when i start, it says that index of software is domaged and that i should use  synaptic (it identified the wrong package but it cant delete it) or write "sudo apt-get install -f", when i put it to terminal i only get to java license agreement, where is ok "button" on the bottom but i dont know how to go next (its frozen?)
Sound doesnt work, programs which open music files freeze when they open something (but there is sound when i log in), "users and groups" freezes too.
I know i messed up something but since i am newbie in ubuntu (and linux) i dont know what . Switching users wont help.

---

### Post by rsambuca on 2007-09-25
> **frostwyrm333 said:**
> Well, more problems,
When i was installing the package of restricted codecs, java and that stuff, the installation of java frozen in the "agree the license" screen. I restarted, and then everything messes up. I tried to download new updates. The installer told me that some packages are wrong(java), update says 
"Error: BrokenCount > 0" and when i start, it says that index of software is domaged and that i should use  synaptic (it identified the wrong package but it cant delete it) or write "sudo apt-get install -f", when i put it to terminal i only get to java license agreement, where is ok "button" on the bottom but i dont know how to go next (its frozen?)
Sound doesnt work, programs which open music files freeze when they open something (but there is sound when i log in), "users and groups" freezes too.
I know i messed up something but since i am newbie in ubuntu (and linux) i dont know what . Switching users wont help.

Just use the arrow keys or the tab button to agree to the license terms.

---

### Post by frostwyrm333 on 2007-09-25
yepp, tried, whole window will freeze, after that update manager will freeze.
I really think should reinstall ubuntu. Cant be worse.:)

---

