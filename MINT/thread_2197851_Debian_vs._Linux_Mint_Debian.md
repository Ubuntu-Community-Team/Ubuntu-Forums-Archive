---
title: "Debian vs. Linux Mint Debian"
date: 2014-01-05
forum: MINT
---

### Post by Tk007LwZFJW5ej on 2014-01-05
I'm ready to move on from Ubuntu. What are the pros/cons of installing Debian-based Linux Mint vs. just Debian?

---

### Post by monkeybrain20122 on 2014-01-05
Debian has three versions:stable, testing and unstable.  LMDE is based on Debian testing. Mint probably comes with codecs and non free stuffs (driver, firmware etc) that would be a hassel to install in Debian testing. Mint's update is probably slower than Debian's but I can be wrong on that. Debian uses iceweasel as default browser instead of Firefox, I think Mint uses Firefox.  Neither is true 'rolling' and repo get frozen before the next Debian stable release. Don't let the name fool you, "testing" doesn't mean 'bleeding edge' (as in Arch) or even new, as packages go from Debian experimental to Debian unstable and sit there for a while before hitting testing, by that time they are not new.

I have not used Mint, but have used Debian unstable. Personally I don't find very big differences with Ubuntu in terms of usage except that I have to do more trouble shootings and that hardware is less likely to work out of the box with Debian. So I don't really agree that Debian is "more advanced", you can pretty much do the same things with both OSes if you have to, but Ubuntu is just a lot more convenient.

---

### Post by ibjsb4 on 2014-01-05
If your after the gnome2 look and feel (Mint), you could just install it to your current ubuntu install.

```
sudo apt-get install gnome-panel
```

And choose your desktop at boot (login) by clicking on the login window icon.

---

### Post by malspa on 2014-01-05
> **monkeybrain20122 said:**
> Debian has three versions:stable, testing and unstable.  LMDE is based on Debian testing.

That's one big difference, along with the way LMDE holds back updates and uses update packs -- that doesn't happen with Debian Testing.

Personally, I prefer to stick with Debian Stable, which is one reason why I haven't wanted to run LMDE.

---

### Post by tgalati4 on 2014-01-05
Mint works out-of-the-box.  Debian requires some fiddling.

---

### Post by BubuXP on 2014-01-13
> **tgalati4 said:**
> Mint works out-of-the-box.  Debian requires some fiddling.
But only if you want to customize UI elements that looks ugly (like default themes/settings on LXDE and Xfce, font rendering, etc.).

Consider that I abandoned LMDE two years ago for pure Debian testing because LMDE was not updated for months (not even security updates). LMDE is a secondary choice for Mint developers, only regular Mint is considered. LMDE is a mere experiment, they take a debian testing snapshot and apply Mint mods and patches to that snapshot, then they leave that without any change for months until a new snapshot is taken. But between snapshots there was no updates at all.
Maybe that behavior changes, but if you don't like anymore Ubuntu and want to move Mint, probably there will be a time when you will leave Mint too for Debian, the source of them all.

---

### Post by tgalati4 on 2014-01-13
I have not had that experience with Linux Mint (based on Ubuntu).  With plain Debian install, there are several questions--How do I . . .?  With Mint, I find those questions are answered.  Similarly with Ubuntu, How do I remove a feature or simply move the close window icons to the right side.  Mint takes care of it.

Things I don't like about Ubuntu (there is a lengthy thread)==> Linux Mint.
Things I wish were easier in Debian==> Linux Mint.

But generally, I agree with *BubuXP*.  At some point it will be easier to build Mint from Debian than to undo a bunch of stuff in Ubuntu.  That point is probably close.

---

### Post by mastablasta on 2014-01-15
one could also install mint debian and change the repos to debian stable. :-) solves the security patches problem i guess as wlel as seting up debian...

---

