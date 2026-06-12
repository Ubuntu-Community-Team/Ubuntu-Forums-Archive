---
title: "After installation No Display"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2010-05-22
Hi, I finally got Ubuntu server edition 10.4 LTS installed. But After the installation my computer boots and after the BIOS screen there is a blinking cursur and then the monitor says that there is no input. How can I fix this? I am running a Dell Optiplex SX270, no modifications.  Please help.

---

### Post by darkod on 2010-05-22
I don't have experience with server, but grub seems broken. I think the symptoms happen when grub can't find its config files to continue booting.

Are you sure the grub install went ok?

---

### Post by Theory5 on 2010-05-22
> **darkod said:**
> I don't have experience with server, but grub seems broken. I think the symptoms happen when grub can't find its config files to continue booting.

Are you sure the grub install went ok?

Hmm not sure. There were no error messages, and nothing out of the ordinary. It gave me the choice to install GRUB legacy or GRUB 2 and I picked GRUB 2. So, how would I go about fixing this?
I reinstalled GRUB after booting into rescue mode off my installation USB stick. It still doesnt work.
Also I don't hear any noise when It boots up

---

### Post by Theory5 on 2010-05-23
Bump! 
Oh Also I have a 20" widescreen and my optiplex has Integrated Intel Extreme Graphics Video with DVI-I connector. Are these supported?

---

### Post by Paegus on 2010-08-14
i believe it's a problem with using a DVI->VGA adapter. Mine works fine using a DVI cable but when i try to plug it into the same monitor's VGA connector using that adapter the screen no-signals when the loading screen should have appeared. I've tried all 5 DVI adapters i have as well.

This does not happen in windows btw. it loads fine with the DVI->VGA adapter.

---

