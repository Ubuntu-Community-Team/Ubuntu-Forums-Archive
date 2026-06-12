---
title: "Cancelling an OEM config dialogue uninstalls all OEM config stuff, locks out user??"
date: 2023-01-28
forum: Installation &amp; Upgrades
---

### Post by Yougo on 2023-01-28
Hi 

I made an OEM install on my old laptop (Kubuntu 22.04) so i can give it away. worked like a charm, it booted up and gave me a nice welcome and setup dialoge. 

Closing that dialogue (because i don't want to set up right now) is a **BAD IDEA**: it proceeds to uninstall all OEM config stuff, breaks the OEM user, logs out and leaves you with a locked out laptop?!
is that normal? that's way to easy for a new user to "break their new laptop" before even using it.

(i can just install again for now, but am hesitant to give it away like that :( it would make a very bad impression)

is there any way for it to just shut down when the setup dialogue closes?

---

### Post by MAFoElffen on 2023-01-28
I just spun up an OEM install... I didn't see a way to cancel it, but I guess you found a way. LOL. If I just shut the power off, it does reboot again to the OEM config steps.

---

### Post by Yougo on 2023-01-28
Yeah that's the other way i could have gone about it. power down or close the window. i think it's the clean-up script to remove the oem-config stuff and the temporary oem user that's set to run after the window closes regardless if the setup completed successfully or not.
i made a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2004077](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2004077)

---

