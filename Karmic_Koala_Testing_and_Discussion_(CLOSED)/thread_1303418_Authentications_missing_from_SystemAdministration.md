---
title: "Authentications missing from System/Administration"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PatrikG on 2009-10-28
The item Authentications no longer appear in my System/Administration menu. I can't find it either under the "Edit Menu"-window.

I did a 

locate polkit-gnome | grep desktop

Which yields:
/etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
/usr/share/app-install/desktop/polkit-gnome-authorization.desktop

And:
polkit-gnome-authentication

Which says:
polkit-gnome-authentication: command not found

How can I get it back? it's annoying to always go into the terminal to mount USB disks for instance.

---

### Post by albandy on 2009-10-28
try reinstalling the polkit libraries.

---

### Post by PatrikG on 2009-10-28
Thanks! I found it in synaptic.

---

### Post by PatrikG on 2009-10-28
but...

now I only see

> org
  > freedesktop
    > policykit
           and 4 items under here

Have I missed some other package?

---

### Post by albandy on 2009-10-28
reinstall or install gnome-system-tools

---

### Post by PatrikG on 2009-10-28
Did a reinstall, but still only those few items in there :(

---

### Post by chrisccoulson on 2009-10-28
polkit-gnome-authorizations only manages policies for applications still using the old Policykit API. Most applications have now been ported to the new Policykit-1 API, for which there is no equivalent tool just yet.

---

