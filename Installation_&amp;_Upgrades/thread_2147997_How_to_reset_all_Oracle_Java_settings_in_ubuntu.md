---
title: "How to reset all Oracle Java settings in ubuntu?"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by sinmpae on 2013-05-23
I am using ubuntu 12.04 64bit and I have setup oracle java as discribed here [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java).
I usually need oracle java to run web applet of my online banking site which povides security keypad to generate login key.
On each PC time this security keypad needed to be activated with one time password. Once activated, it can generate the login key.

And these settings are common for all browsers so in my case I can generate login key from both chrome and firefox.

I have noticed that each time I update the linux kernel image (provided by Ubuntu update manager) the security keypad no longer be able to generate login key. It shows wrong password. So I need to deactivate the keypad and reactivate by using different one time password. Then it works fine.

I have recently updated Oracle Java to latest version and updated kernel also since then I am not be able to deactivate the keypad nor I am able to generate login key.

I have noticed the applet creates one configure file in home directory each time keypad is configured. As per my findings all java related settings made in .java directory in home. I have tried deleting both .java directory and config file but the keypad isn't rolled back to default settings.

I am looking for additional settings made by applet so by deleting it, I can reset the keypad settings.

---

### Post by Pjotr123 on 2013-05-23
Can you use the Java Control Panel to throw away all remains of applets?

32-bit:
```
/opt/java/32/jre1.7.0_21/bin/ControlPanel
```

64-bit:
```
/opt/java/64/jre1.7.0_21/bin/ControlPanel
```

---

