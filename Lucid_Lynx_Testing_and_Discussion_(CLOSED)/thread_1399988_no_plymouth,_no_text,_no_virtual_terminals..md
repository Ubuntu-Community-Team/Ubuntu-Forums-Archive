---
title: "no plymouth, no text, no virtual terminals."
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rolandixor on 2010-02-06
When I first upgraded to lucid things were going fine, now, after some updates, no splash screen (never had plymouth), no text with splash disabled in grub (yes, I rebuilt my initramfs) no virtual terminals either. Just a black screen with blue yellow and white lines at first, then a big white block at the top, and then on the virtual terminals, a corrupted copy of my login screen's image.

And then... I can't change my gdm theme (using the sudo -u gdm blablabla method).

Oh, nvidia 9600M GT, 190.xx driver.

Open to any suggested fixes so long as they won't break anything. I need my VT's back!!! D:

---

### Post by VMC on 2010-02-06
> **rolandixor said:**
> ...(never had plymouth)...
...nvidia 9600M GT, 190.xx driver.
When you say you never had plymouth, does that mean it never worked or not installed. For me things went dark on boot a few updates ago, so I removed plymouth and now I can boot. Boot-up text complains about plymouth, but everything else works.

Regarding nVidia. I know nothing about that driver. Someone will come along to help you.

---

### Post by rolandixor on 2010-02-06
lol it installed and from some reading I did today I'm guessing that I'm seeing an attempted fallback due to the lack of KMS. I'm hoping all I need to do is change the resolution that is used at boot. Only problem is I'm not sure what to use for that.

And I don't get any text at boot with or without plymouth :(

---

### Post by rolandixor on 2010-02-06
lol it installed and from some reading I did today I'm guessing that I'm seeing an attempted fallback due to the lack of KMS. I'm hoping all I need to do is change the resolution that is used at boot. Only problem is I'm not sure what to use for that.

And I don't get any text at boot with or without plymouth :(

---

### Post by rolandixor on 2010-02-06
what's up with the double posting bug today?

---

### Post by vishalrao on 2010-02-06
Can you ensure you "set gfxpayload=1024x768" or whatever is your native resolution in GRUB2 so that plymouth can work? I had to do this too, but I am running some nouveau test PPA so may be a little different for me.

---

### Post by rolandixor on 2010-02-08
thanks I want to try this, but where do I put this for my kernel? it's bla.bla.bla.32 and I think that the vga=xxx is making the problems appear (tho when I removed it, and rebuilt the initramfs, it didn't work lol). I think you might have the answer tho, so thanks in advance (I feel this will work)

---

### Post by rolandixor on 2010-02-27
okie... this is fixed when I != lazy, I'll post how I fixed it.

---

