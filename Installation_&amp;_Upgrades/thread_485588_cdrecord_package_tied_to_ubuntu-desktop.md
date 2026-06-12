---
title: "cdrecord package tied to ubuntu-desktop?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by torquill on 2007-06-27
Hi all... since cdrecord isn't working for me under Edgy, I decided to go out and get a copy of wodim instead.  The wodim package required that I uninstall cdrecord first, so I asked apt-get to uninstall cdrecord.

apt-get insisted that it needed to uninstall four packages: cdrecord, k3b, nautilus-cd-burner... and ubuntu-desktop.  I could live without nautilus' CD burner, and I can reinstall k3b -- but why on earth would it want to uninstall ubuntu-desktop?

I aborted it, since I don't think uninstalling a major component is a good idea, but now I can't install wodim.  Synaptic gave me the same runaround (that was expected).  Is there any way I can trade cdrecord for wodim without doing a wipe/upgrade to Feisty?

---

### Post by renzokuken on 2007-06-27
ubuntu-desktop is simply a meta-package, i.e. its not really anything at all.......

you can go ahead and remove it without any problems

---

### Post by torquill on 2007-06-27
Okay... the info said that it helps ensure proper upgrades, "so it is recommended that it not be removed".  If it doesn't actually break anything to remove it, I'll go ahead.

Thanks for the prompt reply.  :)

---

