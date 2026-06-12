---
title: "ipv6"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-12-10
i need to disable ipv6.
i tried the /etc/modeprobe.d/aliases file, but it didn't work.
i was "exploring", and went to system/administration/networking
in the network settings, i clicked the hosts tab. for ME, not sure about anyone else, there are 6 "hosts" that include something to do with ipv6. i was wondering, if i delete them, will that disable ipv6?

---

### Post by Squrdel on 2006-12-10
Open your browser and type "about:config" - without the "".
In the filter entry box type "ipv6". One line will be left, right click and select "toggle". Close the browser.
Job done.

---

### Post by xptweakerntn on 2006-12-10
i have did that, but i want ipv6 GLOBALLY turned off. that way, thunderbird, amarok, anything that uses the internet will respond normally, not just firefox, and when you go to about:config, that only disables it for firefox.

---

### Post by zgornel on 2006-12-11
go into /etc/modprob.d/aliases and change the line:
```
alias net-pf-10 ipv6
``` into ```
alias net-pf-10 off
```and add
```
alias ipv6 off
```
The other option is to disable it recompiling the kernel. :D

---

