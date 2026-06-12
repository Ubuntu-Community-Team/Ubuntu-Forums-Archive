---
title: "ubuntu 12.04.1 LTS live cd username and password"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by dhrayofhope on 2012-08-29
what is the username and password of the live cd.
ubuntu as username and password blank does not work.
I m just trying to use it as live cd...>>>
boot from the cd... and then stacked in the log in page.


Please help.

---

### Post by Karlchen on 2012-08-29
Hello, dhrayofhope.

Provided you are using a genuine Ubuntu 12.04 live system then the user is *ubuntu* and *ubuntu* has got no password.

Karl

---

### Post by coffeecat on 2012-08-29
The username and password are indeed "ubuntu" and nothing for the password, but if you are seeing the login screen, you either have a CD burnt from a faulty ISO, a faulty CD, or the CD is being misread.

Check the md5sum of the downloaded ISO. If that is OK, tap the spacebar (or any key) when you see the purple screen and the two small icons when first booting the CD. At the text menu choose the disc check option.

If the CD passes it could be something as simple as dust on the CD or the optical drive lens.

---

### Post by voltronz on 2013-02-09
> **dhrayofhope said:**
> what is the username and password of the live cd.
ubuntu as username and password blank does not work.
I m just trying to use it as live cd...>>>
boot from the cd... and then stacked in the log in page.


Please help.
I have had this same problem, and fond a solution that worked for me, perhaps it can help you?

ubuntu 12.04 amd64 live cd image installed to usb via Unetbootin, 1gb persistence. the first two times ubuntu started up just fine, and now it is asking me for a username and password. ubuntu isnt even recognized as a username. ctrl+alt+F1 will take you to the terminal, from there i typed "startx" and only a desktop shows up. from there however i can open another terminal with ctrl+alt+T. for my purposes, my harddrive failed, so i am trying to do my homework with this live installation of ubuntu, so from this terminal i can just type "frirefox" and do my homework. this is as far as i need to go, hope this can lead you in the right direction at least

---

