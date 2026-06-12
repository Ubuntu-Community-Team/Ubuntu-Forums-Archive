---
title: "Problem with CUPS"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by makaveli0129 on 2012-02-14
OK so i scanned the internet and show this is a bug in gnome but i can't find a fix and the bug said it was fixed in the previous update. So i'm not sure what it is. I can use my printer to scan just fine but i can't print. Going through the log i see this
```

E [14/Feb/2012:18:46:56 -0500] Unknown directive JobPrivateAccess on line 87.
E [14/Feb/2012:18:46:56 -0500] Unknown directive JobPrivateValues on line 88.
E [14/Feb/2012:18:46:56 -0500] Unknown directive SubscriptionPrivateAccess on line 89.
E [14/Feb/2012:18:46:56 -0500] Unknown directive SubscriptionPrivateValues on line 90.
W [14/Feb/2012:18:46:56 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_Gray__' has already been added
W [14/Feb/2012:18:46:56 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_RGB__' has already been added
W [14/Feb/2012:18:48:12 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_Gray__' has already been added
W [14/Feb/2012:18:48:12 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_RGB__' has already been added
W [14/Feb/2012:18:48:15 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_Gray__' has already been added
W [14/Feb/2012:18:48:15 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_RGB__' has already been added
W [14/Feb/2012:18:48:15 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_Gray__' has already been added
W [14/Feb/2012:18:48:15 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_RGB__' has already been added
W [14/Feb/2012:18:54:26 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_Gray__' has already been added
W [14/Feb/2012:18:54:26 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Lexmark_5000_Series_RGB__' has already been added
W [14/Feb/2012:19:03:30 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_Gray__' has already been added
W [14/Feb/2012:19:03:30 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_RGB__' has already been added
W [14/Feb/2012:19:03:30 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_Gray__' has already been added
W [14/Feb/2012:19:03:30 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_RGB__' has already been added
W [14/Feb/2012:19:05:26 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_Gray__' has already been added
W [14/Feb/2012:19:05:26 -0500] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/My_Lexmark_Printer_RGB__' has already been added
E [14/Feb/2012:19:06:15 -0500] [Job 7] The Printer cannot communicate with the computer.

```

any help would be greatly apprieciated

---

### Post by kc1di on 2012-02-14
Sorry your having problems.
Couple of questions - Which version of ubuntu are you using.
and what printer?

Will try to help
Have you updated your system lately?

---

### Post by makaveli0129 on 2012-02-14
> **kc1di said:**
> Sorry your having problems.
Couple of questions - Which version of ubuntu are you using.
and what printer?

Will try to help
Have you updated your system lately?

ubuntu 11.10 and lexmark x5070 with the linux driver from lexmark

---

### Post by makaveli0129 on 2012-02-17
> **kc1di said:**
> Sorry your having problems.
Couple of questions - Which version of ubuntu are you using.
and what printer?

Will try to help
Have you updated your system lately?

does anyone know how to fix this?

---

