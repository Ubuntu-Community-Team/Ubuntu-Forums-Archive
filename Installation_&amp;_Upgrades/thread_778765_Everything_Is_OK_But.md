---
title: "Everything Is OK But"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by JKhoo on 2008-05-02
A minor problem. Got this message after running Update Manager.

W: GPG error: [http://e17.dunnewind.net](http://e17.dunnewind.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF

This came about after installing Enlightenment and uninstalling it.
Will this cause any problem on the system? Any suggestion appreciated?

---

### Post by noynac on 2008-05-02
I have never encountered that problem, but you may want to open synaptic and click on *settings > repositories > third-party software.* Does it show anything for Enlightenment?

---

### Post by bobnutfield on 2008-05-02
This is because of the lack of a key for a third party source.  It is not usually a problem, but you might fix it by check the source site for instructions on installing the public key.

Hope this helps

Bob

---

### Post by JKhoo on 2008-05-02
Yes that's the problem. Remove it and everything is OK now. Thanks noynac and also you Bob
Appreciate those fast suggestions.

---

### Post by XemeX on 2008-05-02
Here you have got some hint:
http://ubuntuforums.org/showthread.php?t=175116

---

