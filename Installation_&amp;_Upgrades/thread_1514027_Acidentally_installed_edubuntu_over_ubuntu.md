---
title: "Acidentally installed edubuntu over ubuntu"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Ddc2003 on 2010-06-20
I'm running 10.04 lucid. I was looking through the software center and downloaded the edubuntu package. When I restarted my computer, the login screen had a stupid tree and an edubuntu symbol. I hate it so much, but I dont want to reinstall ubuntu and loose all my other applications. Hep?

---

### Post by lemming465 on 2010-06-21
Hmm.  My first guess would be to try **sudo apt-get install ubuntu-desktop --reinstall**

---

### Post by Ddc2003 on 2010-06-21
Thanks for the reply, but it didnt work. Im so confused by this...

---

### Post by Duckblaster on 2010-10-02
try **sudo apt-get remove edubuntu-desktop** then **sudo apt-get autoremove**

---

