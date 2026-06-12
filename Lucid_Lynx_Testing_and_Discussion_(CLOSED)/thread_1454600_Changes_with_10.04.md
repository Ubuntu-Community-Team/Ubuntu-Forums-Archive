---
title: "Changes with 10.04?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kev3124 on 2010-04-14
I have been running the 10.04 beta for a few weeks now. Productivity wise, its been flawless. 

However, 10.04 seems very similar to 9.10, looks wise. Isn't GRUB supposed to be a graphical boot loader now? Mine is still the same black and white system font. Also, the purple splash screen is very grainy, and jumpy. The window controls on the left took some getting used to, but are fine. Is there currently anything on the right? Any way to add things on the right where the buttons used to be?

I think the changes didn't apply themselves properly on my system, even though I have all the updates installed. Thoughts?

Kernel Linux 2.6.32-21-generic 
GNOME 2.30.0

---

### Post by jaco223 on 2010-04-14
> **kev3124 said:**
> I have been running the 10.04 beta for a few weeks now. Productivity wise, its been flawless. 

However, 10.04 seems very similar to 9.10, looks wise. Isn't GRUB supposed to be a graphical boot loader now? Mine is still the same black and white system font. Also, the purple splash screen is very grainy, and jumpy. The window controls on the left took some getting used to, but are fine. Is there currently anything on the right? Any way to add things on the right where the buttons used to be?

I think the changes didn't apply themselves properly on my system, even though I have all the updates installed. Thoughts?

Kernel Linux 2.6.32-21-generic 
GNOME 2.30.0

You can change the buttons to the right side with gconf editor.
Is gconf installed?
GRUB is not graphical as far as I know, but I think you can modify it and theme it.

---

### Post by egalvan on 2010-04-14
If you upgraded from an install which used GRUB1, then your up-grade will still use GRUB1.

If you did a clean install, you should be running GRUB2.

(9.x installs required there be no existing GRUB1 in order to install GRUB2. An existing GRUB1 meant a default to GRUB1, so up-grading to 10.04 also meant GRUB1)

I upgraded my Hardy 8.04 to 9.04, then 9.10, then 10.04Beta (per Ubuntu Community instructions)
GRUB1 came along for the ride :)

When Lucid stabilizes (at 10.04.1) then I will do a clean install on my existing Hardy machines.
This should bring GRUB2 and ext4 to the party.

---

### Post by Sonsum on 2010-04-14
The program Ubuntu Tweak probably has the easiest method of moving the window buttons over.

---

### Post by kev3124 on 2010-04-14
Thanks for the help. Anyway to get the graphical boot with GRUB 2, other than a clean install?

---

### Post by Sonsum on 2010-04-15
Just curious, What do you mean by graphical boot?

---

### Post by kev3124 on 2010-04-16
> **Sonsum said:**
> Just curious, What do you mean by graphical boot?

Something other than a black background with white system font.

Something in this direction 

[img]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.theme.dinxter.png[/img]

---

### Post by Artemis3 on 2010-04-16
If you already use grub2 (**grub-pc**) then read this: [https://wiki.ubuntu.com/Grub2#Theming](https://wiki.ubuntu.com/Grub2#Theming)

You can install the package **grub2-splashimages** for a few sample backgrounds.

Have fun!

---

### Post by Sonsum on 2010-04-16
> **kev3124 said:**
> Something other than a black background with white system font.

Something in this direction 

[img]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.theme.dinxter.png[/img]

This is news to me! I have GRUB 2 but I didn't know it could do that! :)

---

### Post by cecilpierce on 2010-04-16
There is a thread called "GRUB2 theming for lucid?" if you want a graphical boot menu like the one you showed.

---

