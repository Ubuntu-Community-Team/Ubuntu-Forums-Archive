---
title: "Karmic Alpha 4 on MBP5,1 - Success!"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alexmurray on 2009-08-27
Just a quick shout out to say I installed Karmic Alpha 4 and it is quite an improvement over Jaunty on my MBP5,1 - sound works out of the box, as does trackpad, and EFI booting now works flawlessly as well - all without any mactel ppa drivers (since 2.6.31 has all the applesmc and mbp_nvidia_bl, bcm5974 etc updates which were backported against Jaunty in the mactel support repo) - initially had some trouble getting the broadcom wl driver installed but I think that was jockey (the old restricted driver manager)'s fault.

---

### Post by amd-64 on 2009-08-27
on a MBP5,3 how do I convert from REFIT to EFI booting and what is your main reason for EFI booting. Can you now select the graphics driver.

Thanks

---

### Post by mthwkln on 2009-08-27
I have a MBP5,2 and the touchpad does work now, which is nice. But I still have trouble with wireless, shutdown (screen goes black but the computer never turns off) and no audio. I also cannot turn on desktop effects for some reason, but there is a workaround.

I'm an Ubuntu newbie, as of today I've only been using it 3 days. I'm using Wubi BTW. I didn't feel up to messing with rEFIt just yet.

EDIT: Disregard. I reinstalled and most of my issues are resolved.

---

### Post by pxwpxw on 2009-08-28
> **alexmurray said:**
> Just a quick shout out to say I installed Karmic Alpha 4 

and EFI booting now works flawlessly as well - 



elilo as well as grub?

---

### Post by alexmurray on 2009-08-29
I've only tried using grub - using the grub64.efi posted in the efi booting thread - can successfully boot without noefi now (but still need fakebios).

---

