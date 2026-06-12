---
title: "Fix for Broken Remote Desktop Server (vino) after 11.10 upgrade"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by iposner on 2011-11-15
I'm sure there are several people who can tell me how to install a different type of server to compensate for the ropey vino/11.10/Unity combination.

But I want the Remote Desktop fixed for existing users of the x64 version who upgraded to 11.10 and found that the remote desktop service no longer works with the Unity interface (it worked with 11.04 and the Gnome desktop). There are many of us (just check the other posts) who get a message that the server has closed the connection.

Remote desktop software is** mission critical** for those of us who support remote users. No, we can't go to each PC and apply the fix - it must be fixed as part of the regular distribution updates.

Hopefully someone at Canonical will read this and get a fix in the pipeline.

---

### Post by nukie77 on 2011-12-01
The NoMachine Free NX server still works for me just fine after I made the following changes client side:

"Issue resolved for me. I went back to play around with NX and found that by setting the NX client to load custom and then run the command:

gnome-session --session=ubuntu-2d

with New virtual desktop selected, I was able to connect."

---

### Post by iposner on 2011-12-01
Just updated the problematic machine - finally fixed! Well done whoever put that fix in.

---

### Post by iposner on 2011-12-15
A recent upgrade has broken the remote desktop again! I suspect it was the upgrade to kernel 3.0.0-14... can somebody take a look at this? Again, this problem only manifests itself on the 64-bit version.

---

