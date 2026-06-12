---
title: "Botched upgrade from 7.10 to 10.04 -- options?"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by mikecrowe on 2010-06-26
Hi folks,

OK, yes, this was stupid, so no recriminations, please.  It was a old machine, and I was trying to upgrade from 7.10.  It's not urgent that I fix, but it would be nice if I could keep some of my stuff.

After my attempted upgrade (I had to terminate at a very bad time), the machine boots to an (initramfs) prompt.  I've downloaded 10.04, booted to the installer, and am saving all the /etc /var directories (to recover the stuff I'd like to save).

So, here's my question:  Can the 10.04 installer somehow use the existing partition and upgrade, rather than having to wipe out?  i.e. recover from an attempted upgrade?

TIA
Mike

---

### Post by Sonsum on 2010-06-26
So you're currently in between a 8.04 > 10.04 upgrade?

---

### Post by mikecrowe on 2010-06-26
Bingo -- I was VNC'd in, but wasn't paying attention.  Started the upgrade via SSH (from inside the VNC session), and got to the Exim/SSH restart.  When SSH terminated, it hung.  To further complicate matters, my VMware install didn't allow me to get to my console, so I had to reboot the VM.

---

