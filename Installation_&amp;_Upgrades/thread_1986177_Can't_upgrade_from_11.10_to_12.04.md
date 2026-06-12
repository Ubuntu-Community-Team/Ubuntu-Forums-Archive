---
title: "Can't upgrade from 11.10 to 12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by kyng on 2012-05-24
When I click upgrade in Upgrade manager it downloads 2 files, asks for root psw and then nothing happens. Upgrade managee is closed and there are no error messages or anything so I have no idea what is wrong. Any sugestions?

---

### Post by MG&amp;TL on 2012-05-24
Well, I never recommend upgrades, (too much trouble, for me), but if you want to do that, there may be some debugging output from update-manager.

Try:

```
update-manager
```

from the terminal.

---

### Post by mörgæs on 2012-05-24
Or boot the computer and run

```
sudo apt-get update
sudo apt-get upgrade
```

as they give more detailed error messages.

If it does not work, don't waste too much time. A fresh install is always worth considering.

---

### Post by raja.genupula on 2012-05-24
what updates are installed ?

open software-center -> History -> updates .

---

### Post by MG&amp;TL on 2012-05-24
> **mörgæs said:**
> Or boot the computer and run

```
sudo apt-get update
sudo apt-get upgrade
```

as they give more detailed error messages.

If it does not work, don't waste too much time. A fresh install is always worth considering.

As OP wants to upgrade from one release to another, why will this help? Just wondering, a little confused. :-k

---

### Post by mörgæs on 2012-05-24
Before trying the online upgrade it's important to verify that the system is stable and receives the normal updates.

---

### Post by kyng on 2012-05-26
```
sudo do-release-upgrade -d
```That did the trick. This problem is solved I guess.

---

### Post by nwgray on 2012-06-03
> **kyng said:**
> ```
sudo do-release-upgrade -d
```That did the trick. This problem is solved I guess.

That worked for me as well. 

Thanks for the tip!!!

---

