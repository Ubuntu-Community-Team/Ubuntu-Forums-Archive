---
title: "update-manager and apport aren't working behind proxy, anyone else?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Eversmann on 2009-09-30
Hello.

I just noticed today, working with the netbook on my college, that using the current version of update-manager and the apport utility (noticed when trying to report the bug) aren't working using the gnome proxy settings.

Anyone else have the same problem?

---

### Post by Zoot7 on 2009-09-30
Exact same issue here. The nm-applet automatically crashes when I try to connect to my College network, I'm waiting for the Beta to see if that will sort the problem.

---

### Post by Eversmann on 2009-09-30
Not really the same issue. My networkmanager works flawlessly (instantly i must say) but, when i use the proxy settings from the gnome proxy one, update-manager doesn't use it, neither the apport utility.

The other applications, having the "automatic detect proxy settings" or the "use gnome settings" should work.

apt-get command works too (and that's the last application i expected to see working this way)

---

### Post by rburkartjo on 2009-09-30
yes the update manager isnt working for me either

---

### Post by Zoot7 on 2009-10-01
I see I didn't read the thread properly did I? :p

Anyway.. just to follow up. I got the network manager applet working okay, but the update manager didn't work behind the proxy. However after manually setting the proxy settings and using the option "Apply System Wide", it worked okay and fetched over 300mb of updates after that.

---

