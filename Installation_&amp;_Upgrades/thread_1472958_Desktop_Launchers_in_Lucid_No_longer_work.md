---
title: "Desktop Launchers in Lucid No longer work"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by jr3us on 2010-05-04
There must be something turned on in the security settings keeping Desktop Launchers from working.

I have verified that the launchers have execute bit turned on in the permissions, yet when try to start one, I get an alert window saying this is an Untrusted application launcher.

How do I disable this feature, or in the alternative, make them trusted?

Thanks in advance!

---

### Post by jr3us on 2010-05-05
bump!

Any ideas?

---

### Post by jr3us on 2010-05-06
bump again.. 

Any ideas?!

---

### Post by RichardG891 on 2010-05-26
Thread a bit old but in case anyone else stumbles upon it:

Up until 10.04, ubuntu used to warn you it was untrusted but give you a button to "mark as trusted" and all would be well again.

Two options now:

If you don't want to mark it as trusted but just temporarily run it, right-click on the *****.desktop launcher and select run as administrator.

If you want it trusted, show its proper icon, etc.: right click on it and select properties. On the permissions tab of the menu box that appears, tick "Allow executing file as program".... and all is well again.

---

### Post by GrandTheft on 2010-06-22
Thanks, the first option works and is my workaround for the while. The second doesnt, though. The behaviour is neither changed by chmodding +x, nor by setting the tick at "allow execution" in permissions. Might be a bug...

[https://bugs.launchpad.net/ubuntu/+bug/572918](https://bugs.launchpad.net/ubuntu/+bug/572918)

Regards,
GT

---

