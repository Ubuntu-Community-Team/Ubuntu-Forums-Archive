---
title: "Two, should be easy post install Grub2 questions?"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by markjs on 2011-11-04
OK, I got everything installed and booting like I like it, but there are two minor annoying issues.

The first is that I have it defaulting to Windows as most of my work is Windows and it serves as my DVR.  The problem isn't much but it annoys me; when it gets past Grub2, somehow the Num Lock key is off and I have to hit that to enter my password.  I know it seems minor, but I have my reasons which are probably boring and unimportant, but is there any way to set it not to turn Num Lock off? It is on by default in BIOS.

The second question has to do with my graphics driver (Radeon HD 4200 onboard graphics: Asus M4A785-M motherboard) and Grub2.  Before it was enabled, Grub2 looked fine, but now, though the desktop is perfect in the monitor's native 1440x900 resolution, Grub2 is skewed about 1 1/2 inches to the left and it wavers as if it's straining something to even display at all and my boot menu is, as a result, completely unreadable.  Of course I know by what line what will boot, but it is damn annoying as well.  Is there an easy fix for this?

Thanks in advance!  I love this board and Ubuntu, for if not for the friendly folk here and the ease of Ubuntu's interface, I'd probably still be sour on Linux.

---

### Post by hansdown on 2011-11-04
Hi, markjs.

Those , could be annoying things.

Could you please post which version you are using, and whether this is an upgrade?

---

### Post by markjs on 2011-11-04
Oh yeah, doh!  It's 11.10 and a clean install.

---

### Post by hansdown on 2011-11-04
Does the num lock happen in both os?

---

### Post by markjs on 2011-11-04
> **hansdown said:**
> Does the num lock happen in both os?

Strangely enough, no, only Windows 7.

---

### Post by hansdown on 2011-11-05
This should help, for that.

[http://social.technet.microsoft.com/Forums/en-US/w7itprogeneral/thread/8f604425-19c5-48f1-b70a-f61674e9e1f4/](http://social.technet.microsoft.com/Forums/en-US/w7itprogeneral/thread/8f604425-19c5-48f1-b70a-f61674e9e1f4/)

The second part, of your question, may take some time.

---

### Post by markjs on 2011-11-05
> **hansdown said:**
> This should help, for that.

[http://social.technet.microsoft.com/Forums/en-US/w7itprogeneral/thread/8f604425-19c5-48f1-b70a-f61674e9e1f4/](http://social.technet.microsoft.com/Forums/en-US/w7itprogeneral/thread/8f604425-19c5-48f1-b70a-f61674e9e1f4/)

The second part, of your question, may take some time.

Well, don't ask me how or why but that solved both problems, even though the Num Lock thing was caused by Grub2.  I know this because as soon as the Grub menu comes up, the Num Lock light goes off.  I can see how the Windows registry turns it back on, and obviously something in Ubuntu does as well.

Here is what is truly bizarre though and I don't trust it; after changing that in the Windoze registry and trying it out, I rebooted to Ubuntu and, wonder of wonders, the wavery skewed screen issue seems to have vanished as well!  I am sure changing the Windows registry did not fix that, but perhaps some Ubuntu update, or Grub2 itself repaired it?  I can't complain, but still, it is suspicious!

---

### Post by hansdown on 2011-11-05
Glad you fixed it, markjs.

Hope all is well.

---

