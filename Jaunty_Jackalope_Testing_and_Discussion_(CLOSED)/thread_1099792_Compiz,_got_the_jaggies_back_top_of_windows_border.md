---
title: "Compiz, got the jaggies back top of windows border on rotate cube or change workspace"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-03-18
This is a regression back to intrepid. Compiz was smooth no jaggies. Anyone else see this.

---

### Post by scaine on 2009-03-18
All smooth here.  Tosh U-400 with GMA4500 graphics running latest Compiz (updated and reboot about 20 minutes ago).  I use the Shiki theme - very dark.  What kind of "jaggies" are you seeing?  Is it obvious?  If so, then definitely all good here.

---

### Post by philinux on 2009-03-18
Also cube caps not working. Nvidia 180.37 installed.

---

### Post by scaine on 2009-03-18
Yep, no cap here either, although I never set it - just use whatever default there is.  I change/update/re-install Ubuntu too often to care about it anymore.

As for the "jaggies" - are you talking about that jagged line running under your top menu, you can see in your screenshot?  If so, then yes, I have that too.  I never noticed it until you pointed it out.  It's very subtle on my laptop, possibly because I very rarely drag my cube these days - I usually just Super-1,2,3,4,Left or Right to get to wherever I want to go...

[EDIT : Right, it looks like it's just the default cube-cap image that's now missing with the latest updates.  Stick your own jpg into cube-cap and it'll work fine.  However, nothing I have done to desktop cube, general options or rotate cube has gotten rid of those jaggies when I jump to another workspace.  Thanks man.  Now I'm bloody seeing it all the time...]

---

### Post by philinux on 2009-03-18
> **scaine said:**
> Yep, no cap here either, although I never set it - just use whatever default there is.  I change/update/re-install Ubuntu too often to care about it anymore.

As for the "jaggies" - are you talking about that jagged line running under your top menu, you can see in your screenshot?  If so, then yes, I have that too.  I never noticed it until you pointed it out.  It's very subtle on my laptop, possibly because I very rarely drag my cube these days - I usually just Super-1,2,3,4,Left or Right to get to wherever I want to go...

And the window borders. It had gone in jaunty now it's back.

---

### Post by Amaranth on 2009-03-18
To get rid of that you have to configure your nvidia driver to do antialiasing on all 3D applications. Intel and ATI users, you're stuck with it.

---

### Post by philinux on 2009-03-18
> **Amaranth said:**
> To get rid of that you have to configure your nvidia driver to do antialiasing on all 3D applications. Intel and ATI users, you're stuck with it.

Thanks for reply. 
What do you recommend for these settings.
Also like I said they had gone previously in Jaunty. Reappeared after the latest updates.

---

### Post by philinux on 2009-03-19
Trying to dable with antialiasing settings in nvidia-settings borks compiz and terminal.

---

