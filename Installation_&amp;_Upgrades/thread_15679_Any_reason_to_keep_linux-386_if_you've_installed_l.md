---
title: "Any reason to keep linux-386 if you've installed linux-686?"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by Hikaru79 on 2005-02-16
I've installed, from Synaptic (Hoary), the linux-686, linux-image-686-1-3, and linux-restricted-modules-686-1-3. However, I still have the same thing of all of these but for 386 installed. uname -a returned 686 so I don't think I'm actually using the 386 kernel. Is it safe to remove all the 386-related packages? And if so, what's the best way to do it?

---

### Post by Xian on 2005-02-16
[QUOTE=Hikaru79]Is it safe to remove all the 386-related packages? And if so, what's the best way to do it?[/QUOTE]
I always like to have one back-up kernel on the system as a just-in-case measure but if you have been using the i686 blend for a while and feel comfortable with it, then you can just remove the old kernel(s) using Synaptic. It will clean them from your system and /boot directory.

---

