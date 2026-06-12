---
title: "Problems installing any program on Fistey 7.04"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by kelimandya on 2007-07-19
Ok Fyi i am inexperienced at this but Every time i try to download a program i get the error  "Only 

one software management tool is allowed to be open at a time" but i have made absolutly certain 

that nothing else is open. also whenever i try to run synaptic or update manager i get the message

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." Well any help would be greatly appreciated. Thanks.

---

### Post by kelimandya on 2007-07-20
Someone, Please?

---

### Post by aquavitae on 2007-07-20
> **kelimandya said:**
> 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Did you try running 'dpkg --configure -a'?

---

### Post by kelimandya on 2007-07-20
I don't know how to.

---

### Post by aquavitae on 2007-07-20
Look under the menu for a terminal.  In ubuntu its called gnome-terminal and under kubuntu its konsole.  It will open a screen that looks a bit like windows "dos".  In it, type ```
sudo dpkg --configure -a
```  The sudo part is so that you can run it as if you were the root user.  You won't be able to run dpkg as a normal user because of its permissions.  Once you've done that, try synaptic again.  If it still doesn't work, copy the output from dpkg --configure -a and post it, along with the error message from synaptic.

---

### Post by kelimandya on 2007-07-20
Worked like a Charm, THANKS A TON!

---

