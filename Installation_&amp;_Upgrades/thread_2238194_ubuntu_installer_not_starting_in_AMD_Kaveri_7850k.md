---
title: "ubuntu installer not starting in AMD Kaveri 7850k"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by nsk_balu on 2014-08-06
ubuntu installer not starting in AMD Kaveri 7850k

I am using the VGA port to connect monitor. Installer starts and click install ubuntu not starting and it says no input (Video not detecting).

How to fix this ?

---

### Post by Mark Phelps on 2014-08-06
All you've told us is that you're running and AMD APU and have a VGA port.  That's not nearly enough to go on.

Boot from the installation media, choose Try Ubuntu, and when you get to a desktop, open a terminal and enter "lspci" -- and post that info back here.

Folks need to see info about your hardware before they can offer detailed advice.

---

### Post by nsk_balu on 2014-08-06
I was able to see the menu 

Try ubuntu/install ubuntu/check media

After that, If i select install/try ubuntu.. The next screen is not going. It gives video not detecting.

I have a laptop with AMD a6 which works fine for ubuntu installation same media.

---

### Post by Mark Phelps on 2014-08-06
See if the details in the link work with regard to setting nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

