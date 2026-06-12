---
title: "Ubuntu 8.04 to 10.04 Upgrading Troubles"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by zarakstan on 2010-03-28
I just tried upgrading my current 8.04 installation of Ubuntu. Because when I ran Update Manager no upgrades seemed to be available, I ran the command &quot;sudo update-manager -d&quot;. Update Manager opened again and I clicked on the button that said &quot;Upgrade to Ubuntu 10.04 LTS&quot; after some checking of some description an error message popped up, it read  >  **Could not calculate the upgrade** A unresolvable problem occurred while calculating the upgrade.  Please report this bug against the 'update-manager' package and include the following error message: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'  Now when I try to run update manager I have a blank list instead of a list of updates, despite the fact that it says 1442 updates are available. When I hit "Install Updates" anyway I get another error message: > Could not apply changes! Fix broken packages first.   Any ideas what may have caused this and/or anyway to fix it?

---

### Post by flope on 2010-09-07
Hi zarakstan, 
I am assuming by this time you already solved your problem. 
How did you do it?
I am having the same error message.

Thanks
F

---

### Post by mörgæs on 2010-09-08
Generally the safe approach is doing a clean installation of 10.04 rather than an upgrade. When Update Manger warns of itself being buggy as in this example I wouldn't risk it.

---

