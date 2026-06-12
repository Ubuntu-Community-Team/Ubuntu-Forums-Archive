---
title: "If compiz is installed as default why not the settings manager."
date: 2008-11-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-11
Seems crazy to have something like compiz installed but not it settings manager.

---

### Post by kestal on 2008-11-11
> **philinux said:**
> Seems crazy to have something like compiz installed but not it settings manager.

thats a question I ask myself every day! they somewhat fixed it with 8.10, giving you the basic options already set up.. but the manager is pretty useful for the eye-candy and marketing backend that I think Jaunty should deserve :)

I am sure most of us can type in sudo apt-get install simple-ccsm and sudo apt-get install compizconfig-settings-manager, but why not just include it to begin with!

I wonder if anything is stopping canonical from setting it up and having it pre-installed.

---

### Post by crjackson on 2008-11-11
> **philinux said:**
> Seems crazy to have something like compiz installed but not it settings manager.

No kidding. I couldn't agree more...

---

### Post by kestal on 2008-11-11
well, its not that big of a hassle to sudo it or anything, but its just the convenience. That and I think having a fresh/unified 'out of the box' experience (prior to learning how to use the terminal for the new Linux User) is what Jaunty should aim for.

---

### Post by RAOF on 2008-11-11
Because the settings manager is (pretty much unavoidably) a pile of UI evil?  Compiz simply has too many options for any sane UI to expose all of them.

It may be worthwhile doing the work to get simple-ccsm in by default, though.

---

### Post by ronacc on 2008-11-11
+1

---

### Post by denzilla on 2008-11-11
> **RAOF said:**
> Because the settings manager is (pretty much unavoidably) a pile of UI evil?  Compiz simply has too many options for any sane UI to expose all of them.

It may be worthwhile doing the work to get simple-ccsm in by default, though.


You can't even enable Vsync with the simple ccsm. Someone needs to cleanup the current ccsm or at least add a bit more functionality to the simple ccsm.

---

### Post by RAOF on 2008-11-11
> **denzilla said:**
> You can't even enable Vsync with the simple ccsm. Someone needs to cleanup the current ccsm or at least add a bit more functionality to the simple ccsm.

This begs the obvious question: why isn't sync-to-vblank enabled by default?

The thought process should go: "I need to twiddle this knob" -> "Can I make it so I don't have to twiddle the knob", rather than -> "Let's make it easier to twiddle the knob".

---

### Post by denzilla on 2008-11-11
> **RAOF said:**
> This begs the obvious question: why isn't sync-to-vblank enabled by default?

The thought process should go: "I need to twiddle this knob" -> "Can I make it so I don't have to twiddle the knob", rather than -> "Let's make it easier to twiddle the knob".

Your guess is as good as mine. I've never installed Ubuntu or any other Linux distro and had Vsync from the getgo. Kinda ruins the fancy graphical effects with the screen tear and all. I agree with you though. Vsync should be on by default.

---

### Post by ronacc on 2008-11-11
> **RAOF said:**
> This begs the obvious question: why isn't sync-to-vblank enabled by default?

The thought process should go: "I need to twiddle this knob" -> "Can I make it so I don't have to twiddle the knob", rather than -> "Let's make it easier to twiddle the knob".

what about those of us who WANT to twiddle every knob ? I despise a system that wants to wipe my *** for me . It makes me think that some arrogant dev thinks he knows more about how I want my system to look/operate than I do , I use linux to avoid that crap .

---

### Post by | MM | on 2008-11-11
> **ronacc said:**
> what about those of us who WANT to twiddle every knob ? I despise a system that wants to wipe my *** for me . It makes me think that some arrogant dev thinks he knows more about how I want my system to look/operate than I do , I use linux to avoid that crap .

No worries, you can play with a text file or gconf or something, but thats besides the point.  Top quality software should come with sane defaults, and if a default cannot be applied then it needs a reasonably intelligent fallback mechanism.  And there is absolutely no reason to confront 99% of users with a myriad of potential configurations just because 1% want to twiddle every nob...

---

### Post by ronacc on 2008-11-11
sane defaults cetainly ,a simple set of controls sure , for those who prefer that , just don't remove the full version for those who wish that .

---

### Post by RAOF on 2008-11-11
> **ronacc said:**
> what about those of us who WANT to twiddle every knob ? I despise a system that wants to wipe my *** for me . It makes me think that some arrogant dev thinks he knows more about how I want my system to look/operate than I do , I use linux to avoid that crap .

Then you can install ccsm, and have about as good a GUI interface to all those options as can be generated.  I'm not opposed to the existence of knobs, nor the tools to twiddle them, but "I always need to twiddle this knob" isn't necessarily a good argument for "so we should include *knob twiddling app* in the default install".

We're not talking about removing ccsm from the archives.  We're arguing whether it should be in the default install.

---

### Post by ronacc on 2008-11-11
> **RAOF said:**
> Then you can install ccsm, and have about as good a GUI interface to all those options as can be generated.  I'm not opposed to the existence of knobs, nor the tools to twiddle them, but "I always need to twiddle this knob" isn't necessarily a good argument for "so we should include *knob twiddling app* in the default install".

We're not talking about removing ccsm from the archives.  We're arguing whether it should be in the default install.

I know I can install ccsm and I do . I have no objection to simple-ccsm as the default but your comment a few posts above about ccsm being "a pile of ui evil " sure sounded like it was a canidate for banishment.

---

