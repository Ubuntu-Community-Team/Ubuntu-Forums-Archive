---
title: "Revert back to ubuntu 2 from 3 ubuntu 7.10"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by troy896 on 2008-07-02
i installed ubuntu 3 in 7.10 but i hate it. i want to go back to firefox 2. can anyone tell me how?

---

### Post by Pumalite on 2008-07-02
sudo apt-get install firefox-2

---

### Post by troy896 on 2008-07-02
yes, but i want to remove firefox 3. not just install firefox 2. and also what wouldi change in the menu for it to go to firefox 2...

---

### Post by dominiquec on 2008-07-02
```
sudo apt-get remove firefox firefox-3.0
```

and follow that up with

```
sudo apt-get install firefox-2
```

---

### Post by DJ_Peng on 2008-07-02
Keep in mind that your profile may not work with Firefox 2 since Firefox 3 used it. You may need to create a new profile, but there's a way to get some of the data back. The [mozillaZine knowledge base]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox") has some info you may find helpful.

Just out of curiosity, what do you dislike about Firefox 3? I've said Firefox 3 could be a polarizing release (I'm not that thrilled with it myself) and I'm curious what is leading you back to Firefox 2.

---

### Post by meindian523 on 2008-07-02
I also think you should be purging all firefox 2.0 files
```
sudo apt-get remove --purge firefox firefox-3 && sudo apt-get install firefox-3
```

---

