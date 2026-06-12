---
title: "Trying to install wifi radar."
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by amna543 on 2012-12-22
We have moved the wifi and Ubuntu won't recognise my wifi this normally wouldn't be a problem but I don't have wifi radar anymore. So I tried installing it but it says "requires installation of untrusted packages' can anyone help please?

---

### Post by grahammechanical on 2012-12-23
I think that we need to clarify what the problem is. What version of Ubuntu are you using?

You say that you have moved the WiFi. Do you mean that you have moved the wireless access point/hub/router to somewhere else? If so, Ubuntu should still connect to it because you have not changed anything in Ubuntu, have you? Perhaps the wireless access point is not in range or the wireless signal is too weak.

The message "requires installation of untrusted packages" means exactly what is says. Canonical who take responsibility for Ubuntu do not take responsibility for applications developed by other people. In this sense they are 'untrusted' packages. It does not mean that we should not install them. It is our decision.

Not knowing the version of Ubuntu that you are using I cannot give specific advice.

You can open a terminal and run this command:

```
nm-tool
```

that should show you a list of wireless access points that are in range and the signal strength. Is your access point in that list? Do you see any access points in range. Perhaps you have switched off wireless networking in Ubuntu.

Regards.

---

