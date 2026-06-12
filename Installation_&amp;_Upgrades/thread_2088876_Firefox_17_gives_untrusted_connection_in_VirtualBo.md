---
title: "Firefox 17 gives untrusted connection in VirtualBox with Ubuntu 12.04 guest"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by cx1964 on 2012-11-27
When I try to connect to my Bank with Firefox 17 from Virtualbox 4.1.22 and a Ubuntu 12.04 64 bits client a get a Untrused connection message.
When I try to connect to the same URL from my Bank with Firefox 17
natively under Ubuntu 12.04 64 bits I won't get this message.
In Virtualbox I completely remove Firefox 17 (see artikel [http://askubuntu.com/questions/89638/how-to-completely-uninstall-and-reinstall-firefox](http://askubuntu.com/questions/89638/how-to-completely-uninstall-and-reinstall-firefox)) and then did a fresh install of Firefox 17, I still get the "Untrused connection message".
I also installed the latest Chrome browser in VirtualBox. When I connect tot the same URL of my bank with Chrome in Virtualbox I also do not get this message.

Does anyone have a idea how to fix this Firefox problem with Virtualbox?

Thanks in advance

---

### Post by cx1964 on 2012-12-02
Problem is solved.

When I upgraded VirtualBox from version 4.1. to 4.2.4 I was able to
create an thrusted internet connection with Firefox version 17 in a Ubuntu 12.04 guest.

---

