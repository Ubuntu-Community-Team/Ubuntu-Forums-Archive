---
title: "DON'T sudo apt-get install fglrx &amp;&amp; aticonfig"
date: 2010-04-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-29
I have seen a couple of posts where users are trying to install fglrx drivers using the following method. It doesn't work in Lucid.
```
sudo apt-get install fglrx && sudo aticonfig --initial
```Enable it in System-Admin-Hardware Drivers or it will not configure properly.
Guide here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Try this guide for removing drivers:
[https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")
Be sure you need fglrx - I would try to get the default radeon driver working first.

---

