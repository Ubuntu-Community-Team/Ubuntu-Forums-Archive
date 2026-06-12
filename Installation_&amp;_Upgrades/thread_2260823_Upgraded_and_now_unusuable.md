---
title: "Upgraded and now unusuable"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by d.mayfair on 2015-01-14
I've just installed some upgrades on my Lubuntu 14.04 system that have sent my computer into meltdown.
After the upgrades installed I restarted the pc.Unfortunately I have xbmc set to run from start up.When xbmc loads I am getting video tearing and the mouse/keyboard don't respond to inputs.I can't exit xbmc to the desktop.
As some packages were removed I guess there's no way of rolling back and I'm pretty much screwed,yes ?

---

### Post by Impavidus on 2015-01-14
It may have been a kernel upgrade. I had one yesterday and they sometimes cause nasty side effects. Can you get to the grub menu and boot an older kernel?

---

### Post by d.mayfair on 2015-01-14
Does pressing 'c' get the grub menu up ? Or is it 'shift' ?
Either way it's not working.
I can get the desktop up from booting.Is there anyway to stop xbmc from subsequently starting ? I have a few seconds where the keyboard is working before xbmc starts and  it freezes

---

### Post by d.mayfair on 2015-01-14
It was 'esc' that got me into the grub menu.
I think it's graphics driver related.
After the upgrade the screen resolution was wrong,the icons were smaller.
I've now booted from an earlier kernel and it doesn't autostart xbmc.Again the screen resolution is wrong but now the icons are really big.
Anyways now I'm back in I've deleted xbmc from autostarting.
I'm also allowing the lubuntu to install upgrades just to see what happens this time.Probably the wrong option but it's done now :)

---

### Post by d.mayfair on 2015-01-15
I seem to have it sorted now,it was a driver issue.

---

