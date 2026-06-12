---
title: "Resolution too low to install"
date: 2022-12-18
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2022-12-18
What the topic says.

I am not able to install the normal way, so I have to choose safe mode. Seems to be some issues with my GFX card.
When I'm trying to install in safe mode, the resolution is too low because I cannot click the bottom buttons of the windows "previous", "next" and "cancel".

Any ideas on how to get passed this?

---

### Post by MAFoElffen on 2022-12-18
What is your Graphics Card?

---

### Post by pingaan on 2022-12-18
RTX3080 mobile (it's a Razer Blade laptop).

---

### Post by grahammechanical on 2022-12-19
Use the tab key to cycle between the options and then press Enter when you have tabbed into the option you want.

Regards

---

### Post by MAFoElffen on 2022-12-19
At the grub menu... Edit, change "quiet" to "nomodeset" ... <Cntl><X> to boot.

Need more details?

---

### Post by MAFoElffen on 2022-12-19
Also, if you add "nomodeset video=1440x900"... the installer will boot as 1024x768, BUT...

If you then go to "Try" which will get you to the desktop > Right click on the desktop > Display settings > select the resolution you want it to be...

1440x900 is the lowest that the Live Image Environment will offer. Adding it as a boot option will tickle the Live Image Environment that there are other resolutions...

---

### Post by ActionParsnip on 2022-12-20
Does the system have a make and model?

---

### Post by MAFoElffen on 2022-12-20
The OP provided info in Post #3...

---

### Post by ActionParsnip on 2022-12-21
You can hold (I think) ALT and then drag an app window from any point. Might be CTRL. Does that help...?

---

### Post by ajgreeny on 2022-12-21
> **ActionParsnip said:**
> You can hold (I think) ALT and then drag an app window from any point. Might be CTRL. Does that help...?

You were right first time; it's the left Alt key+left mouse click.

---

### Post by pingaan on 2022-12-28
Sorry for the late reply - holidays = busy days!
@MAFoElffen had the winning ticket - thanks!! <3

---

