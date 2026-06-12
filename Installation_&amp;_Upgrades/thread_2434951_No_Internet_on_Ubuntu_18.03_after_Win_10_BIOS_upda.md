---
title: "No Internet on Ubuntu 18.03 after Win 10 BIOS update"
date: 2020-01-14
forum: Installation &amp; Upgrades
---

### Post by kubasienczyk on 2020-01-14
EDIT: problem solved. Disabling Secure Boot, which got back up, did the trick.

So I had a laptop service point install Ubuntu 18.03 on my IdeaPad  L340 with Win 10 preinstalled to achieve my usual dual boot mode. (I did  it myself couple of times, but on this machine the USB installer  wouldn't show the  "install alongside existing Windows installer"  option). I worked great - for a week. Some Lenovo updates kicked in,  including a BIOS update and the boot menu disappeared.


  I entered BIOS to change boot order and moved Ubuntu to the first  spot. That did the trick and the boot menu is back. However, for some  bizarre reason, Ubuntu is now disconnected from the Internet, prompting:  no WiFi adapter available. (It was the same when I first tried  installing Ubuntu on this machine by myself, so the update must have  reset something). On Windows 10 WiFi works fine, as I used to on the  said Ubuntu. I'm puzzled.


  What do I do?

---

### Post by CelticWarrior on 2020-01-14
Disable Secure Boot and try again.

---

### Post by kubasienczyk on 2020-01-14
That did the trick. The BIOS update reset that too. Works now. Thank you!

---

### Post by CelticWarrior on 2020-01-14
Please use the thread tools to mark it as solved. Thank you.

---

