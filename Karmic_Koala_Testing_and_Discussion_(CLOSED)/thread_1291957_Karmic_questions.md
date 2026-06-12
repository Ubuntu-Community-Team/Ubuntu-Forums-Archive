---
title: "Karmic questions"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jetsaredim on 2009-10-15
I posted a similar message on the ubuntu-users mailing list, but haven't gotten any answers...

I'm trying out the karmic beta on one of my test machines so I can work out the kinks.  One of the things I'm having a real problem with is the decision to use empathy as the default messaging client.  Does anyone know what the consequences would be of uninstalling empathy and installing pidgin in its place?

Another minor annoyance is that in previous releases I was able to use the scroll of my mouse on an open section of desktop to switch workspaces.  This seems to be disabled by default in karmic.  I assume this is just some obscure gnome setting somewhere.  Can someone tell me how to turn this on again?

Thanks.

---

### Post by Lars Noodén on 2009-10-15
You may need to explicitly point some programs to pidgin.  But otherwise, they should be mostly or entirely interchangeable.

---

### Post by mcduck on 2009-10-15
> **jetsaredim said:**
> I posted a similar message on the ubuntu-users mailing list, but haven't gotten any answers...

I'm trying out the karmic beta on one of my test machines so I can work out the kinks.  One of the things I'm having a real problem with is the decision to use empathy as the default messaging client.  Does anyone know what the consequences would be of uninstalling empathy and installing pidgin in its place?

Another minor annoyance is that in previous releases I was able to use the scroll of my mouse on an open section of desktop to switch workspaces.  This seems to be disabled by default in karmic.  I assume this is just some obscure gnome setting somewhere.  Can someone tell me how to turn this on again?

Thanks.

I wouldn't recommend uninstalling Empathy at this point, as that would remove the ubuntu-desktop metapackage, which is essential in making sure that if some update adds new packages they will get installed on your system.

After the release, when the development phase is finished, you can safely uninstall Empathy. Just make sure that you'll re-install the ubuntu-desktop package if you upgrade your install to next release (10.04).

What comes to the scroll wheel switching workspaces, you'll need to install CompizConfig Settings Manager and enable that option  in the Viewport Switcher-plugin's settings. Go to "Desktop-based Viewport Switching"-tab, and set "Move Next" to "Button4" and "Move Prev" to "Button5".

---

### Post by Lars Noodén on 2009-10-15
@ mcduck : tying so many packages into the desktop is a rather severe problem, linux is supposed to be modular.  

@ jetsaredim  : yes, the package ubuntu-desktop lists empathy as a dependency, but having tested installing ubuntu-desktop and then uninstalling empathy, I see that the ubuntu-desktop is still there.  AFAIK no problem.

I do see some unwanted cruft that came with ubuntu-desktop as well as some different cruft that came with kubuntu-desktop.

---

### Post by mcduck on 2009-10-15
> **Lars Noodén said:**
> @ mcduck : tying so many packages into the desktop is a rather severe problem, linux is supposed to be modular.  

@ jetsaredim  : yes, the package ubuntu-desktop lists empathy as a dependency, but having tested installing ubuntu-desktop and then uninstalling empathy, I see that the ubuntu-desktop is still there.  AFAIK no problem.

I do see some unwanted cruft that came with ubuntu-desktop as well as some different cruft that came with kubuntu-desktop.

They are not tied to desktop. "ubuntu-desktop" is tied to them. :D

The "ubuntu-desktop" is a metapackage, meaning that it's just an empty package that depends on all the packages that belong to default Ubuntu desktop install, but no package depends on it. So, installing ubuntu-desktop will install everything that belongs to the default setup, removing it removes nothing else than the ubuntu-desktop package itself.

The reason you should keep that package installed for now is that 9.10 is still under development, and the developers might still need to add some new packages to the system. Having the "ubuntu-desktop" metapackage installed is what makes that happen, they simply add any new stuff they need to add to the install into that package's dependencies, and as a result the new stuff gets installed even though you didn't have those packages previously. (without that, updates would only update the packages you already have).

Like I said, during normal use it's safe to remove the ubuntu-desktop metapackage and you won't loose anything. But it should be installed during upgrades between different releases to make sure all new stuff gets installed. And since Karmic is still under development you should consider every update you mae as similar to upgrading between different release versions, the updates still actually change many things instead of just providing new versions of already installed packages.

---

