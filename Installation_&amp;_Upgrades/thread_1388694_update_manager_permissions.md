---
title: "update manager permissions"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by alexdavis on 2010-01-23
Hey

So when using the update manager gui, I have encountered some kind of problem. The update manager autostarts, and it shows me what needs to be updated. The 'install updates' button does not work until i hit 'check', at which point it prompts me for my password. After the check is complete, I can THEN push "install updates". Neither are greyed out at any point.

I was also having a problem with eclipse where I couldn't push buttons, which i fixed by setting GDK_NATIVE_WINDOWS=1 in a script before opening. It may be related.

Ubuntu 9.10.

A

---

### Post by static0verdrive on 2010-01-23
Ubuntu and it's variants like Kubuntu don't have an administrative account like "Administrator" or "root"... instead they prompt for your password in order to gain administrative privileges for a few moments. Regular users in linux only have access to their home directory, so any and all updating of the OS or applications will require admin rights in order to proceed. Also, Apt always wants to check for the newest versions of files before going ahead with downloading and installing, so you need to check before you can do anything else. So although it does seem a bit strange, I think your update manager is working properly. Hope this helps!

---

### Post by alexdavis on 2010-01-23
> **static0verdrive said:**
> Ubuntu and it's variants like Kubuntu don't have an administrative account like "Administrator" or "root"... instead they prompt for your password in order to gain administrative privileges for a few moments. Regular users in linux only have access to their home directory, so any and all updating of the OS or applications will require admin rights in order to proceed. Also, Apt always wants to check for the newest versions of files before going ahead with downloading and installing, so you need to check before you can do anything else. So although it does seem a bit strange, I think your update manager is working properly. Hope this helps!

Don't think so. I'm not confused by the fact that the privileges need to be elevated; I am only confused by the behavior of the 'install updates' button. Update Manager shows me what needs to be updated, yet the button to do so does not click.
It is, in fact, broken.

A

---

