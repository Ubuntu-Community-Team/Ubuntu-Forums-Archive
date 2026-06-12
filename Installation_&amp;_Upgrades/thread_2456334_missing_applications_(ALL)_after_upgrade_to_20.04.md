---
title: "missing applications (ALL) after upgrade to 20.04"
date: 2021-01-09
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2021-01-09
this is strange and annoying.
I just upgraded to 20.04 and while it looks good all my default applications are gone. All of them. 
when I click on the Launcher or "Search you computer" swirly icon (which used to be loaded with apps, even as basic as Calculator,) there are none.
not the ones i installed myself, nor the system default ones.

where'd they all go? 

the system is pretty useless without these tools.

---

### Post by vanadium on 2021-01-10
The figure suggests you are using the Unity desktop. Your applications are not gone. They only are not displayed anymore. The upgrade removed a unity lens, needed to find and display the installed applications on your system. Make sure that at least unity-lens-applications is installed.

---

### Post by TheFu on 2021-01-10
Upgrades only retain applications that were previously installed AND part of the core Ubuntu Repositories.  Any PPA apps aren't moved forward. Any manually installed apps are likely to remain where they were, unless overwritten.

If you were using Unity, there is a team trying to keep that DE alive, but the default Ubuntu moved to Gnome3, so you can have either bloated DE if you like those.  DEs are very much a personal preference.  When Unity became available, I switched DEs and eventually ended without any DE, choosing to run a WM that hasn't changed too much in 20 yrs.  Every few years, I'm not shocked into some new-but-claimed-better DE. I get to use a WM that I first used around 1995. It is like coming home.

---

### Post by grahammechanical on 2021-01-10
From my experience of upgrading 18.04 with Unity to 20.04 - I was asked if I wanted obsolete packages removed. I authorised that and most of Unity was removed. Unity was one of a few login options. It must be possible to login to a desktop of Ubuntu with Gnome 3 shell or Ubuntu with Wayland. Which also uses the Gnome 3 shell.

Regards

---

### Post by pjstock on 2021-01-10
> **vanadium said:**
> Make sure that at least unity-lens-applications is installed.

thank you. 
I'm a bit of a simpleton when it comes to Ubuntu or Linux. a lazy Ubuntu user. I've always just used Ubuntu and it has miraculously worked.

I had never heard of Unity or Gnome..

though I have two systems, both of which I have recently upgraded from 18.04 to 20.04.
System A i upgraded following the instructions for an upgrade from the desktop.
System B I upgraded from a bootable USB stick.

the results look a bit different.
System A (the one I am writing about here, where it appeared that I had "lost" my applications) has a Swirly icon in the Upper LH corner which apparently "Search you computer"

System B has a 9 dot matrix on the sidebar which is "Show Applications" and many (though not all) of my 18.04 applications show there.

how would one install "Unity-lens-applications"?

and once it is installed, how would I use these lenses to view my applications?

Peter

---

### Post by pjstock on 2021-01-10
how would I know if a Ubuntu system was using Unity or Gnome3?

I have 2 systems that I upgraded to 20.04 - via different upgrade methods and with slightly different results.

NEVER MIND. I figured out how to tell which was which.
and indeed, I have Gnome on System B (that I upgraded from a USB stick) and Unity on System A (which I upgraded using system commands while connected.)

but I cannot figure out how to actually USE Unity Lenses to see, access and use my various applications.

should I maybe just dump Unity and switch System A to Gnome?

Peter

---

### Post by pjstock on 2021-01-10
Okay I think I am now set.
reading up I discovered that if I Logged Out then at the Log In screen there is a Settings icon which when clicked on gives several desktop options. mine was showing Unity. when I switched to "Ubuntu" my applications showed back up again.

I wish I understood the point of Unity and how to make it practical. but I can just muddle along from here, in Gnome.

Peter

---

