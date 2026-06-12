---
title: "Named user root, can't login"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by acosby on 2010-03-05
I effed up.  Let's start there.
In a moment of stupid bliss after finally installing Ubuntu on a laptop without media, I named my user root.
Like an idiot.
A big friggin idiot.
Am I stuck reinstalling? Please tell me there's a way around.
Cheers (and shame),
Alex.

---

### Post by honey toast on 2010-03-05
this belong in the ubuntu hall of shame. All I can say is live and learn. I'd definitely rebuild.

---

### Post by chuina on 2010-03-05
What Ubuntu you install ?

And what happen when you boot the Laptop ?

Can you get a GRUB (boot loader) menu ?

---

### Post by acosby on 2010-03-05
Infinite shame, indeed.  I have grub, and it boots to Ubuntu login.  I'm going to hope I can still do a netboot.  Any ideas on how?

---

### Post by whoop on 2010-03-05
It might be a bit shameful, but the installer could have indicated that the name "root" is reserved.
Maybe you can login with the actual root account via the recovery console, create a new user there, login with that and see if you can remove the "fake" root user.
Might as well experiment with this, see if you can fix this, if it fails you can always reinstall.

---