### Post by RAOF on 2008-11-11
> **ronacc said:**
> I know I can install ccsm and I do . I have no objection to simple-ccsm as the default but your comment a few posts above about ccsm being "a pile of ui evil " sure sounded like it was a canidate for banishment.

Oh, no.  It *is* a pile of UI evil, but that's only because it has to be.  That makes it potentially unsuitable for default install, not for the archive in general.  We've certainly got programs with worse UIs in there!

---

### Post by Cenotaph on 2008-11-12
I think the way it is now makes sense. I would like to see a different default configuration though.

ccsm offers lots of plugins, some of them which aren't exactly stable, so the way it is now Ubuntu let's you choose two stable profiles with simple plugins that can improve your productivity and are easy to configure for everyone.

Providing the tool to mess with compiz configurations to everyone can have poor results for those who don't know what they are doing.

However, I would like Ubuntu to have by default scale and expo functionality using the corners as the Super+E and Shift+Alt+Up are very poor key combos for things that are really important in my desktop.

I guess simple-ccsm would be a good alternative to the current tab in Appearance, but simple-ccsm seems a little too buggy at this point to make it as a default tool.

---

### Post by danf_1979 on 2008-11-12
I think it is a good idea that it is not installed by default. I guess this is a newbie-fool-proof policy, and should stay as it is.

---

### Post by sdowney717 on 2008-11-13
All I want is compiz to work with video and google earth with no flashing.

ALSO, a big problem is when your system has a video driver problem and you start compiz and get a white screen.

We got one PC that I enabled compiz on and got the white screen on every boot. So I had to log in recovery mode and remove all compiz binaries to get it back.

This is happening with an intel server board and an ATI AGP x1300 on hardy.

---

### Post by Ocxic on 2008-11-15
because sync to vblank can actually hinder performance on lower end video cards.
my dad has on board graphics that works great, if I enable sync to vblank everything becomes very jumpy. vblank is only goo for higher end video cards, even my GForce 7600 gets a little jumpy when it's enabled.

---

### Post by danbuter on 2008-11-15
The better question is what sane distro would include compiz as default ;).

---

### Post by MadsRH on 2008-11-15
> **cenotaph said:**
> i think the way it is now makes sense. I would like to see a different default configuration though.

+1

---

### Post by philinux on 2008-11-17
My feeling now is that **simple-ccsm** should be installed as default but definitely not **ccsm**.

But I think it needs renaming to **easy-ccsm. :)**

---

### Post by psyke83 on 2008-11-17
> **Ocxic said:**
> because sync to vblank can actually hinder performance on lower end video cards.
my dad has on board graphics that works great, if I enable sync to vblank everything becomes very jumpy. vblank is only goo for higher end video cards, even my GForce 7600 gets a little jumpy when it's enabled.

Compiz's sync_to_vblank is ignored for the open-source drivers because of DRI's indirect rendering. For onboard Intel and ATI chipsets it won't make *any* difference to enable this setting by default.

As for the NVIDIA cards, we *need* sync_to_vblank enabled or else video will tear (compositing seems to override the vertical sync options for textured and overlay video in nvidia-settings). If your card is too slow to handle compiz, then... tough, disable it.

I think we should have this setting enabled by default; regressions would affect a minority of users (even my old GeForce FX 5200 **PCI** can just about handle compiz with vblank enabled).

P.S. Re: jumpy compiz on a GeForce 7600 - impossible, I say. I bet that you didn't disable the "DynamicTwinView" driver option. If Dynamic TwinView is enabled (and by default, it is), compiz will mistakenly believe the refresh rate of your screen is something like 50Hz, and the vertical sync will constrain to 50fps instead of the actual rate of your screen. This will give the impression that compiz is sluggish, when in fact it is being throttled by mistake.

From the driver [README]("http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-b.html"):
> Option "DynamicTwinView" "boolean"

    Enable or disable support for dynamically configuring TwinView on this X screen. When DynamicTwinView is enabled (the default), the refresh rate of a mode (reported through XF86VidMode or XRandR) does not correctly report the refresh rate, but instead is a unique number such that each MetaMode has a different value. This is to guarantee that MetaModes can be uniquely identified by XRandR.

    When DynamicTwinView is disabled, the refresh rate reported through XRandR will be accurate, but NV-CONTROL clients such as nvidia-settings will not be able to dynamically manipulate the X screen's MetaModes. TwinView can still be configured from the X config file when DynamicTwinView is disabled.

    Default: DynamicTwinView is enabled.

A quick test to check if you're affected: System/Preferences/Screen Resolution. Check the refresh rate displayed in this application (it's the same rate used by compiz, unless you already set an override).

On my system (single screen setup, GeForce 6200 PCI):
[LIST]
[*]With DynamicTwinView enabled: application says 50Hz, actual rate (verified by monitor OSD) 75Hz. Compiz is choppy.
[*]With DynamicTwinView disabled: application says 75Hz, actual rate (verified by monitor OSD) 75Hz. Compiz is smooth.
[/LIST]

---

### Post by ssam on 2008-11-17
> **RAOF said:**
> The thought process should go: "I need to twiddle this knob" -> "Can I make it so I don't have to twiddle the knob", rather than -> "Let's make it easier to twiddle the knob".

+1

especially true when the the options are effectively
(o) Broken
(o) Slow
(o) Also broken
(o) Works
but with fun labels like 'xmapsync', 'bitfliplib', 'mipgfx'

I remember the days when everyone wanted a GUI to configure DMA on hard disks.

---

