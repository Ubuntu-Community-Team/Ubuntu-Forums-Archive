---
title: "Safe to remove &quot;Hoary&quot; from software updates?"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by KurtB on 2005-12-06
Hello,

After upgrading from Hoary to Breezy, I get updates concerning modules from kernel 2.6.10...which are from Hoary.

Is it "safe" to still update Hoary stuff after that you've upgraded your system to Breezy?

In the "Preferences" dialog, I see that you can remove software-update binaries concerning Hoary -> is it done or not done to remove everything from Hoary and only let Breezy updates be in the list?

---

### Post by nocturn on 2005-12-06
[QUOTE=KurtB]Hello,

After upgrading from Hoary to Breezy, I get updates concerning modules from kernel 2.6.10...which are from Hoary.

Is it "safe" to still update Hoary stuff after that you've upgraded your system to Breezy?

In the "Preferences" dialog, I see that you can remove software-update binaries concerning Hoary -> is it done or not done to remove everything from Hoary and only let Breezy updates be in the list?[/QUOTE]

If you are running Breezy, all references to Hoary should be gone...
Having a mixed setup can bring your system down.

Just a tip, after changing everyting to Breezy, run dist-upgrade again.

---

### Post by KurtB on 2005-12-07
mmmhz,

Sounds serious if I can compromize my system.

I'm going to run dist-upgrade as you proposed in your post. Meanwhile I only unchecked all repositories pointing to Hoary.

I suppose this isn't enough to be "safe"?

---

### Post by Pablo_Escobar on 2005-12-07
If You upgraded to Breezy stick to Breezy repos, not Hoarys. There is no way for a downgrade.

---

