---
title: "Error Unity tweak tool"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by AxxdcJc on 2013-10-11
Hello, once installed this application when I run I get the following error:
Error: schema com.canonical.desktop.interface not installed

could you help me?

---

### Post by hansdown on 2013-10-11
Welcome to the forum, AxxdcJc.

Which version of ubuntu are you running?

---

### Post by AxxdcJc on 2013-10-12
My Ubuntu version is 13.04

---

### Post by hansdown on 2013-10-12
Have you removed anything from the original install?

Like 

```
 pulseadio and/or indicator-sound
```

[https://bugs.launchpad.net/unity-tweak-tool/+bug/1236313](https://bugs.launchpad.net/unity-tweak-tool/+bug/1236313)

---

### Post by grahammechanical on 2013-10-13
Do you get this error when you launch Unity Tweak or when you try to change something with Unity Tweak. I am running a pre-release version of 13.10 and I have just installed Unity Tweak tool and it loads without giving that error message.

Regards.

---

### Post by pharma on 2013-10-18
Hi - I had your exact problem.  I went to synaptic Missing Recommended Packages and installed them all.  Unity Tweak worked OK.

---

### Post by stanislav-schmidt on 2013-11-13
For those who still need a solution: the problem occurs if one uninstalls the overlay scrollbars. To solve the problem install the overlay scroll bars again (sudo apt-get install overlay-scrollbar) and disable them via the Unity Tweak Tool itself. (System->Scrolling)

This solution has been proposed here: [https://bugs.launchpad.net/unity-tweak-tool/+bug/1130403](https://bugs.launchpad.net/unity-tweak-tool/+bug/1130403)

---

