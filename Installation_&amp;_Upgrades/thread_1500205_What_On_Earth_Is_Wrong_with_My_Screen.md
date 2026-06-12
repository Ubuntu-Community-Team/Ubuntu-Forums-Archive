---
title: "What On Earth Is Wrong with My Screen"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by MimeyNaomi on 2010-06-02
Here's the deal:

I had a hard time with the 10.04 installation.  This is my mom's 6-year-old Gateway E4000.  During various points in the CD installation, it would crash, I'd get the error:
```
Glib-Warning **: getpwuid_r(): failed due to unknown user id (0)
```
and then a row of white vertical lines would start blinking on a black background.  And I was like, "What?"

But after combing the forums, I managed to get through the entire install by hitting F6 at the beginning and selecting acpi=off, noapic, and nomodeset, then install.  Coolio!

But then, when I boot, the same thing happens.  The Glib-warning is gone, but at any point during boot, or five minutes after it's booted successfully, or ten minutes, the screen will go blank and I'll get those white blinking lines of death.

Also, for the entire installation and the first few boots, my top menu bar was totally effed.  It was upside-down and pixelated.  This seemed to fix itself.

WHAT DOES IT MEEEEAN!

Thank you very much for your time.

---

### Post by lemming465 on 2010-06-04
Are your kernel options in grub when you boot still including *acpi=off noapic nomodeset*?  Just because you specified them during install doesn't, alas, mean they persisted.  
> Also, for the entire installation and the first few boots, my top menu bar was totally effed. It was upside-down and pixelated. This seemed to fix itself.

WHAT DOES IT MEEEEAN!
Probably it means there were bugs in the video support, some of which were improved in later upgrades.

---

### Post by MimeyNaomi on 2010-06-04
I'll give it a try and update!  Thanks for your reply.

---

