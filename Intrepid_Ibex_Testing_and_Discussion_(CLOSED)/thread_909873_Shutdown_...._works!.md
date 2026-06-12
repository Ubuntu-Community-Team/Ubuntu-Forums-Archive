---
title: "Shutdown .... works!?"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-09-04
Just wanted to let people know; it's discussed in another thread. (I know that now, but not when I was messing about and lost some unsaved docs, in fact, it's incredible how much the sensation was similar to when you think there's another step and you keep going ...)  
So, in case you weren't looking for it, to clarify, it now works.

::makes mental note to stop messing about with broken things -- they will likely be fixed, silently::

---

### Post by phenest on 2008-09-04
But... pressing the power button only brings up the option to logout.

---

### Post by Macius_Pl on 2008-09-04
System -> Shutdown works , reboot too :)

---

### Post by mc4100 on 2008-09-04
> **Macius_Pl said:**
> System -> Shutdown works , reboot too :)
I just tried Hibernate ... works perfectly too, with a nice "fade-out" transition as well (is this new?). Best thing is, the swap partition is 1/2 size of RAM. Amazing! ... maybe someone can explain it.

---

### Post by ivikas on 2008-09-04
Hello all,

         You can associate the action when you press the power button.Just do this

Goto System->preference->power management

In the power management window that opens up click on the general tab

beside the action it is written as:

[COLOR="Red"]When the power button is pressed : Ask me[/COLOR] so we are given the options as what to do.

So select the alternative actions like shutdown,suspend,hibernate

So next time you press power button,no questions,system will respond to your preferences...

---

### Post by phenest on 2008-09-04
> **ivikas said:**
> Hello all,

         You can associate the action when you press the power button.Just do this

Goto System->preference->power management

In the power management window that opens up click on the general tab

beside the action it is written as:

[COLOR="Red"]When the power button is pressed : Ask me[/COLOR] so we are given the options as what to do.

So select the alternative actions like shutdown,suspend,hibernate

So next time you press power button,no questions,system will respond to your preferences...

If I set it to 'ask me', it only gives a logout option, whereas before, it gave ALL options.

---

### Post by mc4100 on 2008-09-04
> **phenest said:**
> If I set it to 'ask me', it only gives a logout option, whereas before, it gave ALL options.

You should submit a bug report, that "ask me" in power prefs presents the "Log Out..." dialog, when the expected one is "Shut Down..."

---

### Post by arcinthesky on 2008-09-04
Sadly the new update made Hibernate to reboot the computer instead of shutdown. This version it shows texts showing s2disk is running and stuff. The last version that didn't show text works, anyone know how to fix this?

---

### Post by kseise on 2008-09-04
Just to clarify, the default button in the panel seems to have been changed from a power button to a logout button.  I don't know if everyone is talking about the case power button or the panel applet, but I found the panel applet was only letting me logout.I deleted mine and added the "Shut Down" applet back to the panel and it works fine.

---

### Post by philinux on 2008-09-05
Yes the shutdown applet works fine. And the shutdown is much quicker.

---

### Post by Nullack on 2008-09-05
What I especially like is how gdm is shutting down clean now on restart

---

### Post by ronacc on 2008-09-05
one by one the bugs are getting squashed , there is hope .

---

### Post by phenest on 2008-09-05
> **kseise said:**
> Just to clarify, the default button in the panel seems to have been changed from a power button to a logout button.  I don't know if everyone is talking about the case power button or the panel applet, but I found the panel applet was only letting me logout.I deleted mine and added the "Shut Down" applet back to the panel and it works fine.

I was refering to the physical power button on the computer case. This is what the  Power Preferences is refering to as well. 'Ask me' only gives logout options, and not shutdown. restart, etc, options, as it did before.

---

### Post by Gina on 2008-09-05
I really don't know why they couldn't keep the same arrangement as in Hardy.  That works great and looks nice too.

---

### Post by phenest on 2008-09-05
I agree. The new dialogs are good, but now there 2. The logout and shutdown options should be in the same dialog.

---

### Post by rouge568 on 2008-10-07
This has been registered as a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/252795](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/252795)

However, there is a permanent and effective fix. Add Ted Gould's Launchpad repository, and use the gnome-power-manager package from there. This was mentioned in the bug discussion page. 
[https://edge.launchpad.net/~ted-gould/+archive](https://edge.launchpad.net/~ted-gould/+archive)

Instead of the logout options, the power-down options are displayed, with the automatic 60-second shutdown. Very nice!

---

