---
title: "[SOLVED] Blank screen after splash menu(suspect: lack of drivers for brand-new GeForc"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Shadow ZERO on 2008-01-21
On to my problem, which is of course more speculation since there's nothing but that in these forums.  I think I've figured out most people's "blank screen after splash" problem with new GeForce 8800s, and thats that (whatever)buntu 7.10 doesn't have video drivers for the new nVidia G92 core.  So, what would another joe-schmoe like myself recommend?  Would the new KDE4.0 CD have better drivers?  Should I download a nightly build?  Or am I going to have to regress to a text-install?

EDIT: I removed the complaint part of this post and moved it to a more appropriate section of the forums, where it has already received over 2 pages of replies.  Its the these forums in general that frustrate me though, not any part of the actual Ubuntu/Kubuntu OS.

---

### Post by zvacet on 2008-01-21
I understand your frustration because you can not have full operating system,but that is not reason to be hostile to the people wich are willing to help you in their free time.If you looked closer you will see that your question is answered more then once on this forums.Anyway,if you are willling to try

Ctrl+Alt+F2

```
sudo dpkg-reconfigure xserver-xorg
```

when you come to drivers section select **vesa** and continue with reconfiguration to the end.When you are finish type **startx** and that should give you basic graphic.Once when you have it you can go search for your video card drivers.They should be under restricted drivers manager.

---

### Post by cdtech on 2008-01-21
I had the same problem. I had to go into the recovery mode to install my NVidia drivers.

```
sudo apt-get install nvidia-glx-new
```

I actually tried several, nvidia-glx, nvidia-glx-new, until I found the new to work for me. Now I get the NVidia splash screen and everything seems to work great now.

If you install one of the above it will remove the existing one automatically.

---

### Post by Shadow ZERO on 2008-01-22
I normally reconfigure my entire xserver-xorg on any xBuntu Installation anyway, so doing this doesn't bother me.  Installing the glx-new drivers is also sort of a no-brainer, but I've never had to use any text commands until after my actual installation.  My problem occurs BEFORE the installation, after the LIVE CD splash screen.  These commands you guys have recommended are for after the installation, no?

---

